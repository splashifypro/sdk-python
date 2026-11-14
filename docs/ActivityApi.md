# splashifypro.ActivityApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**app_activity_logs_get**](ActivityApi.md#app_activity_logs_get) | **GET** /app/activity-logs | List activity logs


# **app_activity_logs_get**
> Dict[str, object] app_activity_logs_get(action=action, entity_type=entity_type, entity_id=entity_id, actor_id=actor_id, limit=limit, cursor=cursor)

List activity logs

Paginated audit trail of account activity. total is a real
row count; page with cursor/next_cursor, not offset.

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
    api_instance = splashifypro.ActivityApi(api_client)
    action = 'action_example' # str | Filter by action (optional)
    entity_type = 'entity_type_example' # str | Filter by entity type (optional)
    entity_id = 'entity_id_example' # str | Filter by entity id (optional)
    actor_id = 'actor_id_example' # str | Filter by actor id (optional)
    limit = 56 # int | Page size, default 50, max 200 (optional)
    cursor = 'cursor_example' # str | Opaque cursor from a previous response's next_cursor (optional)

    try:
        # List activity logs
        api_response = api_instance.app_activity_logs_get(action=action, entity_type=entity_type, entity_id=entity_id, actor_id=actor_id, limit=limit, cursor=cursor)
        print("The response of ActivityApi->app_activity_logs_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ActivityApi->app_activity_logs_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **action** | **str**| Filter by action | [optional] 
 **entity_type** | **str**| Filter by entity type | [optional] 
 **entity_id** | **str**| Filter by entity id | [optional] 
 **actor_id** | **str**| Filter by actor id | [optional] 
 **limit** | **int**| Page size, default 50, max 200 | [optional] 
 **cursor** | **str**| Opaque cursor from a previous response&#39;s next_cursor | [optional] 

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
**200** | { success, logs, total, next_cursor } |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

