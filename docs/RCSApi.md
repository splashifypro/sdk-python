# splashifypro.RCSApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**public_rcs_send_post**](RCSApi.md#public_rcs_send_post) | **POST** /public/rcs/send | Send an RCS message
[**public_rcs_send_template_post**](RCSApi.md#public_rcs_send_template_post) | **POST** /public/rcs/send-template | Send an RCS template message


# **public_rcs_send_post**
> Dict[str, object] public_rcs_send_post(body)

Send an RCS message

Send any RCS message type — text, media, card or multiple_cards.

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
    api_instance = splashifypro.RCSApi(api_client)
    body = None # object | RCS message payload (to, type, and the type-specific fields)

    try:
        # Send an RCS message
        api_response = api_instance.public_rcs_send_post(body)
        print("The response of RCSApi->public_rcs_send_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling RCSApi->public_rcs_send_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| RCS message payload (to, type, and the type-specific fields) | 

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
**200** | { success, rcs_message_id, message_id, conversation_id } |  -  |
**400** | Invalid request body |  -  |
**401** | Missing/invalid API key |  -  |
**402** | Insufficient wallet balance |  -  |
**403** | RCS not enabled for this account |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_rcs_send_template_post**
> Dict[str, object] public_rcs_send_template_post(body)

Send an RCS template message

Send a stored, approved RCS template. Positional {#varN#} placeholders are filled from the variables array, in order.

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
    api_instance = splashifypro.RCSApi(api_client)
    body = None # object | RCS template payload (to, template_id, variables)

    try:
        # Send an RCS template message
        api_response = api_instance.public_rcs_send_template_post(body)
        print("The response of RCSApi->public_rcs_send_template_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling RCSApi->public_rcs_send_template_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| RCS template payload (to, template_id, variables) | 

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
**200** | { success, rcs_message_id, message_id, conversation_id } |  -  |
**400** | Invalid request body |  -  |
**401** | Missing/invalid API key |  -  |
**402** | Insufficient wallet balance |  -  |
**403** | RCS not enabled for this account |  -  |
**404** | Template not found |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

