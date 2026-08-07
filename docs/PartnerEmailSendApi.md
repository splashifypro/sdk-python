# splashifypro.PartnerEmailSendApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**partner_email_emails_message_id_get**](PartnerEmailSendApi.md#partner_email_emails_message_id_get) | **GET** /partner/email/emails/{message_id} | Get email status
[**partner_email_send_bulk_post**](PartnerEmailSendApi.md#partner_email_send_bulk_post) | **POST** /partner/email/send-bulk | Send bulk templated email
[**partner_email_send_post**](PartnerEmailSendApi.md#partner_email_send_post) | **POST** /partner/email/send | Send email
[**partner_email_send_raw_post**](PartnerEmailSendApi.md#partner_email_send_raw_post) | **POST** /partner/email/send-raw | Send raw MIME email
[**partner_email_send_template_post**](PartnerEmailSendApi.md#partner_email_send_template_post) | **POST** /partner/email/send-template | Send templated email


# **partner_email_emails_message_id_get**
> Dict[str, object] partner_email_emails_message_id_get(message_id)

Get email status

Look up the current status and event timeline for an email
by message_id. Returns sent / delivered / bounced / complained
state plus open + click counters.

### Example

* Api Key Authentication (BearerAuth):

```python
import splashifypro
from splashifypro.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://apis.splashifypro.com/api/v1
# See configuration.py for a list of all supported configuration parameters.
configuration = splashifypro.Configuration(
    host = "https://apis.splashifypro.com/api/v1"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure API key authorization: BearerAuth
configuration.api_key['BearerAuth'] = os.environ["API_KEY"]

# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['BearerAuth'] = 'Bearer'

# Enter a context with an instance of the API client
with splashifypro.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = splashifypro.PartnerEmailSendApi(api_client)
    message_id = 'message_id_example' # str | Message ID returned from /send

    try:
        # Get email status
        api_response = api_instance.partner_email_emails_message_id_get(message_id)
        print("The response of PartnerEmailSendApi->partner_email_emails_message_id_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailSendApi->partner_email_emails_message_id_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **message_id** | **str**| Message ID returned from /send | 

### Return type

**Dict[str, object]**

### Authorization

[BearerAuth](../README.md#BearerAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | { success: true, message: {...} } |  -  |
**401** | Missing/invalid API key |  -  |
**404** | Message not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **partner_email_send_bulk_post**
> Dict[str, object] partner_email_send_bulk_post(body)

Send bulk templated email

One template + one verified From + N destinations, each
with its own ReplacementData map. Equivalent to AWS SES
SendBulkTemplatedEmail. Caps: 50 destinations × 50
recipients = 500 total per request.

### Example

* Api Key Authentication (BearerAuth):

```python
import splashifypro
from splashifypro.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://apis.splashifypro.com/api/v1
# See configuration.py for a list of all supported configuration parameters.
configuration = splashifypro.Configuration(
    host = "https://apis.splashifypro.com/api/v1"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure API key authorization: BearerAuth
configuration.api_key['BearerAuth'] = os.environ["API_KEY"]

# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['BearerAuth'] = 'Bearer'

# Enter a context with an instance of the API client
with splashifypro.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = splashifypro.PartnerEmailSendApi(api_client)
    body = None # object | Send bulk payload (template_name, from, default_template_data, destinations[])

    try:
        # Send bulk templated email
        api_response = api_instance.partner_email_send_bulk_post(body)
        print("The response of PartnerEmailSendApi->partner_email_send_bulk_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailSendApi->partner_email_send_bulk_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Send bulk payload (template_name, from, default_template_data, destinations[]) | 

### Return type

**Dict[str, object]**

### Authorization

[BearerAuth](../README.md#BearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | { success: true, sent, failed, results: [...] } |  -  |
**400** | Invalid request, TEMPLATE_NOT_FOUND |  -  |
**401** | Missing/invalid API key |  -  |
**402** | Insufficient wallet balance |  -  |
**403** | Sandbox quota or sending paused |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **partner_email_send_post**
> Dict[str, object] partner_email_send_post(body)

Send email

Send a transactional or marketing email to up to 50 recipients
(combined to + cc + bcc). Equivalent to AWS SES SendEmail.

### Example

* Api Key Authentication (BearerAuth):

```python
import splashifypro
from splashifypro.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://apis.splashifypro.com/api/v1
# See configuration.py for a list of all supported configuration parameters.
configuration = splashifypro.Configuration(
    host = "https://apis.splashifypro.com/api/v1"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure API key authorization: BearerAuth
configuration.api_key['BearerAuth'] = os.environ["API_KEY"]

# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['BearerAuth'] = 'Bearer'

# Enter a context with an instance of the API client
with splashifypro.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = splashifypro.PartnerEmailSendApi(api_client)
    body = None # object | Send email payload (from, to, subject, html_body, text_body, configuration_set_name?)

    try:
        # Send email
        api_response = api_instance.partner_email_send_post(body)
        print("The response of PartnerEmailSendApi->partner_email_send_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailSendApi->partner_email_send_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Send email payload (from, to, subject, html_body, text_body, configuration_set_name?) | 

### Return type

**Dict[str, object]**

### Authorization

[BearerAuth](../README.md#BearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | { success: true, results: [{recipient, message_id, status}] } |  -  |
**400** | Invalid request, FROM_NOT_VERIFIED, TOO_MANY_RECIPIENTS |  -  |
**401** | Missing/invalid API key |  -  |
**402** | Insufficient wallet balance |  -  |
**403** | Sandbox quota reached or sending paused |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **partner_email_send_raw_post**
> Dict[str, object] partner_email_send_raw_post(body)

Send raw MIME email

Submit a pre-built RFC 5322 MIME message — useful when you've
already constructed the email body yourself (DKIM-ready,
multipart, calendar invites, etc). Equivalent to AWS SES
SendRawEmail. Max 10 MiB raw body.

### Example

* Api Key Authentication (BearerAuth):

```python
import splashifypro
from splashifypro.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://apis.splashifypro.com/api/v1
# See configuration.py for a list of all supported configuration parameters.
configuration = splashifypro.Configuration(
    host = "https://apis.splashifypro.com/api/v1"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure API key authorization: BearerAuth
configuration.api_key['BearerAuth'] = os.environ["API_KEY"]

# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['BearerAuth'] = 'Bearer'

# Enter a context with an instance of the API client
with splashifypro.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = splashifypro.PartnerEmailSendApi(api_client)
    body = None # object | Send raw payload (raw_message_base64, destinations[], from, configuration_set_name?)

    try:
        # Send raw MIME email
        api_response = api_instance.partner_email_send_raw_post(body)
        print("The response of PartnerEmailSendApi->partner_email_send_raw_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailSendApi->partner_email_send_raw_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Send raw payload (raw_message_base64, destinations[], from, configuration_set_name?) | 

### Return type

**Dict[str, object]**

### Authorization

[BearerAuth](../README.md#BearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | { success: true, message_id, status } |  -  |
**400** | Invalid MIME, FROM_NOT_VERIFIED |  -  |
**401** | Missing/invalid API key |  -  |
**402** | Insufficient wallet balance |  -  |
**403** | Sandbox quota or sending paused |  -  |
**413** | Raw message exceeds 10 MiB |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **partner_email_send_template_post**
> Dict[str, object] partner_email_send_template_post(body)

Send templated email

Render a saved template with per-recipient variables and
send it. Equivalent to AWS SES SendTemplatedEmail. Templates
are pre-rendered at save time so per-send substitution is
cheap.

### Example

* Api Key Authentication (BearerAuth):

```python
import splashifypro
from splashifypro.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://apis.splashifypro.com/api/v1
# See configuration.py for a list of all supported configuration parameters.
configuration = splashifypro.Configuration(
    host = "https://apis.splashifypro.com/api/v1"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure API key authorization: BearerAuth
configuration.api_key['BearerAuth'] = os.environ["API_KEY"]

# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['BearerAuth'] = 'Bearer'

# Enter a context with an instance of the API client
with splashifypro.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = splashifypro.PartnerEmailSendApi(api_client)
    body = None # object | Send template payload (template_name OR template_id, from, to[], variables{})

    try:
        # Send templated email
        api_response = api_instance.partner_email_send_template_post(body)
        print("The response of PartnerEmailSendApi->partner_email_send_template_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailSendApi->partner_email_send_template_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Send template payload (template_name OR template_id, from, to[], variables{}) | 

### Return type

**Dict[str, object]**

### Authorization

[BearerAuth](../README.md#BearerAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | { success: true, results: [{recipient, message_id, status}] } |  -  |
**400** | Invalid request, TEMPLATE_NOT_FOUND, FROM_NOT_VERIFIED |  -  |
**401** | Missing/invalid API key |  -  |
**402** | Insufficient wallet balance |  -  |
**403** | Sandbox quota or sending paused |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

