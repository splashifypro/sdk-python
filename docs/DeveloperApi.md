# splashifypro.DeveloperApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**app_developer_opt_out_error_put**](DeveloperApi.md#app_developer_opt_out_error_put) | **PUT** /app/developer/opt-out-error | Toggle opt-out send errors
[**app_developer_secret_key_generate_post**](DeveloperApi.md#app_developer_secret_key_generate_post) | **POST** /app/developer/secret-key/generate | Generate (or regenerate) the API secret key
[**app_developer_settings_get**](DeveloperApi.md#app_developer_settings_get) | **GET** /app/developer/settings | Get developer settings
[**app_developer_webhook_put**](DeveloperApi.md#app_developer_webhook_put) | **PUT** /app/developer/webhook | Configure the console webhook


# **app_developer_opt_out_error_put**
> Dict[str, object] app_developer_opt_out_error_put(body)

Toggle opt-out send errors

When enabled, the Message Send API returns an error instead
of silently no-op'ing when called for a contact who has
opted out.

### Example

* Api Key Authentication (BearerAuth):

```python
import splashifypro
from splashifypro.models.handlers_update_opt_out_error_request import HandlersUpdateOptOutErrorRequest
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
    api_instance = splashifypro.DeveloperApi(api_client)
    body = splashifypro.HandlersUpdateOptOutErrorRequest() # HandlersUpdateOptOutErrorRequest | { enabled: boolean }

    try:
        # Toggle opt-out send errors
        api_response = api_instance.app_developer_opt_out_error_put(body)
        print("The response of DeveloperApi->app_developer_opt_out_error_put:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling DeveloperApi->app_developer_opt_out_error_put: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**HandlersUpdateOptOutErrorRequest**](HandlersUpdateOptOutErrorRequest.md)| { enabled: boolean } | 

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
**200** | { success, message } |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_developer_secret_key_generate_post**
> Dict[str, object] app_developer_secret_key_generate_post()

Generate (or regenerate) the API secret key

Invalidates any existing sk_live_ key immediately. This is
the Authorization key for /api/v1/public/* requests — a
different secret from any webhook's signing secret.

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
    api_instance = splashifypro.DeveloperApi(api_client)

    try:
        # Generate (or regenerate) the API secret key
        api_response = api_instance.app_developer_secret_key_generate_post()
        print("The response of DeveloperApi->app_developer_secret_key_generate_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling DeveloperApi->app_developer_secret_key_generate_post: %s\n" % e)
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
**200** | { success, message, secret_key } |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_developer_settings_get**
> Dict[str, object] app_developer_settings_get()

Get developer settings

webhook_id/webhook_secret/webhook_active describe the real
app_webhooks row backing this page's Configure Webhook
editor — the same object GET /app/webhooks lists and
POST /app/webhooks/{id}/rotate-secret operates on. Deliveries
to webhook_url are signed with webhook_secret exactly like
any webhook created through that API.

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
    api_instance = splashifypro.DeveloperApi(api_client)

    try:
        # Get developer settings
        api_response = api_instance.app_developer_settings_get()
        print("The response of DeveloperApi->app_developer_settings_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling DeveloperApi->app_developer_settings_get: %s\n" % e)
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

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_developer_webhook_put**
> Dict[str, object] app_developer_webhook_put(body)

Configure the console webhook

Creates or updates the single app_webhooks row backing this
page — its id and signing secret stay stable across edits,
so changing the URL never invalidates signature
verification. Deliveries are signed exactly like a webhook
created via POST /app/webhooks (same headers, same HMAC
scheme) — see Verifying signatures in the webhooks guide.
An empty webhook_url deactivates it without deleting it;
reconfiguring later reuses the same id and secret. Manage
it like any other webhook via GET/PATCH/DELETE
/app/webhooks/{id} and /rotate-secret using the webhook_id
returned by GET /app/developer/settings.

### Example

* Api Key Authentication (BearerAuth):

```python
import splashifypro
from splashifypro.models.handlers_update_webhook_request import HandlersUpdateWebhookRequest
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
    api_instance = splashifypro.DeveloperApi(api_client)
    body = splashifypro.HandlersUpdateWebhookRequest() # HandlersUpdateWebhookRequest | { webhook_url: string, webhook_events: string[] }

    try:
        # Configure the console webhook
        api_response = api_instance.app_developer_webhook_put(body)
        print("The response of DeveloperApi->app_developer_webhook_put:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling DeveloperApi->app_developer_webhook_put: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**HandlersUpdateWebhookRequest**](HandlersUpdateWebhookRequest.md)| { webhook_url: string, webhook_events: string[] } | 

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
**200** | { success, message, webhook_id } |  -  |
**400** | Invalid URL / events |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

