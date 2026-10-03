# splashifypro.ExpensesApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**app_expenses_billing_logs_get**](ExpensesApi.md#app_expenses_billing_logs_get) | **GET** /app/expenses/billing-logs | Billing log entries
[**app_expenses_summary_get**](ExpensesApi.md#app_expenses_summary_get) | **GET** /app/expenses/summary | Expense summary


# **app_expenses_billing_logs_get**
> Dict[str, object] app_expenses_billing_logs_get(period=period, limit=limit, cursor=cursor)

Billing log entries

Paginated per-message deduction log. total is a real count of
billable rows for the period, not the size of one page; page
with cursor/next_cursor.

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
    api_instance = splashifypro.ExpensesApi(api_client)
    period = 'period_example' # str | 7d, 30d, 3m, 6m, or all — default 30d (optional)
    limit = 56 # int | Page size, default 100, max 500 (optional)
    cursor = 'cursor_example' # str | Opaque cursor from a previous response's next_cursor (optional)

    try:
        # Billing log entries
        api_response = api_instance.app_expenses_billing_logs_get(period=period, limit=limit, cursor=cursor)
        print("The response of ExpensesApi->app_expenses_billing_logs_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ExpensesApi->app_expenses_billing_logs_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **period** | **str**| 7d, 30d, 3m, 6m, or all — default 30d | [optional] 
 **limit** | **int**| Page size, default 100, max 500 | [optional] 
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

# **app_expenses_summary_get**
> Dict[str, object] app_expenses_summary_get(period=period)

Expense summary

Message deduction stats: total spent, breakdown by category,
total messages, and real sent/delivered counts from WhatsApp
status (not the account's billing-timing preference). period
in the response is the resolved value, not the raw query
param — an unrecognised value silently falls back to 30d.

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
    api_instance = splashifypro.ExpensesApi(api_client)
    period = 'period_example' # str | 7d, 30d, 3m, 6m, or all — default 30d (optional)

    try:
        # Expense summary
        api_response = api_instance.app_expenses_summary_get(period=period)
        print("The response of ExpensesApi->app_expenses_summary_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ExpensesApi->app_expenses_summary_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **period** | **str**| 7d, 30d, 3m, 6m, or all — default 30d | [optional] 

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
**200** | OK |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

