# splashifypro.RCSApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**public_rcs_check_capability_post**](RCSApi.md#public_rcs_check_capability_post) | **POST** /public/rcs/check-capability | Check RCS reachability
[**public_rcs_send_post**](RCSApi.md#public_rcs_send_post) | **POST** /public/rcs/send | Send an RCS message (free-form or from a stored template)
[**public_rcs_send_template_post**](RCSApi.md#public_rcs_send_template_post) | **POST** /public/rcs/send-template | (Deprecated) Send an approved RCS template — use POST /rcs/send instead


# **public_rcs_check_capability_post**
> Dict[str, object] public_rcs_check_capability_post(body)

Check RCS reachability

Returns the subset of the given phone numbers that are RCS-reachable on JioCX. Accepts a single phone or a bulk list (up to 10,000). Fail-open — if the gateway is momentarily unavailable, the input is returned unchanged so send flows are not blocked.

### Example

* Api Key Authentication (BearerAuth):

```python
import splashifypro
from splashifypro.models.handlers_check_capability_request import HandlersCheckCapabilityRequest
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
    api_instance = splashifypro.RCSApi(api_client)
    body = splashifypro.HandlersCheckCapabilityRequest() # HandlersCheckCapabilityRequest | phone (single, E.164) OR phones (array of E.164)

    try:
        # Check RCS reachability
        api_response = api_instance.public_rcs_check_capability_post(body)
        print("The response of RCSApi->public_rcs_check_capability_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling RCSApi->public_rcs_check_capability_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**HandlersCheckCapabilityRequest**](HandlersCheckCapabilityRequest.md)| phone (single, E.164) OR phones (array of E.164) | 

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
**200** | { success, total, reachable_count, reachable, unreachable } |  -  |
**400** | Missing phone / phones or malformed body |  -  |
**401** | Missing/invalid API key |  -  |
**403** | RCS not enabled for this account |  -  |
**500** | Gateway lookup failed |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_rcs_send_post**
> Dict[str, object] public_rcs_send_post(body)

Send an RCS message (free-form or from a stored template)

Send any RCS message type — text, media, card, multiple_cards — OR reference a stored approved template by template_id with positional variables. Presence of template_id picks the template path.

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
    api_instance = splashifypro.RCSApi(api_client)
    body = None # object | Free-form: { to, type, ... }. Template: { to, template_id, variables? }

    try:
        # Send an RCS message (free-form or from a stored template)
        api_response = api_instance.public_rcs_send_post(body)
        print("The response of RCSApi->public_rcs_send_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling RCSApi->public_rcs_send_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Free-form: { to, type, ... }. Template: { to, template_id, variables? } | 

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
**200** | { success, rcs_message_id, message_id, conversation_id } |  -  |
**400** | Invalid request body |  -  |
**401** | Missing/invalid API key |  -  |
**402** | Insufficient wallet balance |  -  |
**403** | RCS not enabled for this account, or template not approved |  -  |
**404** | Template not found (template_id path only) |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_rcs_send_template_post**
> Dict[str, object] public_rcs_send_template_post(body)

(Deprecated) Send an approved RCS template — use POST /rcs/send instead

Send a stored, approved RCS template. Positional {#varN#} placeholders are filled from the variables array, in order.
Deprecated alias. POST /rcs/send accepts { to, template_id, variables } directly. Kept for backward-compatibility.

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
    api_instance = splashifypro.RCSApi(api_client)
    body = None # object | RCS template payload (to, template_id, variables)

    try:
        # (Deprecated) Send an approved RCS template — use POST /rcs/send instead
        api_response = api_instance.public_rcs_send_template_post(body)
        print("The response of RCSApi->public_rcs_send_template_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling RCSApi->public_rcs_send_template_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| RCS template payload (to, template_id, variables) | 

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
**200** | { success, rcs_message_id, message_id, conversation_id } |  -  |
**400** | Invalid request body |  -  |
**401** | Missing/invalid API key |  -  |
**402** | Insufficient wallet balance |  -  |
**403** | RCS not enabled / template not approved |  -  |
**404** | Template not found |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

