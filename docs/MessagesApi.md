# splashifypro.MessagesApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**app_messages_send_media_post**](MessagesApi.md#app_messages_send_media_post) | **POST** /app/messages/send-media | Send a media message
[**app_messages_typing_indicator_post**](MessagesApi.md#app_messages_typing_indicator_post) | **POST** /app/messages/typing-indicator | Send a typing indicator
[**public_message_post**](MessagesApi.md#public_message_post) | **POST** /public/message | Send a WhatsApp message


# **app_messages_send_media_post**
> Dict[str, object] app_messages_send_media_post(body)

Send a media message

Sends an image, video, audio, or document message. Pass
either media_url (any public URL) or media_id (a file
previously uploaded via POST /app/media) — not both required.

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
    api_instance = splashifypro.MessagesApi(api_client)
    body = None # object | { to, media_type, media_url|media_id, caption?, filename?, voice? }

    try:
        # Send a media message
        api_response = api_instance.app_messages_send_media_post(body)
        print("The response of MessagesApi->app_messages_send_media_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling MessagesApi->app_messages_send_media_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| { to, media_type, media_url|media_id, caption?, filename?, voice? } | 

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
**200** | { success: true, wa_message_id: string } |  -  |
**400** | Missing/invalid fields |  -  |
**401** | Unauthorized |  -  |
**404** | media_id not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_messages_typing_indicator_post**
> Dict[str, object] app_messages_typing_indicator_post(body)

Send a typing indicator

Shows the typing indicator on the given inbound message's
conversation. WhatsApp dismisses it after ~25s or on the next
message from this business, whichever comes first.

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
    api_instance = splashifypro.MessagesApi(api_client)
    body = None # object | { message_id: string }

    try:
        # Send a typing indicator
        api_response = api_instance.app_messages_typing_indicator_post(body)
        print("The response of MessagesApi->app_messages_typing_indicator_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling MessagesApi->app_messages_typing_indicator_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| { message_id: string } | 

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
**200** | { success: true, dismissed_after_seconds: 25 } |  -  |
**400** | message_id is required |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_message_post**
> Dict[str, object] public_message_post(body)

Send a WhatsApp message

Send any supported WhatsApp message type to a contact.
See type-specific request examples in the per-message docs.

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
    api_instance = splashifypro.MessagesApi(api_client)
    body = None # object | Send message payload (type, phoneNumber, data)

    try:
        # Send a WhatsApp message
        api_response = api_instance.public_message_post(body)
        print("The response of MessagesApi->public_message_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling MessagesApi->public_message_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Send message payload (type, phoneNumber, data) | 

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
**200** | { result: true, message: ..., id: &lt;message_id&gt; } |  -  |
**400** | Invalid request body |  -  |
**401** | Missing/invalid API key |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

