# splashifypro.EmailApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**public_email_send_post**](EmailApi.md#public_email_send_post) | **POST** /public/email/send | Send a transactional email
[**public_email_send_template_post**](EmailApi.md#public_email_send_template_post) | **POST** /public/email/send-template | Send a templated email
[**public_email_status_message_id_get**](EmailApi.md#public_email_status_message_id_get) | **GET** /public/email/status/{message_id} | Get email delivery status


# **public_email_send_post**
> Dict[str, object] public_email_send_post(body)

Send a transactional email

Send a fully-formed HTML email to one or more recipients.
Caller supplies subject + html + text + from_email + recipient.
Optional attachments[] (PDFs, images, docs) ride inline as
base64 — backend builds multipart/mixed and DKIM-signs. Caps:
20 files / 10 MiB total / executable extensions blocked.
Delivered via the platform's self-hosted email pipeline with
category=email_transactional. From-email must be on a verified
sender domain.

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
    api_instance = splashifypro.EmailApi(api_client)
    body = None # object | Send email payload (to, subject, html, text, from_email, reply_to, attachments)

    try:
        # Send a transactional email
        api_response = api_instance.public_email_send_post(body)
        print("The response of EmailApi->public_email_send_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling EmailApi->public_email_send_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Send email payload (to, subject, html, text, from_email, reply_to, attachments) | 

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
**200** | { result: true, message_id: ... } |  -  |
**400** | Invalid request body / domain not verified / INVALID_ATTACHMENT |  -  |
**401** | Missing/invalid API key |  -  |
**402** | Plan does not include email marketing |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_email_send_template_post**
> Dict[str, object] public_email_send_template_post(body)

Send a templated email

Send an email using a saved template (created via the
in-app template editor at /email/templates). Caller supplies
template_id + recipient + variables map. Backend pulls the
template's pre-rendered HTML and substitutes {{vars}}.
Optional attachments[] ride inline as base64 — same shape +
caps as /send (20 files / 10 MiB / blocked extensions).

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
    api_instance = splashifypro.EmailApi(api_client)
    body = None # object | Template send payload (to, template_id, variables, from_email, subject, attachments)

    try:
        # Send a templated email
        api_response = api_instance.public_email_send_template_post(body)
        print("The response of EmailApi->public_email_send_template_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling EmailApi->public_email_send_template_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Template send payload (to, template_id, variables, from_email, subject, attachments) | 

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
**200** | { result: true, message_id: ... } |  -  |
**400** | Invalid request body / template not found / INVALID_ATTACHMENT |  -  |
**401** | Missing/invalid API key |  -  |
**402** | Plan does not include email marketing |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_email_status_message_id_get**
> Dict[str, object] public_email_status_message_id_get(message_id)

Get email delivery status

Look up the current status of an email message by its
message_id (returned from /public/email/send or /send-template).
Status values: queued, sending, delivered, bounced, failed.

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
    api_instance = splashifypro.EmailApi(api_client)
    message_id = 'message_id_example' # str | Message ID returned by send

    try:
        # Get email delivery status
        api_response = api_instance.public_email_status_message_id_get(message_id)
        print("The response of EmailApi->public_email_status_message_id_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling EmailApi->public_email_status_message_id_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **message_id** | **str**| Message ID returned by send | 

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
**200** | { result: true, status: ..., delivered_at: ..., bounced_at: ... } |  -  |
**401** | Missing/invalid API key |  -  |
**404** | Message not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

