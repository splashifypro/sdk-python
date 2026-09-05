# splashifypro.MediaApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**app_media_get**](MediaApi.md#app_media_get) | **GET** /app/media | List uploaded media files


# **app_media_get**
> Dict[str, object] app_media_get(type=type)

List uploaded media files

storage_used/storage_limit are included so a caller does not
need a second round-trip to GET /app/media/storage.

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
    api_instance = splashifypro.MediaApi(api_client)
    type = 'type_example' # str | Filter: image, video, audio, or document (optional)

    try:
        # List uploaded media files
        api_response = api_instance.app_media_get(type=type)
        print("The response of MediaApi->app_media_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling MediaApi->app_media_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **type** | **str**| Filter: image, video, audio, or document | [optional] 

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
**200** | { success, files, count, storage_used, storage_limit } |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

