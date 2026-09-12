# splashifypro.DripCampaignsApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**public_drip_campaigns_get**](DripCampaignsApi.md#public_drip_campaigns_get) | **GET** /public/drip/campaigns | List drip campaigns
[**public_drip_start_post**](DripCampaignsApi.md#public_drip_start_post) | **POST** /public/drip/start | Start a drip campaign for a contact


# **public_drip_campaigns_get**
> Dict[str, object] public_drip_campaigns_get()

List drip campaigns

Returns this account's drip campaigns with their id, name and status. Use the campaign_id with the start endpoint.

### Example


```python
import splashifypro
from splashifypro.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://apis.splashifypro.com/api/v1
# See configuration.py for a list of all supported configuration parameters.
configuration = splashifypro.Configuration(
    host = "https://apis.splashifypro.com/api/v1"
)


# Enter a context with an instance of the API client
with splashifypro.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = splashifypro.DripCampaignsApi(api_client)

    try:
        # List drip campaigns
        api_response = api_instance.public_drip_campaigns_get()
        print("The response of DripCampaignsApi->public_drip_campaigns_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling DripCampaignsApi->public_drip_campaigns_get: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

**Dict[str, object]**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | OK |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_drip_start_post**
> Dict[str, object] public_drip_start_post(request)

Start a drip campaign for a contact

Enrols one contact into a drip campaign. The first message goes out after that step's configured wait, and the rest follow on their own schedule. The campaign must be running. Safe to call twice — a contact already in the campaign is reported, not enrolled again.

### Example


```python
import splashifypro
from splashifypro.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://apis.splashifypro.com/api/v1
# See configuration.py for a list of all supported configuration parameters.
configuration = splashifypro.Configuration(
    host = "https://apis.splashifypro.com/api/v1"
)


# Enter a context with an instance of the API client
with splashifypro.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = splashifypro.DripCampaignsApi(api_client)
    request = None # object | campaign_id and phone_number

    try:
        # Start a drip campaign for a contact
        api_response = api_instance.public_drip_start_post(request)
        print("The response of DripCampaignsApi->public_drip_start_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling DripCampaignsApi->public_drip_start_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **request** | **object**| campaign_id and phone_number | 

### Return type

**Dict[str, object]**

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | OK |  -  |
**400** | Bad Request |  -  |
**404** | Not Found |  -  |
**409** | Conflict |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

