# splashifypro.WalletApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**app_wallet_alerts_get**](WalletApi.md#app_wallet_alerts_get) | **GET** /app/wallet/alerts | Get the low-balance alert threshold
[**app_wallet_alerts_put**](WalletApi.md#app_wallet_alerts_put) | **PUT** /app/wallet/alerts | Set the low-balance alert threshold
[**app_wallet_info_get**](WalletApi.md#app_wallet_info_get) | **GET** /app/wallet/info | Wallet balance


# **app_wallet_alerts_get**
> Dict[str, object] app_wallet_alerts_get()

Get the low-balance alert threshold

The balance at which the wallet_low webhook fires.
is_default is true when the account has not configured one
and the ₹100 platform default is in effect.

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
    api_instance = splashifypro.WalletApi(api_client)

    try:
        # Get the low-balance alert threshold
        api_response = api_instance.app_wallet_alerts_get()
        print("The response of WalletApi->app_wallet_alerts_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling WalletApi->app_wallet_alerts_get: %s\n" % e)
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
**200** | { success, low_balance_threshold, is_default, currency } |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_wallet_alerts_put**
> Dict[str, object] app_wallet_alerts_put(body)

Set the low-balance alert threshold

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
    api_instance = splashifypro.WalletApi(api_client)
    body = None # object | { low_balance_threshold: number }

    try:
        # Set the low-balance alert threshold
        api_response = api_instance.app_wallet_alerts_put(body)
        print("The response of WalletApi->app_wallet_alerts_put:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling WalletApi->app_wallet_alerts_put: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| { low_balance_threshold: number } | 

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
**200** | { success, low_balance_threshold } |  -  |
**400** | low_balance_threshold must be a positive number |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_wallet_info_get**
> Dict[str, object] app_wallet_info_get()

Wallet balance

Wallet balance and last recharge info for the current app
user. spent_balance accumulates from every wallet debit
(direct sends and broadcasts) — accounts predating this
accumulation may see a jump rather than a full history.

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
    api_instance = splashifypro.WalletApi(api_client)

    try:
        # Wallet balance
        api_response = api_instance.app_wallet_info_get()
        print("The response of WalletApi->app_wallet_info_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling WalletApi->app_wallet_info_get: %s\n" % e)
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
**200** | OK |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

