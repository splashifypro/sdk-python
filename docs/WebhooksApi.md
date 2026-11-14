# splashifypro.WebhooksApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**app_webhooks_events_get**](WebhooksApi.md#app_webhooks_events_get) | **GET** /app/webhooks/events | List subscribable webhook event names
[**app_webhooks_get**](WebhooksApi.md#app_webhooks_get) | **GET** /app/webhooks | List registered webhooks
[**app_webhooks_id_delete**](WebhooksApi.md#app_webhooks_id_delete) | **DELETE** /app/webhooks/{id} | Delete a webhook
[**app_webhooks_id_get**](WebhooksApi.md#app_webhooks_id_get) | **GET** /app/webhooks/{id} | Get a webhook
[**app_webhooks_id_patch**](WebhooksApi.md#app_webhooks_id_patch) | **PATCH** /app/webhooks/{id} | Update a webhook
[**app_webhooks_id_rotate_secret_post**](WebhooksApi.md#app_webhooks_id_rotate_secret_post) | **POST** /app/webhooks/{id}/rotate-secret | Rotate a webhook&#39;s signing secret
[**app_webhooks_id_test_post**](WebhooksApi.md#app_webhooks_id_test_post) | **POST** /app/webhooks/{id}/test | Send a test event
[**app_webhooks_post**](WebhooksApi.md#app_webhooks_post) | **POST** /app/webhooks | Register a webhook


# **app_webhooks_events_get**
> Dict[str, object] app_webhooks_events_get()

List subscribable webhook event names

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
    api_instance = splashifypro.WebhooksApi(api_client)

    try:
        # List subscribable webhook event names
        api_response = api_instance.app_webhooks_events_get()
        print("The response of WebhooksApi->app_webhooks_events_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling WebhooksApi->app_webhooks_events_get: %s\n" % e)
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
**200** | { success, events } |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_webhooks_get**
> Dict[str, object] app_webhooks_get()

List registered webhooks

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
    api_instance = splashifypro.WebhooksApi(api_client)

    try:
        # List registered webhooks
        api_response = api_instance.app_webhooks_get()
        print("The response of WebhooksApi->app_webhooks_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling WebhooksApi->app_webhooks_get: %s\n" % e)
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
**200** | { success, webhooks } |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_webhooks_id_delete**
> Dict[str, object] app_webhooks_id_delete(id)

Delete a webhook

Deleting the webhook backing Settings → Developer →
Configure Webhook resets that page to "not configured"
rather than leaving it pointing at a dangling id.

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
    api_instance = splashifypro.WebhooksApi(api_client)
    id = 'id_example' # str | Webhook ID

    try:
        # Delete a webhook
        api_response = api_instance.app_webhooks_id_delete(id)
        print("The response of WebhooksApi->app_webhooks_id_delete:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling WebhooksApi->app_webhooks_id_delete: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| Webhook ID | 

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
**200** | { success, message } |  -  |
**404** | Webhook not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_webhooks_id_get**
> Dict[str, object] app_webhooks_id_get(id)

Get a webhook

Returns one webhook regardless of whether it was created via
this API or Settings → Developer → Configure Webhook — same
fields either way. The secret is never echoed here; read it
from GET /app/developer/settings (console webhook) or the
create/rotate-secret response (only shown once).

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
    api_instance = splashifypro.WebhooksApi(api_client)
    id = 'id_example' # str | Webhook ID

    try:
        # Get a webhook
        api_response = api_instance.app_webhooks_id_get(id)
        print("The response of WebhooksApi->app_webhooks_id_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling WebhooksApi->app_webhooks_id_get: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| Webhook ID | 

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
**200** | { success, webhook } |  -  |
**404** | Webhook not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_webhooks_id_patch**
> Dict[str, object] app_webhooks_id_patch(id, body=body)

Update a webhook

Sparse update — only url/events/description fields present
in the body are changed. The id and secret never change;
rotate the secret via POST /app/webhooks/{id}/rotate-secret.

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
    api_instance = splashifypro.WebhooksApi(api_client)
    id = 'id_example' # str | Webhook ID
    body = None # object | { url?: string, events?: string[], description?: string } (optional)

    try:
        # Update a webhook
        api_response = api_instance.app_webhooks_id_patch(id, body=body)
        print("The response of WebhooksApi->app_webhooks_id_patch:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling WebhooksApi->app_webhooks_id_patch: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| Webhook ID | 
 **body** | **object**| { url?: string, events?: string[], description?: string } | [optional] 

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
**200** | { success, webhook } |  -  |
**400** | Invalid URL / events |  -  |
**404** | Webhook not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_webhooks_id_rotate_secret_post**
> Dict[str, object] app_webhooks_id_rotate_secret_post(id)

Rotate a webhook's signing secret

Invalidates the old secret immediately — the new one is
shown once in this response. Works on a webhook migrated
from Settings → Developer → Configure Webhook the same way
it works on one created via POST /app/webhooks.

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
    api_instance = splashifypro.WebhooksApi(api_client)
    id = 'id_example' # str | Webhook ID

    try:
        # Rotate a webhook's signing secret
        api_response = api_instance.app_webhooks_id_rotate_secret_post(id)
        print("The response of WebhooksApi->app_webhooks_id_rotate_secret_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling WebhooksApi->app_webhooks_id_rotate_secret_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| Webhook ID | 

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
**200** | { success, message, secret } |  -  |
**404** | Webhook not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_webhooks_id_test_post**
> Dict[str, object] app_webhooks_id_test_post(id)

Send a test event

Fires a signed { event: "test", ... } payload at the
webhook's URL asynchronously — the 200 here only confirms
the request was queued, not that delivery succeeded.

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
    api_instance = splashifypro.WebhooksApi(api_client)
    id = 'id_example' # str | Webhook ID

    try:
        # Send a test event
        api_response = api_instance.app_webhooks_id_test_post(id)
        print("The response of WebhooksApi->app_webhooks_id_test_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling WebhooksApi->app_webhooks_id_test_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| Webhook ID | 

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
**200** | { success, message } |  -  |
**400** | Webhook URL not allowed |  -  |
**404** | Webhook not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **app_webhooks_post**
> Dict[str, object] app_webhooks_post(body)

Register a webhook

Registers a webhook subscribed to the given events. The
response's secret is shown once — every delivery to this URL
is signed with it (see Verifying signatures in the webhooks
guide). A webhook created here and one configured via
Settings → Developer → Configure Webhook are the same kind of
object — GET /app/webhooks lists both, signed the same way.

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
    api_instance = splashifypro.WebhooksApi(api_client)
    body = None # object | { url: string, events: string[], description?: string }

    try:
        # Register a webhook
        api_response = api_instance.app_webhooks_post(body)
        print("The response of WebhooksApi->app_webhooks_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling WebhooksApi->app_webhooks_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| { url: string, events: string[], description?: string } | 

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
**201** | { success, webhook: { id, url, events, secret, ... } } |  -  |
**400** | Invalid URL / events |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

