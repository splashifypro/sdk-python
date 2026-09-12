# Splashify Pro — Python SDK

[![PyPI](https://img.shields.io/badge/pypi-splashifypro-3776ab?logo=pypi&logoColor=white)](https://pypi.org/project/splashifypro/)
[![Python](https://img.shields.io/badge/python-3.9%2B-3776ab?logo=python&logoColor=white)](https://pypi.org/project/splashifypro/)
[![docs](https://img.shields.io/badge/docs-splashifypro.com-1B70FF)](https://docs.splashifypro.com/public-api)
[![license](https://img.shields.io/badge/license-MIT-22c55e)](./LICENSE)

Official Python SDK for the [Splashify Pro](https://splashifypro.com) API —
send WhatsApp messages, transactional emails, manage contacts and
conversations, and fire Meta Conversions events from your Python backend.

## Install

```bash
pip install splashifypro
```

Requires Python 3.9+.

## Get your API key

1. **Sign in** to your Splashify Pro account at
   [app.splashifypro.com](https://app.splashifypro.com).
   No account yet? [Sign up free](https://app.splashifypro.com/auth/signup).

2. Open the **Settings** dialog (gear icon, top right) → click the
   **Developer** tile.
   *Direct link:* [app.splashifypro.com/settings/developer](https://app.splashifypro.com/settings/developer)

3. Under **API Keys**, click **Generate Secret Key**.

4. Copy the key shown (starts with `sk_live_…`) and store it somewhere
   secure — it's shown **only once**. If you lose it, generate a new one
   and the old one stops working.

5. Use it as the `SPLASHIFY_API_KEY` environment variable in your app.
   **Never commit it to git or paste it into client-side code** — the
   key carries full account access.

> **Tip:** Set up a [webhook URL](https://app.splashifypro.com/settings/developer)
> on the same page to receive delivery / read receipts and inbound message
> events.

## Authentication

The SDK uses HTTP Basic with the API key as the username:

```python
import os
from splashifypro import Configuration, ApiClient
from splashifypro.api import MessagesApi

config = Configuration(username=os.environ["SPLASHIFY_API_KEY"])
client = ApiClient(config)

messages = MessagesApi(client)
```

## Quickstart — send a WhatsApp text

```python
result = messages.public_message_post(
    body={
        "type": "Text",
        "countryCode": "+91",
        "phoneNumber": "9999999999",
        "data": {"message": "Hi! Thanks for reaching out 👋"},
    }
)

print(result["id"])  # message_id — use to poll status / correlate webhooks
```

## Send a WhatsApp template

```python
messages.public_message_post(body={
    "type": "Template",
    "countryCode": "+91",
    "phoneNumber": "9999999999",
    "template": {
        "name": "order_confirmation",
        "languageCode": "en",
        "bodyValues": ["Sayan", "ORD-1042", "₹1,499"],
        "buttonValues": {"0": ["https://shop.example.com/orders/1042"]},
    },
})
```

## Send a transactional email

> Requires a verified sender domain. Set up at
> **https://app.splashifypro.com/settings/email-domain**.

```python
from splashifypro.api import EmailApi

email = EmailApi(client)

email.public_email_send_post(body={
    "to": "customer@example.com",
    "subject": "Your receipt for Order #1042",
    "html": "<h1>Thanks!</h1><p>Order #1042 confirmed.</p>",
    "text": "Thanks! Order #1042 confirmed.",
    "from_email": "billing@yourdomain.com",
    "from_name": "Acme Inc.",
})
```

## Available APIs

| Class                | What it does                                                |
| -------------------- | ----------------------------------------------------------- |
| `MessagesApi`        | Send WhatsApp messages (text, template, media, interactive) |
| `EmailApi`           | Send transactional + templated emails                       |
| `ContactsApi`        | List + filter contacts                                      |
| `ConversationsApi`   | Assign chats to team members                                |
| `MetaConversionsApi` | Fire Meta Pixel / Conversions API events                    |

Full reference, request/response shapes, and per-endpoint examples:
**https://docs.splashifypro.com/public-api**

## Async usage

The SDK is sync by default. For async workloads, run synchronous calls in a
thread pool:

```python
import asyncio

result = await asyncio.to_thread(
    messages.public_message_post,
    body={"type": "Text", "countryCode": "+91", "phoneNumber": "9999999999",
          "data": {"message": "Hello!"}},
)
```

## Rate limits

Per-key limits depend on your plan tier. Hitting the limit returns HTTP 429 —
the response body includes `Retry-After`. Tier and current consumption are
visible at https://app.splashifypro.com/settings/developer.

## Error handling

```python
from splashifypro.exceptions import ApiException

try:
    result = messages.public_message_post(body={...})
except ApiException as e:
    print(f"HTTP {e.status}: {e.body}")
```

## Support

- **Issues / bug reports:** [github.com/splashifypro/sdk-python/issues](https://github.com/splashifypro/sdk-python/issues)
- **Documentation:** [docs.splashifypro.com/public-api](https://docs.splashifypro.com/public-api)
- **Email support:** support@splashifypro.in

## License

[MIT](./LICENSE)

---

This SDK is auto-generated from the official OpenAPI specification. Pull
requests for SDK-side improvements (typing, ergonomic wrappers, async
helpers, etc.) are welcome; underlying API changes should be filed against
the documentation site.
