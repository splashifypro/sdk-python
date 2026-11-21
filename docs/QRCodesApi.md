# splashifypro.QRCodesApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**public_qr_codes_get**](QRCodesApi.md#public_qr_codes_get) | **GET** /public/qr-codes | List QR codes
[**public_qr_codes_id_delete**](QRCodesApi.md#public_qr_codes_id_delete) | **DELETE** /public/qr-codes/{id} | Delete a QR code
[**public_qr_codes_id_patch**](QRCodesApi.md#public_qr_codes_id_patch) | **PATCH** /public/qr-codes/{id} | Update a QR code
[**public_qr_codes_post**](QRCodesApi.md#public_qr_codes_post) | **POST** /public/qr-codes | Create a QR code


# **public_qr_codes_get**
> Dict[str, object] public_qr_codes_get()

List QR codes

Every WhatsApp QR code on the account with its link, scans and chats in the last 7 and 30 days, plus daily scans for 30 days.

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
    api_instance = splashifypro.QRCodesApi(api_client)

    try:
        # List QR codes
        api_response = api_instance.public_qr_codes_get()
        print("The response of QRCodesApi->public_qr_codes_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling QRCodesApi->public_qr_codes_get: %s\n" % e)
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
**200** | { success, links[{ id, name, prefill, slug, url, scans_7d, scans_30d, chats_7d, chats_30d, created_at }], daily, tracking_available, base_url, phone } |  -  |
**401** | Missing or invalid API key |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_qr_codes_id_delete**
> Dict[str, object] public_qr_codes_id_delete(id)

Delete a QR code

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
    api_instance = splashifypro.QRCodesApi(api_client)
    id = 'id_example' # str | QR code id

    try:
        # Delete a QR code
        api_response = api_instance.public_qr_codes_id_delete(id)
        print("The response of QRCodesApi->public_qr_codes_id_delete:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling QRCodesApi->public_qr_codes_id_delete: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| QR code id | 

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
**200** | { success } |  -  |
**401** | Missing or invalid API key |  -  |
**404** | QR code not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_qr_codes_id_patch**
> Dict[str, object] public_qr_codes_id_patch(id, body)

Update a QR code

Changes the name or the prefilled message. The link and the printed QR code stay the same.

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
    api_instance = splashifypro.QRCodesApi(api_client)
    id = 'id_example' # str | QR code id
    body = None # object | { name?, prefill? }

    try:
        # Update a QR code
        api_response = api_instance.public_qr_codes_id_patch(id, body)
        print("The response of QRCodesApi->public_qr_codes_id_patch:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling QRCodesApi->public_qr_codes_id_patch: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **id** | **str**| QR code id | 
 **body** | **object**| { name?, prefill? } | 

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
**200** | { success, link } |  -  |
**400** | Invalid id or nothing to change |  -  |
**401** | Missing or invalid API key |  -  |
**404** | QR code not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_qr_codes_post**
> Dict[str, object] public_qr_codes_post(body)

Create a QR code

Creates a tracked WhatsApp link and QR code. prefill is the message the customer's chat opens with (up to 500 characters). Up to 200 QR codes per account.

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
    api_instance = splashifypro.QRCodesApi(api_client)
    body = None # object | { name, prefill? }

    try:
        # Create a QR code
        api_response = api_instance.public_qr_codes_post(body)
        print("The response of QRCodesApi->public_qr_codes_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling QRCodesApi->public_qr_codes_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| { name, prefill? } | 

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
**201** | { success, link } |  -  |
**400** | Name missing or too long |  -  |
**401** | Missing or invalid API key |  -  |
**403** | QR codes with counts are not available on this account |  -  |
**409** | WhatsApp number not connected, or 200 QR codes already |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

