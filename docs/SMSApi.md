# splashifypro.SMSApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**public_sms_bulk_bulk_id_get**](SMSApi.md#public_sms_bulk_bulk_id_get) | **GET** /public/sms/bulk/{bulk_id} | Bulk send progress
[**public_sms_messages_message_id_get**](SMSApi.md#public_sms_messages_message_id_get) | **GET** /public/sms/messages/{message_id} | One SMS status
[**public_sms_send_bulk_post**](SMSApi.md#public_sms_send_bulk_post) | **POST** /public/sms/send-bulk | Send one template to many numbers
[**public_sms_send_post**](SMSApi.md#public_sms_send_post) | **POST** /public/sms/send | Send one SMS
[**public_sms_senders_get**](SMSApi.md#public_sms_senders_get) | **GET** /public/sms/senders | SMS sender IDs
[**public_sms_templates_get**](SMSApi.md#public_sms_templates_get) | **GET** /public/sms/templates | Approved SMS templates


# **public_sms_bulk_bulk_id_get**
> Dict[str, object] public_sms_bulk_bulk_id_get(bulk_id)

Bulk send progress

Progress of a bulk send by the bulk_id /public/sms/send-bulk returned.
status is queued, running, completed, stopped or cancelled.
failed counts numbers the network refused plus delivery failures reported so far.

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
    api_instance = splashifypro.SMSApi(api_client)
    bulk_id = 'bulk_id_example' # str | bulk_id from /public/sms/send-bulk

    try:
        # Bulk send progress
        api_response = api_instance.public_sms_bulk_bulk_id_get(bulk_id)
        print("The response of SMSApi->public_sms_bulk_bulk_id_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling SMSApi->public_sms_bulk_bulk_id_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **bulk_id** | **str**| bulk_id from /public/sms/send-bulk | 

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
**200** | { success, bulk_id, name, status, stop_reason, total, sent, delivered, failed, charged, created_at, completed_at } |  -  |
**400** | Invalid bulk_id |  -  |
**401** | Missing or invalid API key |  -  |
**404** | Bulk send not found, or SMS not set up |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_sms_messages_message_id_get**
> Dict[str, object] public_sms_messages_message_id_get(message_id)

One SMS status

Status of one message by the message_id /public/sms/send returned.
status is queued, sent, delivered, failed or rejected. error says why when it did not arrive.

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
    api_instance = splashifypro.SMSApi(api_client)
    message_id = 'message_id_example' # str | message_id from /public/sms/send

    try:
        # One SMS status
        api_response = api_instance.public_sms_messages_message_id_get(message_id)
        print("The response of SMSApi->public_sms_messages_message_id_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling SMSApi->public_sms_messages_message_id_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **message_id** | **str**| message_id from /public/sms/send | 

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
**200** | { success, message_id, to, dlt_template_id, status, error, parts, charged, created_at, delivered_at } |  -  |
**400** | Invalid message_id |  -  |
**401** | Missing or invalid API key |  -  |
**404** | Message not found, or SMS not set up |  -  |
**503** | The message could not be read right now, try again shortly |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_sms_send_bulk_post**
> Dict[str, object] public_sms_send_bulk_post(body, idempotency_key=idempotency_key)

Send one template to many numbers

Queues 1 to 1,000 messages on one approved template of any DLT type.
Every row is checked first. A wrong variable count is a 400 naming the row.
Invalid numbers, repeats and opted-out contacts are skipped and counted.
Refused with 402 and nothing queued when the wallet cannot cover the estimate.

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
    api_instance = splashifypro.SMSApi(api_client)
    body = None # object | { dlt_template_id, name?, messages: [{ to, variables[] }] }
    idempotency_key = 'idempotency_key_example' # str | Makes a retry safe: a repeat within 24 hours gets the same bulk_id back with its current status and replayed true, and nothing is queued again (optional)

    try:
        # Send one template to many numbers
        api_response = api_instance.public_sms_send_bulk_post(body, idempotency_key=idempotency_key)
        print("The response of SMSApi->public_sms_send_bulk_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling SMSApi->public_sms_send_bulk_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| { dlt_template_id, name?, messages: [{ to, variables[] }] } | 
 **idempotency_key** | **str**| Makes a retry safe: a repeat within 24 hours gets the same bulk_id back with its current status and replayed true, and nothing is queued again | [optional] 

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
**200** | { success, bulk_id, name, queued, skipped, skipped_rows, estimated_parts, estimated_cost, status, replayed? } |  -  |
**400** | Invalid request, a row&#39;s variables, or no sendable rows |  -  |
**401** | Missing or invalid API key |  -  |
**402** | Wallet balance below the estimate, nothing queued |  -  |
**404** | SMS not set up (code sms_not_set_up) or template not found |  -  |
**409** | The first request with this Idempotency-Key is still running (code idempotency_in_progress) |  -  |
**422** | This Idempotency-Key was used with a different body (code idempotency_key_reused) |  -  |
**429** | Rate limit exceeded, including 10 bulk sends a minute per account (code rate_limited) |  -  |
**503** | SMS sending unavailable, try again shortly |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_sms_send_post**
> Dict[str, object] public_sms_send_post(body, idempotency_key=idempotency_key)

Send one SMS

Sends one DLT SMS from an approved template to an Indian mobile number.
The template decides the DLT type, the sender ID and the price.
variables fill the template's {#var#} slots in order, 30 characters at most each.
A message the network refuses is a 200 with accepted false.

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
    api_instance = splashifypro.SMSApi(api_client)
    body = None # object | { to, dlt_template_id, variables[] }
    idempotency_key = 'idempotency_key_example' # str | Makes a retry safe: a repeat within 24 hours gets the first answer back with replayed true, and nothing is sent again (optional)

    try:
        # Send one SMS
        api_response = api_instance.public_sms_send_post(body, idempotency_key=idempotency_key)
        print("The response of SMSApi->public_sms_send_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling SMSApi->public_sms_send_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| { to, dlt_template_id, variables[] } | 
 **idempotency_key** | **str**| Makes a retry safe: a repeat within 24 hours gets the first answer back with replayed true, and nothing is sent again | [optional] 

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
**200** | { success, accepted, message_id, status, parts, unicode, charged, balance_after, message?, replayed? } |  -  |
**400** | Invalid request, number or variables |  -  |
**401** | Missing or invalid API key |  -  |
**402** | Wallet balance too low |  -  |
**403** | The contact opted out (code opted_out) |  -  |
**404** | SMS not set up (code sms_not_set_up) or template not found |  -  |
**409** | The first request with this Idempotency-Key is still running (code idempotency_in_progress) |  -  |
**422** | This Idempotency-Key was used with a different body (code idempotency_key_reused) |  -  |
**429** | Rate limit exceeded |  -  |
**503** | SMS sending unavailable, try again shortly |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_sms_senders_get**
> Dict[str, object] public_sms_senders_get()

SMS sender IDs

The sender IDs on the account. status is approved, pending or rejected;
type is the DLT type the sender ID was registered for.

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
    api_instance = splashifypro.SMSApi(api_client)

    try:
        # SMS sender IDs
        api_response = api_instance.public_sms_senders_get()
        print("The response of SMSApi->public_sms_senders_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling SMSApi->public_sms_senders_get: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

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
**200** | { success, senders: [{ sender_id, type, status }] } |  -  |
**401** | Missing or invalid API key |  -  |
**404** | SMS not set up (code sms_not_set_up) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_sms_templates_get**
> Dict[str, object] public_sms_templates_get()

Approved SMS templates

The approved DLT templates on the account. type is promotional, transactional,
service_implicit or service_explicit; variables is how many {#var#} slots the body has.

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
    api_instance = splashifypro.SMSApi(api_client)

    try:
        # Approved SMS templates
        api_response = api_instance.public_sms_templates_get()
        print("The response of SMSApi->public_sms_templates_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling SMSApi->public_sms_templates_get: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

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
**200** | { success, templates: [{ dlt_template_id, name, type, sender_id, body, variables }] } |  -  |
**401** | Missing or invalid API key |  -  |
**404** | SMS not set up (code sms_not_set_up) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

