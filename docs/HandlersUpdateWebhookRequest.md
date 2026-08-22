# HandlersUpdateWebhookRequest


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**webhook_events** | **List[str]** |  | [optional] 
**webhook_url** | **str** |  | [optional] 

## Example

```python
from splashifypro.models.handlers_update_webhook_request import HandlersUpdateWebhookRequest

# TODO update the JSON string below
json = "{}"
# create an instance of HandlersUpdateWebhookRequest from a JSON string
handlers_update_webhook_request_instance = HandlersUpdateWebhookRequest.from_json(json)
# print the JSON string representation of the object
print(HandlersUpdateWebhookRequest.to_json())

# convert the object into a dict
handlers_update_webhook_request_dict = handlers_update_webhook_request_instance.to_dict()
# create an instance of HandlersUpdateWebhookRequest from a dict
handlers_update_webhook_request_from_dict = HandlersUpdateWebhookRequest.from_dict(handlers_update_webhook_request_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


