# splashifypro.TemplatesApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**public_templates_get**](TemplatesApi.md#public_templates_get) | **GET** /public/templates | List templates
[**public_templates_insights_get**](TemplatesApi.md#public_templates_insights_get) | **GET** /public/templates/insights | Template insights


# **public_templates_get**
> Dict[str, object] public_templates_get(status=status)

List templates

List the WhatsApp message templates of your account, with their approval status.

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
    api_instance = splashifypro.TemplatesApi(api_client)
    status = 'status_example' # str | Only this status, for example APPROVED (optional)

    try:
        # List templates
        api_response = api_instance.public_templates_get(status=status)
        print("The response of TemplatesApi->public_templates_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling TemplatesApi->public_templates_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **status** | **str**| Only this status, for example APPROVED | [optional] 

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
**200** | { result: true, templates: [...], count: n } |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_templates_insights_get**
> Dict[str, object] public_templates_insights_get(days=days)

Template insights

Sent, delivered, read, button click and reply rates per template over the last 30 or 90 days, with the account average.

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
    api_instance = splashifypro.TemplatesApi(api_client)
    days = 56 # int | 30 (default) or 90 (optional)

    try:
        # Template insights
        api_response = api_instance.public_templates_insights_get(days=days)
        print("The response of TemplatesApi->public_templates_insights_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling TemplatesApi->public_templates_insights_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **days** | **int**| 30 (default) or 90 | [optional] 

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
**200** | { success, days, broadcasts, rows[], averages } |  -  |
**401** | Missing or invalid API key |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

