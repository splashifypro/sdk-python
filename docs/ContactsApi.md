# splashifypro.ContactsApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**public_apis_users_post**](ContactsApi.md#public_apis_users_post) | **POST** /public/apis/users | List contacts (paginated, filterable)
[**public_contacts_delete_post**](ContactsApi.md#public_contacts_delete_post) | **POST** /public/contacts/delete | Delete a contact
[**public_contacts_notes_post**](ContactsApi.md#public_contacts_notes_post) | **POST** /public/contacts/notes | Add a note to a contact
[**public_contacts_post**](ContactsApi.md#public_contacts_post) | **POST** /public/contacts | Create a contact
[**public_contacts_tags_post**](ContactsApi.md#public_contacts_tags_post) | **POST** /public/contacts/tags | Assign tags to a contact
[**public_contacts_tags_remove_post**](ContactsApi.md#public_contacts_tags_remove_post) | **POST** /public/contacts/tags/remove | Remove tags from a contact


# **public_apis_users_post**
> Dict[str, object] public_apis_users_post(offset=offset, limit=limit, body=body)

List contacts (paginated, filterable)

Returns a paginated list of contacts (customers) for the
authenticated account. Filters are applied in-memory and
support traits: created_at_utc, modified_at_utc, phone_number,
name, email, whatsapp_opted_in, plus any custom column from
the contact's column_data.

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
    api_instance = splashifypro.ContactsApi(api_client)
    offset = 56 # int | Pagination offset (default 0) (optional)
    limit = 56 # int | Page size (default 100, max 500) (optional)
    body = None # object | Optional filter object: {filters:[{trait,op,val}]} (optional)

    try:
        # List contacts (paginated, filterable)
        api_response = api_instance.public_apis_users_post(offset=offset, limit=limit, body=body)
        print("The response of ContactsApi->public_apis_users_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ContactsApi->public_apis_users_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **offset** | **int**| Pagination offset (default 0) | [optional] 
 **limit** | **int**| Page size (default 100, max 500) | [optional] 
 **body** | **object**| Optional filter object: {filters:[{trait,op,val}]} | [optional] 

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
**200** | { result: true, data: { customers: [...], total_customers, has_next_page } } |  -  |
**401** | Missing/invalid API key |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_contacts_delete_post**
> Dict[str, object] public_contacts_delete_post(body)

Delete a contact

Permanently delete a contact and its conversation history.

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
    api_instance = splashifypro.ContactsApi(api_client)
    body = None # object | { phone_number | contact_id }

    try:
        # Delete a contact
        api_response = api_instance.public_contacts_delete_post(body)
        print("The response of ContactsApi->public_contacts_delete_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ContactsApi->public_contacts_delete_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| { phone_number | contact_id } | 

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
**200** | { result: true } |  -  |
**404** | Contact not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_contacts_notes_post**
> Dict[str, object] public_contacts_notes_post(body)

Add a note to a contact

Append (default) or replace the free-text notes on a contact.

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
    api_instance = splashifypro.ContactsApi(api_client)
    body = None # object | { phone_number | contact_id, note, append }

    try:
        # Add a note to a contact
        api_response = api_instance.public_contacts_notes_post(body)
        print("The response of ContactsApi->public_contacts_notes_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ContactsApi->public_contacts_notes_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| { phone_number | contact_id, note, append } | 

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
**200** | { result: true, notes: &#39;…&#39; } |  -  |
**404** | Contact not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_contacts_post**
> Dict[str, object] public_contacts_post(body)

Create a contact

Add a new contact to your Splashify workspace.

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
    api_instance = splashifypro.ContactsApi(api_client)
    body = None # object | Contact payload (phone_number, display_name, …)

    try:
        # Create a contact
        api_response = api_instance.public_contacts_post(body)
        print("The response of ContactsApi->public_contacts_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ContactsApi->public_contacts_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Contact payload (phone_number, display_name, …) | 

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
**201** | { result: true, contact: {…} } |  -  |
**400** | Invalid request body |  -  |
**409** | Contact already exists |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_contacts_tags_post**
> Dict[str, object] public_contacts_tags_post(body)

Assign tags to a contact

Add one or more tags to a contact. Existing tags are preserved.

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
    api_instance = splashifypro.ContactsApi(api_client)
    body = None # object | { phone_number | contact_id, tags: [] }

    try:
        # Assign tags to a contact
        api_response = api_instance.public_contacts_tags_post(body)
        print("The response of ContactsApi->public_contacts_tags_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ContactsApi->public_contacts_tags_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| { phone_number | contact_id, tags: [] } | 

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
**200** | { result: true, tags: [] } |  -  |
**404** | Contact not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_contacts_tags_remove_post**
> Dict[str, object] public_contacts_tags_remove_post(body)

Remove tags from a contact

Remove one or more tags from a contact.

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
    api_instance = splashifypro.ContactsApi(api_client)
    body = None # object | { phone_number | contact_id, tags: [] }

    try:
        # Remove tags from a contact
        api_response = api_instance.public_contacts_tags_remove_post(body)
        print("The response of ContactsApi->public_contacts_tags_remove_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ContactsApi->public_contacts_tags_remove_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| { phone_number | contact_id, tags: [] } | 

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
**200** | { result: true, tags: [] } |  -  |
**404** | Contact not found |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

