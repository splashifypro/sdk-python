# splashifypro.ConversationsApi

All URIs are relative to *https://apis.splashifypro.com/api/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**app_messages_conversations_conversation_id_assign_post**](ConversationsApi.md#app_messages_conversations_conversation_id_assign_post) | **POST** /app/messages/conversations/{conversation_id}/assign | Assign or release a conversation
[**public_assignment_post**](ConversationsApi.md#public_assignment_post) | **POST** /public/assignment | Assign or release a chat
[**public_teams_get**](ConversationsApi.md#public_teams_get) | **GET** /public/teams | List teams


# **app_messages_conversations_conversation_id_assign_post**
> Dict[str, object] app_messages_conversations_conversation_id_assign_post(conversation_id, body)

Assign or release a conversation

Gives a conversation to a team member, a team or both. Empty assigned_to
releases it (back to its team's queue when it has a team). team_id left out
keeps the team, "" clears it. Fires team_member_assigned, team_member_unassigned or conversation_queued.

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
    body = None # object | { assigned_to: string, team_id?: string, note?: string }

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
 **body** | **object**| { assigned_to: string, team_id?: string, note?: string } | 

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
**200** | { success, assigned_to, assigned_team, team_name, queued } |  -  |
**400** | Invalid conversation_id / body |  -  |
**401** | Unauthorized |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_assignment_post**
> Dict[str, object] public_assignment_post(body)

Assign or release a chat

Routes a conversation to a team member by their email address, to a team
(team_id or team_name: with no agent_email the chat waits in the team's queue),
or both (the person, inside that team). An empty or omitted agent_email with
no team releases it. team_id "" takes the chat out of its team. The
conversation is identified by the customer's phone number. Everything must
belong to the authenticated account.

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
    body = None # object | user_phone_number (required), agent_email, team_id or team_name (all optional)

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
 **body** | **object**| user_phone_number (required), agent_email, team_id or team_name (all optional) | 

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
**200** | { result: true, message, team_id, team_name } |  -  |
**400** | Invalid request / agent, team or phone not found |  -  |
**401** | Missing/invalid API key |  -  |
**409** | Someone else took the chat first (it had nobody on it, and a teammate got it in the meantime) |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **public_teams_get**
> Dict[str, object] public_teams_get()

List teams

The account's teams with their people (id, name, team lead or not). Empty
when the account has no teams. Use a team_id or team_name with
POST /public/assignment.

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

    try:
        # List teams
        api_response = api_instance.public_teams_get()
        print("The response of ConversationsApi->public_teams_get:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling ConversationsApi->public_teams_get: %s\n" % e)
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
**200** | { result: true, teams: [{ team_id, name, color, members: [{ member_id, name, email, is_lead }] }] } |  -  |
**401** | Missing/invalid API key |  -  |
**429** | Rate limit exceeded |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

