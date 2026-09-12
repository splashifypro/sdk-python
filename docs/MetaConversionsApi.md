# splashifypro.MetaConversionsApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**public_capi_send_event_post**](MetaConversionsApi.md#public_capi_send_event_post) | **POST** /public/capi/send-event | Send a Meta Conversion API event


# **public_capi_send_event_post**
> Dict[str, object] public_capi_send_event_post(body)

Send a Meta Conversion API event

Fire a server-side Meta Pixel / Conversions API event for
a contact identified by phone number. Useful for ROI
attribution on Click-to-WhatsApp ads. Event names: Lead,
Purchase, AddToCart, etc. Requires Meta Ads OAuth completed
in the dashboard.

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
    api_instance = splashifypro.MetaConversionsApi(api_client)
    body = None # object | CAPI payload (event_name, phone_number, value, currency)

    try:
        # Send a Meta Conversion API event
        api_response = api_instance.public_capi_send_event_post(body)
        print("The response of MetaConversionsApi->public_capi_send_event_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling MetaConversionsApi->public_capi_send_event_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| CAPI payload (event_name, phone_number, value, currency) | 

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
**200** | { success: true } |  -  |
**400** | Invalid event_name / Meta Ads not connected |  -  |
**401** | Missing/invalid API key |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

