# splashifypro.ContactsApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**public_apis_users_post**](ContactsApi.md#public_apis_users_post) | **POST** /public/apis/users | List contacts (paginated, filterable)


# **public_apis_users_post**
> Dict[str, object] public_apis_users_post(offset=offset, limit=limit, body=body)

List contacts (paginated, filterable)

Returns a paginated list of contacts (customers) for the
authenticated account. Filters are applied in-memory and
support traits: created_at_utc, modified_at_utc, phone_number,
name, email, whatsapp_opted_in, plus any custom column from
the contact's column_data.

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
    api_instance = splashifypro.ContactsApi(api_client)
    offset = 56 # int | Pagination offset (default 0) (optional)
    limit = 56 # int | Page size (default 100, max 500) (optional)
    body = None # object | Optional filter object: {filters:[{trait,op,val}]} (optional)

    try:
        # List contacts (paginated, filterable)
        api_response = api_instance.public_apis_users_post(offset=offset, limit=limit, body=body)
        print("The response of ContactsApi->public_apis_users_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ContactsApi->public_apis_users_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **offset** | **int**| Pagination offset (default 0) | [optional] 
 **limit** | **int**| Page size (default 100, max 500) | [optional] 
 **body** | **object**| Optional filter object: {filters:[{trait,op,val}]} | [optional] 

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
**200** | { result: true, data: { customers: [...], total_customers, has_next_page } } |  -  |
**401** | Missing/invalid API key |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

