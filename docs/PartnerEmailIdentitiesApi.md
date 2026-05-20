# splashifypro.PartnerEmailIdentitiesApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**partner_email_identities_get**](PartnerEmailIdentitiesApi.md#partner_email_identities_get) | **GET** /partner/email/identities | List sending identities
[**partner_email_identities_post**](PartnerEmailIdentitiesApi.md#partner_email_identities_post) | **POST** /partner/email/identities | Create sending identity
[**partner_email_identities_type_value_verify_post**](PartnerEmailIdentitiesApi.md#partner_email_identities_type_value_verify_post) | **POST** /partner/email/identities/{type}/{value}/verify | Verify identity


# **partner_email_identities_get**
> Dict[str, object] partner_email_identities_get()

List sending identities

Returns every verified or pending sending identity (domains
+ verified email addresses) for the authenticated partner.

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
    api_instance = splashifypro.PartnerEmailIdentitiesApi(api_client)

    try:
        # List sending identities
        api_response = api_instance.partner_email_identities_get()
        print("The response of PartnerEmailIdentitiesApi->partner_email_identities_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailIdentitiesApi->partner_email_identities_get: %s\n" % e)
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
**200** | { success: true, identities: [{type,value,status,...}] } |  -  |
**401** | Missing/invalid API key |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **partner_email_identities_post**
> Dict[str, object] partner_email_identities_post(body)

Create sending identity

Register a new sending identity. For DOMAIN type returns
the SPF + DKIM CNAME + DMARC TXT records to publish; for
EMAIL_ADDRESS type sends a one-time confirmation token.

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
    api_instance = splashifypro.PartnerEmailIdentitiesApi(api_client)
    body = None # object | Create identity payload (identity_type, identity_value)

    try:
        # Create sending identity
        api_response = api_instance.partner_email_identities_post(body)
        print("The response of PartnerEmailIdentitiesApi->partner_email_identities_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailIdentitiesApi->partner_email_identities_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Create identity payload (identity_type, identity_value) | 

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
**200** | { success: true, identity: {...}, dns_records: {...} } |  -  |
**400** | Invalid request |  -  |
**401** | Missing/invalid API key |  -  |
**409** | Identity already exists |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **partner_email_identities_type_value_verify_post**
> Dict[str, object] partner_email_identities_type_value_verify_post(type, value)

Verify identity

Re-runs DNS verification (SPF + DKIM + DMARC checks) on a
domain identity. Triggered after publishing the DNS records
returned from CreateIdentity.

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
    api_instance = splashifypro.PartnerEmailIdentitiesApi(api_client)
    type = 'type_example' # str | DOMAIN or EMAIL_ADDRESS
    value = 'value_example' # str | Domain (yourdomain.com) or email address

    try:
        # Verify identity
        api_response = api_instance.partner_email_identities_type_value_verify_post(type, value)
        print("The response of PartnerEmailIdentitiesApi->partner_email_identities_type_value_verify_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PartnerEmailIdentitiesApi->partner_email_identities_type_value_verify_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **type** | **str**| DOMAIN or EMAIL_ADDRESS | 
 **value** | **str**| Domain (yourdomain.com) or email address | 

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
**200** | { success: true, status, spf, dkim, dmarc } |  -  |
**401** | Missing/invalid API key |  -  |
**404** | Identity not found |  -  |
**429** | Rate-limited (1 verify-now per 60s) |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

