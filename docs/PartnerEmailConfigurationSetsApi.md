# splashifypro.PartnerEmailConfigurationSetsApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**partner_email_configuration_sets_get**](PartnerEmailConfigurationSetsApi.md#partner_email_configuration_sets_get) | **GET** /partner/email/configuration-sets | List configuration sets
[**partner_email_configuration_sets_id_delete**](PartnerEmailConfigurationSetsApi.md#partner_email_configuration_sets_id_delete) | **DELETE** /partner/email/configuration-sets/{id} | Delete configuration set
[**partner_email_configuration_sets_id_get**](PartnerEmailConfigurationSetsApi.md#partner_email_configuration_sets_id_get) | **GET** /partner/email/configuration-sets/{id} | Get configuration set
[**partner_email_configuration_sets_id_patch**](PartnerEmailConfigurationSetsApi.md#partner_email_configuration_sets_id_patch) | **PATCH** /partner/email/configuration-sets/{id} | Update configuration set
[**partner_email_configuration_sets_post**](PartnerEmailConfigurationSetsApi.md#partner_email_configuration_sets_post) | **POST** /partner/email/configuration-sets | Create configuration set


# **partner_email_configuration_sets_get**
> Dict[str, object] partner_email_configuration_sets_get(customer_id=customer_id)

List configuration sets

Returns every configuration set for the authenticated
partner. A configuration set is a logical send context —
partners typically create one per downstream end-customer
or per app surface. Optional customer_id filter scopes
the response to one downstream tenant.

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
    api_instance = splashifypro.PartnerEmailConfigurationSetsApi(api_client)
    customer_id = 'customer_id_example' # str | Filter to one downstream customer (optional)

    try:
        # List configuration sets
        api_response = api_instance.partner_email_configuration_sets_get(customer_id=customer_id)
        print("The response of PartnerEmailConfigurationSetsApi->partner_email_configuration_sets_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailConfigurationSetsApi->partner_email_configuration_sets_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **customer_id** | **str**| Filter to one downstream customer | [optional] 

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
**200** | { success: true, configuration_sets: [...] } |  -  |
**401** | Missing/invalid API key |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **partner_email_configuration_sets_id_delete**
> Dict[str, object] partner_email_configuration_sets_id_delete(id)

Delete configuration set

Removes a configuration set + its event destinations.
Sends already in flight against the deleted set
complete normally; future sends referencing the deleted
set fall back to "no config set" defaults (tracking on,
no per-config-set webhooks).

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
    api_instance = splashifypro.PartnerEmailConfigurationSetsApi(api_client)
    id = 'id_example' # str | Config set id

    try:
        # Delete configuration set
        api_response = api_instance.partner_email_configuration_sets_id_delete(id)
        print("The response of PartnerEmailConfigurationSetsApi->partner_email_configuration_sets_id_delete:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailConfigurationSetsApi->partner_email_configuration_sets_id_delete: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| Config set id | 

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
**200** | { success: true } |  -  |
**401** | Missing/invalid API key |  -  |
**404** | Config set not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **partner_email_configuration_sets_id_get**
> Dict[str, object] partner_email_configuration_sets_id_get(id)

Get configuration set

Returns one configuration set by id, including the
current track_opens / track_clicks flags.

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
    api_instance = splashifypro.PartnerEmailConfigurationSetsApi(api_client)
    id = 'id_example' # str | Config set id

    try:
        # Get configuration set
        api_response = api_instance.partner_email_configuration_sets_id_get(id)
        print("The response of PartnerEmailConfigurationSetsApi->partner_email_configuration_sets_id_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailConfigurationSetsApi->partner_email_configuration_sets_id_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| Config set id | 

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
**200** | { success: true, configuration_set: {...} } |  -  |
**401** | Missing/invalid API key |  -  |
**404** | Config set not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **partner_email_configuration_sets_id_patch**
> Dict[str, object] partner_email_configuration_sets_id_patch(id, body)

Update configuration set

Patches an existing configuration set. All fields
optional — only the keys you supply are updated. Use
this to flip track_opens / track_clicks on existing
config sets without recreating them.

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
    api_instance = splashifypro.PartnerEmailConfigurationSetsApi(api_client)
    id = 'id_example' # str | Config set id
    body = None # object | Any subset of: name, description, suppression_options, reputation_tracking_enabled, sending_enabled, track_opens, track_clicks, custom_redirect_domain, tags.

    try:
        # Update configuration set
        api_response = api_instance.partner_email_configuration_sets_id_patch(id, body)
        print("The response of PartnerEmailConfigurationSetsApi->partner_email_configuration_sets_id_patch:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailConfigurationSetsApi->partner_email_configuration_sets_id_patch: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| Config set id | 
 **body** | **object**| Any subset of: name, description, suppression_options, reputation_tracking_enabled, sending_enabled, track_opens, track_clicks, custom_redirect_domain, tags. | 

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
**200** | { success: true, configuration_set: {...} } |  -  |
**400** | Validation error |  -  |
**401** | Missing/invalid API key |  -  |
**404** | Config set not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **partner_email_configuration_sets_post**
> Dict[str, object] partner_email_configuration_sets_post(body)

Create configuration set

Creates a new configuration set. New flags track_opens
+ track_clicks (both default true) control whether
Splashify Pro injects the open-tracking pixel + rewrites
<a href> URLs through the click-tracking redirect on
emails sent through this config set. Set both to false
for transactional / privacy-sensitive flows. See
partner-docs.splashifypro.com/webhooks/tracking for the
full guide.

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
    api_instance = splashifypro.PartnerEmailConfigurationSetsApi(api_client)
    body = None # object | Config set fields. Required: name. Optional: description, customer_id, suppression_options (NONE / BOUNCE / COMPLAINT / BOUNCE_AND_COMPLAINT), reputation_tracking_enabled (default true), sending_enabled (default true), track_opens (default true), track_clicks (default true), custom_redirect_domain, tags.

    try:
        # Create configuration set
        api_response = api_instance.partner_email_configuration_sets_post(body)
        print("The response of PartnerEmailConfigurationSetsApi->partner_email_configuration_sets_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailConfigurationSetsApi->partner_email_configuration_sets_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Config set fields. Required: name. Optional: description, customer_id, suppression_options (NONE / BOUNCE / COMPLAINT / BOUNCE_AND_COMPLAINT), reputation_tracking_enabled (default true), sending_enabled (default true), track_opens (default true), track_clicks (default true), custom_redirect_domain, tags. | 

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
**201** | { success: true, configuration_set: {...} } |  -  |
**400** | Validation error |  -  |
**401** | Missing/invalid API key |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

