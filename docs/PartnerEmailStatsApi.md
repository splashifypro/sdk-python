# splashifypro.PartnerEmailStatsApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**partner_email_quotas_get**](PartnerEmailStatsApi.md#partner_email_quotas_get) | **GET** /partner/email/quotas | Get sending quotas
[**partner_email_stats_get**](PartnerEmailStatsApi.md#partner_email_stats_get) | **GET** /partner/email/stats | Get sending statistics


# **partner_email_quotas_get**
> Dict[str, object] partner_email_quotas_get()

Get sending quotas

Returns the partner's daily send quota, peak send rate,
sandbox flag, today's send count, and reputation status.
Mirrors AWS SES GetSendQuota.

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
    api_instance = splashifypro.PartnerEmailStatsApi(api_client)

    try:
        # Get sending quotas
        api_response = api_instance.partner_email_quotas_get()
        print("The response of PartnerEmailStatsApi->partner_email_quotas_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailStatsApi->partner_email_quotas_get: %s\n" % e)
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
**200** | { success: true, quota: {...} } |  -  |
**401** | Missing/invalid API key |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **partner_email_stats_get**
> Dict[str, object] partner_email_stats_get(days=days, config_set_id=config_set_id)

Get sending statistics

Day-by-day counters for sent / delivered / bounced /
complained / opened / clicked / rejected over the last
N days. Filterable by configuration set.

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
    api_instance = splashifypro.PartnerEmailStatsApi(api_client)
    days = 56 # int | Window size (default 30, max 90) (optional)
    config_set_id = 'config_set_id_example' # str | Filter to one configuration set (optional)

    try:
        # Get sending statistics
        api_response = api_instance.partner_email_stats_get(days=days, config_set_id=config_set_id)
        print("The response of PartnerEmailStatsApi->partner_email_stats_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailStatsApi->partner_email_stats_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **days** | **int**| Window size (default 30, max 90) | [optional] 
 **config_set_id** | **str**| Filter to one configuration set | [optional] 

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
**200** | { success: true, stats: [{day_bucket, sent_count, ...}] } |  -  |
**401** | Missing/invalid API key |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

