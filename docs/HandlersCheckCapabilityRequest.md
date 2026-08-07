# HandlersCheckCapabilityRequest


## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**bot_id** | **str** |  | [optional] 
**phone** | **str** |  | [optional] 
**phones** | **List[str]** |  | [optional] 

## Example

```python
from splashifypro.models.handlers_check_capability_request import HandlersCheckCapabilityRequest

# TODO update the JSON string below
json = "{}"
# create an instance of HandlersCheckCapabilityRequest from a JSON string
handlers_check_capability_request_instance = HandlersCheckCapabilityRequest.from_json(json)
# print the JSON string representation of the object
print(HandlersCheckCapabilityRequest.to_json())

# convert the object into a dict
handlers_check_capability_request_dict = handlers_check_capability_request_instance.to_dict()
# create an instance of HandlersCheckCapabilityRequest from a dict
handlers_check_capability_request_from_dict = HandlersCheckCapabilityRequest.from_dict(handlers_check_capability_request_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


