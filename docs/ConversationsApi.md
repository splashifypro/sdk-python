# splashifypro.ConversationsApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**app_messages_conversations_conversation_id_assign_post**](ConversationsApi.md#app_messages_conversations_conversation_id_assign_post) | **POST** /app/messages/conversations/{conversation_id}/assign | Assign or release a conversation
[**public_assignment_post**](ConversationsApi.md#public_assignment_post) | **POST** /public/assignment | Assign or release a chat


# **app_messages_conversations_conversation_id_assign_post**
> Dict[str, object] app_messages_conversations_conversation_id_assign_post(conversation_id, body)

Assign or release a conversation

Assigns a conversation to a team member, or releases it when
assigned_to is empty — fires team_member_assigned or
team_member_unassigned respectively.

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
    api_instance = splashifypro.ConversationsApi(api_client)
    conversation_id = 'conversation_id_example' # str | Conversation ID
    body = None # object | { assigned_to: string }, empty string releases

    try:
        # Assign or release a conversation
        api_response = api_instance.app_messages_conversations_conversation_id_assign_post(conversation_id, body)
        print("The response of ConversationsApi->app_messages_conversations_conversation_id_assign_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ConversationsApi->app_messages_conversations_conversation_id_assign_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **conversation_id** | **str**| Conversation ID | 
 **body** | **object**| { assigned_to: string }, empty string releases | 

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
**200** | { success: true, assigned_to: string } |  -  |
**400** | Invalid conversation_id / body |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_assignment_post**
> Dict[str, object] public_assignment_post(body)

Assign or release a chat

Routes a conversation to a specific team member by their
email address, or releases it when agent_email is empty or
omitted. Conversation is identified by the customer's phone
number. Both agent and conversation must belong to the
authenticated account.

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
    api_instance = splashifypro.ConversationsApi(api_client)
    body = None # object | Assignment payload: user_phone_number (required), agent_email (empty/omitted releases)

    try:
        # Assign or release a chat
        api_response = api_instance.public_assignment_post(body)
        print("The response of ConversationsApi->public_assignment_post:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ConversationsApi->public_assignment_post: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | **object**| Assignment payload: user_phone_number (required), agent_email (empty/omitted releases) | 

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
**200** | { result: true, message: &#39;Chat Assigned Successfully&#39; } |  -  |
**400** | Invalid request / agent or phone not found |  -  |
**401** | Missing/invalid API key |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

