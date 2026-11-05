# splashifypro.BroadcastsApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**public_broadcasts_id_auto_retarget_delete**](BroadcastsApi.md#public_broadcasts_id_auto_retarget_delete) | **DELETE** /public/broadcasts/{id}/auto-retarget | Cancel an automatic retarget
[**public_broadcasts_id_auto_retarget_get**](BroadcastsApi.md#public_broadcasts_id_auto_retarget_get) | **GET** /public/broadcasts/{id}/auto-retarget | Get a broadcast&#39;s automatic retarget
[**public_broadcasts_id_auto_retarget_post**](BroadcastsApi.md#public_broadcasts_id_auto_retarget_post) | **POST** /public/broadcasts/{id}/auto-retarget | Schedule an automatic retarget


# **public_broadcasts_id_auto_retarget_delete**
> Dict[str, object] public_broadcasts_id_auto_retarget_delete(id)

Cancel an automatic retarget

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
    api_instance = splashifypro.BroadcastsApi(api_client)
    id = 'id_example' # str | Broadcast id

    try:
        # Cancel an automatic retarget
        api_response = api_instance.public_broadcasts_id_auto_retarget_delete(id)
        print("The response of BroadcastsApi->public_broadcasts_id_auto_retarget_delete:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling BroadcastsApi->public_broadcasts_id_auto_retarget_delete: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| Broadcast id | 

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
**200** | { success, rule } (rule status cancelled) |  -  |
**400** | Invalid broadcast id |  -  |
**401** | Missing or invalid API key |  -  |
**409** | No waiting retarget: none, or it already sent |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_broadcasts_id_auto_retarget_get**
> Dict[str, object] public_broadcasts_id_auto_retarget_get(id)

Get a broadcast's automatic retarget

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
    api_instance = splashifypro.BroadcastsApi(api_client)
    id = 'id_example' # str | Broadcast id (GraphQL broadcasts query)

    try:
        # Get a broadcast's automatic retarget
        api_response = api_instance.public_broadcasts_id_auto_retarget_get(id)
        print("The response of BroadcastsApi->public_broadcasts_id_auto_retarget_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling BroadcastsApi->public_broadcasts_id_auto_retarget_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| Broadcast id (GraphQL broadcasts query) | 

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
**200** | { success, rule } (rule is null when none) |  -  |
**400** | Invalid broadcast id |  -  |
**401** | Missing or invalid API key |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_broadcasts_id_auto_retarget_post**
> Dict[str, object] public_broadcasts_id_auto_retarget_post(id, body)

Schedule an automatic retarget

After delay_hours (1 to 72), sends a follow-up to the people who got the broadcast but did not read it. Same template unless template_id is given (WhatsApp only), with template_params as a JSON string of its components. Charged like any broadcast when it sends.

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
    api_instance = splashifypro.BroadcastsApi(api_client)
    id = 'id_example' # str | Broadcast id
    body = None # object | { delay_hours, consent_attested: true, template_id?, template_params? }

    try:
        # Schedule an automatic retarget
        api_response = api_instance.public_broadcasts_id_auto_retarget_post(id, body)
        print("The response of BroadcastsApi->public_broadcasts_id_auto_retarget_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling BroadcastsApi->public_broadcasts_id_auto_retarget_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| Broadcast id | 
 **body** | **object**| { delay_hours, consent_attested: true, template_id?, template_params? } | 

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
**201** | { success, rule } |  -  |
**400** | Consent not confirmed, wait out of range, or template not found |  -  |
**401** | Missing or invalid API key |  -  |
**404** | Broadcast not found |  -  |
**409** | Broadcast not finished, or it already has a retarget |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

