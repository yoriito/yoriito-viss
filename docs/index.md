# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [yoriito/viss/v1/consumer.proto](#yoriito_viss_v1_consumer-proto)
    - [GetCurrentRequest](#yoriito-viss-v1-consumer-GetCurrentRequest)
    - [GetCurrentResponse](#yoriito-viss-v1-consumer-GetCurrentResponse)
    - [SetTargetRequest](#yoriito-viss-v1-consumer-SetTargetRequest)
    - [SetTargetResponse](#yoriito-viss-v1-consumer-SetTargetResponse)
    - [SubscribeCurrentRequest](#yoriito-viss-v1-consumer-SubscribeCurrentRequest)
    - [SubscribeCurrentResponse](#yoriito-viss-v1-consumer-SubscribeCurrentResponse)
    - [SubscriptionCurrentEvent](#yoriito-viss-v1-consumer-SubscriptionCurrentEvent)
  
    - [VISS](#yoriito-viss-v1-consumer-VISS)
  
- [yoriito/viss/v1/producer.proto](#yoriito_viss_v1_producer-proto)
    - [DefineRequest](#yoriito-viss-v1-producer-DefineRequest)
    - [DefineResponse](#yoriito-viss-v1-producer-DefineResponse)
    - [DeleteRequest](#yoriito-viss-v1-producer-DeleteRequest)
    - [DeleteResponse](#yoriito-viss-v1-producer-DeleteResponse)
    - [GetTargetRequest](#yoriito-viss-v1-producer-GetTargetRequest)
    - [GetTargetResponse](#yoriito-viss-v1-producer-GetTargetResponse)
    - [SetCurrentRequest](#yoriito-viss-v1-producer-SetCurrentRequest)
    - [SetCurrentResponse](#yoriito-viss-v1-producer-SetCurrentResponse)
    - [SubscribeTargetRequest](#yoriito-viss-v1-producer-SubscribeTargetRequest)
    - [SubscribeTargetResponse](#yoriito-viss-v1-producer-SubscribeTargetResponse)
    - [SubscriptionTargetEvent](#yoriito-viss-v1-producer-SubscriptionTargetEvent)
  
    - [VISS](#yoriito-viss-v1-producer-VISS)
  
- [yoriito/viss/v1/common.proto](#yoriito_viss_v1_common-proto)
    - [InspectRequest](#yoriito-viss-v1-InspectRequest)
    - [InspectResponse](#yoriito-viss-v1-InspectResponse)
    - [SubscribeError](#yoriito-viss-v1-SubscribeError)
    - [SubscribeSuccess](#yoriito-viss-v1-SubscribeSuccess)
    - [UnsubscribeRequest](#yoriito-viss-v1-UnsubscribeRequest)
    - [UnsubscribeResponse](#yoriito-viss-v1-UnsubscribeResponse)
  
- [yoriito/viss/v1/types/error.proto](#yoriito_viss_v1_types_error-proto)
    - [Error](#yoriito-viss-v1-Error)
  
    - [ErrorCode](#yoriito-viss-v1-ErrorCode)
    - [ErrorReason](#yoriito-viss-v1-ErrorReason)
  
- [yoriito/viss/v1/types/filter.proto](#yoriito_viss_v1_types_filter-proto)
    - [ChangeFilter](#yoriito-viss-v1-ChangeFilter)
    - [ComboFilter](#yoriito-viss-v1-ComboFilter)
    - [CurvelogFilter](#yoriito-viss-v1-CurvelogFilter)
    - [DefineFilter](#yoriito-viss-v1-DefineFilter)
    - [GetFilter](#yoriito-viss-v1-GetFilter)
    - [HistoryFilter](#yoriito-viss-v1-HistoryFilter)
    - [InspectFilter](#yoriito-viss-v1-InspectFilter)
    - [MiscFilter](#yoriito-viss-v1-MiscFilter)
    - [PathsFilter](#yoriito-viss-v1-PathsFilter)
    - [RangeCondition](#yoriito-viss-v1-RangeCondition)
    - [RangeConditionArray](#yoriito-viss-v1-RangeConditionArray)
    - [RangeConditionWithOp](#yoriito-viss-v1-RangeConditionWithOp)
    - [RangeFilter](#yoriito-viss-v1-RangeFilter)
    - [SubscribeFilter](#yoriito-viss-v1-SubscribeFilter)
    - [TimebasedFilter](#yoriito-viss-v1-TimebasedFilter)
  
    - [Condition](#yoriito-viss-v1-Condition)
    - [Operator](#yoriito-viss-v1-Operator)
  
- [yoriito/viss/v1/types/value.proto](#yoriito_viss_v1_types_value-proto)
    - [BoolArray](#yoriito-viss-v1-BoolArray)
    - [DataPackageCurrent](#yoriito-viss-v1-DataPackageCurrent)
    - [DataPackageTarget](#yoriito-viss-v1-DataPackageTarget)
    - [DataPackagesCurrent](#yoriito-viss-v1-DataPackagesCurrent)
    - [DataPackagesTarget](#yoriito-viss-v1-DataPackagesTarget)
    - [DataPointCurrent](#yoriito-viss-v1-DataPointCurrent)
    - [DataPointTarget](#yoriito-viss-v1-DataPointTarget)
    - [DoubleArray](#yoriito-viss-v1-DoubleArray)
    - [FloatArray](#yoriito-viss-v1-FloatArray)
    - [Int16Array](#yoriito-viss-v1-Int16Array)
    - [Int32Array](#yoriito-viss-v1-Int32Array)
    - [Int64Array](#yoriito-viss-v1-Int64Array)
    - [Int8Array](#yoriito-viss-v1-Int8Array)
    - [MetadataEntries](#yoriito-viss-v1-MetadataEntries)
    - [MetadataEntry](#yoriito-viss-v1-MetadataEntry)
    - [StringArray](#yoriito-viss-v1-StringArray)
    - [Uint16Array](#yoriito-viss-v1-Uint16Array)
    - [Uint32Array](#yoriito-viss-v1-Uint32Array)
    - [Uint64Array](#yoriito-viss-v1-Uint64Array)
    - [Uint8Array](#yoriito-viss-v1-Uint8Array)
    - [ValueObject](#yoriito-viss-v1-ValueObject)
    - [ValueProperty](#yoriito-viss-v1-ValueProperty)
    - [ValueType](#yoriito-viss-v1-ValueType)
  
    - [DataType](#yoriito-viss-v1-DataType)
    - [NodeType](#yoriito-viss-v1-NodeType)
  
- [Scalar Value Types](#scalar-value-types)



<a name="yoriito_viss_v1_consumer-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## yoriito/viss/v1/consumer.proto



<a name="yoriito-viss-v1-consumer-GetCurrentRequest"></a>

### GetCurrentRequest
GetCurrentRequest represents a request to get current sensor data


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| path | [string](#string) |  | The path of the node to get data from |
| filter | [yoriito.viss.v1.GetFilter](#yoriito-viss-v1-GetFilter) | optional | Optional filter to apply to the data retrieval |






<a name="yoriito-viss-v1-consumer-GetCurrentResponse"></a>

### GetCurrentResponse
GetCurrentResponse represents the response to a GetCurrentRequest


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ts | [int64](#int64) |  | Timestamp of the server response |
| data | [yoriito.viss.v1.DataPackagesCurrent](#yoriito-viss-v1-DataPackagesCurrent) |  | data contains the current sensor data |
| error | [yoriito.viss.v1.Error](#yoriito-viss-v1-Error) |  | error contains any error that occurred on the server |






<a name="yoriito-viss-v1-consumer-SetTargetRequest"></a>

### SetTargetRequest
SetTargetRequest represents a request to set target values for actuators


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| data | [yoriito.viss.v1.DataPackagesTarget](#yoriito-viss-v1-DataPackagesTarget) |  | The target data to set for the actuators |






<a name="yoriito-viss-v1-consumer-SetTargetResponse"></a>

### SetTargetResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ts | [int64](#int64) |  | Timestamp of the server response |
| success | [google.protobuf.Empty](#google-protobuf-Empty) |  | success indicates the target values were accepted by the server |
| error | [yoriito.viss.v1.Error](#yoriito-viss-v1-Error) |  | error contains any error that occurred on the server |






<a name="yoriito-viss-v1-consumer-SubscribeCurrentRequest"></a>

### SubscribeCurrentRequest
SubscribeCurrentRequest represents a request to subscribe to current sensor data


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| path | [string](#string) |  | The path of the node to subscribe to |
| filter | [yoriito.viss.v1.SubscribeFilter](#yoriito-viss-v1-SubscribeFilter) |  | Optional filter to apply to the subscription |






<a name="yoriito-viss-v1-consumer-SubscribeCurrentResponse"></a>

### SubscribeCurrentResponse
SubscribeCurrentResponse represents the response to a SubscribeCurrentRequest


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ts | [int64](#int64) |  | Timestamp of the server response |
| success | [yoriito.viss.v1.SubscribeSuccess](#yoriito-viss-v1-SubscribeSuccess) |  | success indicates the subscription was successful |
| error | [yoriito.viss.v1.SubscribeError](#yoriito-viss-v1-SubscribeError) |  | error contains any error that occurred on the server |
| event | [SubscriptionCurrentEvent](#yoriito-viss-v1-consumer-SubscriptionCurrentEvent) |  | event contains data updates for the subscription |






<a name="yoriito-viss-v1-consumer-SubscriptionCurrentEvent"></a>

### SubscriptionCurrentEvent
SubscriptionEvent represents an event in a subscription


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| subscription_id | [string](#string) |  | The ID of the subscription that this event belongs to |
| data | [yoriito.viss.v1.DataPackagesCurrent](#yoriito-viss-v1-DataPackagesCurrent) |  | The current data for the subscription |





 

 

 


<a name="yoriito-viss-v1-consumer-VISS"></a>

### VISS
gRPC Service Definition

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| GetCurrent | [GetCurrentRequest](#yoriito-viss-v1-consumer-GetCurrentRequest) | [GetCurrentResponse](#yoriito-viss-v1-consumer-GetCurrentResponse) | action to get current sensor data |
| Inspect | [.yoriito.viss.v1.InspectRequest](#yoriito-viss-v1-InspectRequest) | [.yoriito.viss.v1.InspectResponse](#yoriito-viss-v1-InspectResponse) | action to get metadata of a node |
| SetTarget | [SetTargetRequest](#yoriito-viss-v1-consumer-SetTargetRequest) | [SetTargetResponse](#yoriito-viss-v1-consumer-SetTargetResponse) | action to set target value to actuator |
| SubscribeCurrent | [SubscribeCurrentRequest](#yoriito-viss-v1-consumer-SubscribeCurrentRequest) | [SubscribeCurrentResponse](#yoriito-viss-v1-consumer-SubscribeCurrentResponse) stream | action to subscribe current sensor data |
| Unsubscribe | [.yoriito.viss.v1.UnsubscribeRequest](#yoriito-viss-v1-UnsubscribeRequest) | [.yoriito.viss.v1.UnsubscribeResponse](#yoriito-viss-v1-UnsubscribeResponse) | action to unsubscribe current sensor data |

 



<a name="yoriito_viss_v1_producer-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## yoriito/viss/v1/producer.proto



<a name="yoriito-viss-v1-producer-DefineRequest"></a>

### DefineRequest
DefineRequest represents a request to define VSS nodes


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| entries | [yoriito.viss.v1.MetadataEntries](#yoriito-viss-v1-MetadataEntries) |  | The set of the path and metada entries to define |






<a name="yoriito-viss-v1-producer-DefineResponse"></a>

### DefineResponse
DefineResponse represents the response to a DefineRequest


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ts | [int64](#int64) |  | Timestamp of the server response |
| success | [google.protobuf.Empty](#google-protobuf-Empty) |  | success indicates that the VSS nodes were defined successfully |
| error | [yoriito.viss.v1.Error](#yoriito-viss-v1-Error) |  | error contains any error that occurred on the server |






<a name="yoriito-viss-v1-producer-DeleteRequest"></a>

### DeleteRequest
DeleteRequest represents a request to delete VSS nodes


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| path | [string](#string) | repeated | The path of the node to delete If a node which does not exist is specified, it is ignored. |






<a name="yoriito-viss-v1-producer-DeleteResponse"></a>

### DeleteResponse
DeleteResponse represents the response to a DeleteRequest


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ts | [int64](#int64) |  | Timestamp of the server response |
| success | [google.protobuf.Empty](#google-protobuf-Empty) |  | success indicates that the VSS nodes were deleted successfully |
| error | [yoriito.viss.v1.Error](#yoriito-viss-v1-Error) |  | error contains any error that occurred on the server |






<a name="yoriito-viss-v1-producer-GetTargetRequest"></a>

### GetTargetRequest
GetTargetRequest represents a request to get target values for actuators


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| path | [string](#string) |  | The path of the node to get target values from |
| filter | [yoriito.viss.v1.GetFilter](#yoriito-viss-v1-GetFilter) | optional | Optional filter to apply to the data retrieval |






<a name="yoriito-viss-v1-producer-GetTargetResponse"></a>

### GetTargetResponse
GetTargetResponse represents the response to a GetTargetRequest


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ts | [int64](#int64) |  | Timestamp of the server response |
| data | [yoriito.viss.v1.DataPackagesTarget](#yoriito-viss-v1-DataPackagesTarget) |  | data contains the target values for the actuators |
| error | [yoriito.viss.v1.Error](#yoriito-viss-v1-Error) |  | error contains any error that occurred on the server |






<a name="yoriito-viss-v1-producer-SetCurrentRequest"></a>

### SetCurrentRequest
SetCurrentRequest represents a request to set current values for sensors


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| data | [yoriito.viss.v1.DataPackagesCurrent](#yoriito-viss-v1-DataPackagesCurrent) |  | The current data to set for the sensors |






<a name="yoriito-viss-v1-producer-SetCurrentResponse"></a>

### SetCurrentResponse
SetCurrentResponse represents the response to a SetCurrentRequest


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ts | [int64](#int64) |  | Timestamp of the server response |
| success | [google.protobuf.Empty](#google-protobuf-Empty) |  | success indicates that the current values were set successfully |
| error | [yoriito.viss.v1.Error](#yoriito-viss-v1-Error) |  | error contains any error that occurred on the server |






<a name="yoriito-viss-v1-producer-SubscribeTargetRequest"></a>

### SubscribeTargetRequest
SubscribeTargetRequest represents a request to subscribe to target value changes of an actuator


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| path | [string](#string) |  | The path of the node to subscribe to |
| filter | [yoriito.viss.v1.SubscribeFilter](#yoriito-viss-v1-SubscribeFilter) |  | Optional filter to apply to the subscription |






<a name="yoriito-viss-v1-producer-SubscribeTargetResponse"></a>

### SubscribeTargetResponse
SubscribeTargetResponse represents the response to a SubscribeTargetRequest


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ts | [int64](#int64) |  | Timestamp of the server response |
| success | [yoriito.viss.v1.SubscribeSuccess](#yoriito-viss-v1-SubscribeSuccess) |  | success indicates the subscription was successful |
| error | [yoriito.viss.v1.SubscribeError](#yoriito-viss-v1-SubscribeError) |  | error contains any error that occurred on the server |
| event | [SubscriptionTargetEvent](#yoriito-viss-v1-producer-SubscriptionTargetEvent) |  | event contains data updates for the subscription |






<a name="yoriito-viss-v1-producer-SubscriptionTargetEvent"></a>

### SubscriptionTargetEvent
SubscribeSuccess represents an event in a subscription


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| subscription_id | [string](#string) |  | The ID of the subscription that this event belongs to |
| data | [yoriito.viss.v1.DataPackagesTarget](#yoriito-viss-v1-DataPackagesTarget) |  | The target data for the subscription |





 

 

 


<a name="yoriito-viss-v1-producer-VISS"></a>

### VISS
gRPC Service Definition

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| GetTarget | [GetTargetRequest](#yoriito-viss-v1-producer-GetTargetRequest) | [GetTargetResponse](#yoriito-viss-v1-producer-GetTargetResponse) | action to get target value of an actuator |
| SetCurrent | [SetCurrentRequest](#yoriito-viss-v1-producer-SetCurrentRequest) | [SetCurrentResponse](#yoriito-viss-v1-producer-SetCurrentResponse) | action to set current value of a sensor |
| Inspect | [.yoriito.viss.v1.InspectRequest](#yoriito-viss-v1-InspectRequest) | [.yoriito.viss.v1.InspectResponse](#yoriito-viss-v1-InspectResponse) | action to get metadata of a node |
| Define | [DefineRequest](#yoriito-viss-v1-producer-DefineRequest) | [DefineResponse](#yoriito-viss-v1-producer-DefineResponse) | action to define VSS nodes. See [here](Define_Delete.md). |
| Delete | [DeleteRequest](#yoriito-viss-v1-producer-DeleteRequest) | [DeleteResponse](#yoriito-viss-v1-producer-DeleteResponse) | action to delete VSS nodes. See [here](Define_Delete.md). |
| SubscribeTarget | [SubscribeTargetRequest](#yoriito-viss-v1-producer-SubscribeTargetRequest) | [SubscribeTargetResponse](#yoriito-viss-v1-producer-SubscribeTargetResponse) stream | action to subscribe to target value changes of an actuator |
| Unsubscribe | [.yoriito.viss.v1.UnsubscribeRequest](#yoriito-viss-v1-UnsubscribeRequest) | [.yoriito.viss.v1.UnsubscribeResponse](#yoriito-viss-v1-UnsubscribeResponse) | action to unsubscribe from target value changes |

 



<a name="yoriito_viss_v1_common-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## yoriito/viss/v1/common.proto



<a name="yoriito-viss-v1-InspectRequest"></a>

### InspectRequest
InspectRequest represents a request to get metadata of a node


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| path | [string](#string) |  | The path of the node to inspect |
| filter | [InspectFilter](#yoriito-viss-v1-InspectFilter) | optional | Optional filter to apply to the inspection |






<a name="yoriito-viss-v1-InspectResponse"></a>

### InspectResponse
InspectResponse represents the response to an InspectRequest


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ts | [int64](#int64) |  | Timestamp of the server response |
| metadata | [MetadataEntries](#yoriito-viss-v1-MetadataEntries) |  | metadata contains the metadata of the node |
| error | [Error](#yoriito-viss-v1-Error) |  | error contains any error that occurred on the server |






<a name="yoriito-viss-v1-SubscribeError"></a>

### SubscribeError
SubscribeError represents an error response for a subscription request


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| error | [Error](#yoriito-viss-v1-Error) |  | Error contains any error that occurred on the server |






<a name="yoriito-viss-v1-SubscribeSuccess"></a>

### SubscribeSuccess
SubscribeSuccess represents a successful subscription response


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| subscription_id | [string](#string) |  | The ID of the subscription |






<a name="yoriito-viss-v1-UnsubscribeRequest"></a>

### UnsubscribeRequest
UnsubscribeRequest represents a request to unsubscribe from a subscription


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| subscription_id | [string](#string) |  | The ID of the subscription to unsubscribe from |






<a name="yoriito-viss-v1-UnsubscribeResponse"></a>

### UnsubscribeResponse
UnsubscribeResponse represents the response to an UnsubscribeRequest


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ts | [int64](#int64) |  | Timestamp of the server response |
| success | [google.protobuf.Empty](#google-protobuf-Empty) |  | success indicates that the unsubscription was successful |
| error | [Error](#yoriito-viss-v1-Error) |  | error contains any error that occurred on the server |





 

 

 

 



<a name="yoriito_viss_v1_types_error-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## yoriito/viss/v1/types/error.proto



<a name="yoriito-viss-v1-Error"></a>

### Error
Error represents an error response in VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| number | [ErrorCode](#yoriito-viss-v1-ErrorCode) |  | ErrorCode represents the error code |
| reason | [ErrorReason](#yoriito-viss-v1-ErrorReason) |  | ErrorReason represents the reason for the error |
| description | [string](#string) | optional | Description provides a human-readable description of the error |





 


<a name="yoriito-viss-v1-ErrorCode"></a>

### ErrorCode
ErrorCode represents the error codes used in VISS

| Name | Number | Description |
| ---- | ------ | ----------- |
| ERROR_UNSPECIFIED | 0 | Unspecified error code |
| ERROR_BAD_REQUEST | 400 | error when the request is invalid or malformed |
| ERROR_UNAUTHORIZED | 401 | error when the request is unauthorized |
| ERROR_FORBIDDEN | 403 | error when the request is forbidden |
| ERROR_NOT_FOUND | 404 | error when the requested node is not found |
| ERROR_REQUEST_TIMEOUT | 408 | error when the request is not acceptable |
| ERROR_TOO_MANY_REQUESTS | 429 | error when the server is overloaded or too many requests are made |
| ERROR_INTERNAL_SERVER_ERROR | 500 | error when the server encountered an internal error |
| ERROR_BAD_GATEWAY | 502 | error when the server received an invalid response from an upstream server |
| ERROR_SERVICE_UNAVAILABLE | 503 | error when the server is currently unavailable |
| ERROR_GATEWAY_TIMEOUT | 504 | error when the server did not receive a timely response from an upstream server |



<a name="yoriito-viss-v1-ErrorReason"></a>

### ErrorReason
ErrorReason represents the reasons for errors in VISS

| Name | Number | Description |
| ---- | ------ | ----------- |
| REASON_UNSPECIFIED | 0 | Unspecified reason for the error |
| REASON_BAD_REQUEST | 1 | Bad request, typically due to malformed request syntax |
| REASON_INVALID_DATA | 2 | Invalid data provided in the request |
| REASON_INVALID_TOKEN | 3 | Invalid token, such as an expired or malformed request id |
| REASON_FORBIDDEN_REQUEST | 4 | Forbidden request, such as when the user does not have permission to access the resource |
| REASON_UNAVAILABLE_DATA | 5 | Unavailable data, such as when the requested data is not available or cannot be retrieved |
| REASON_REQUEST_TIMEOUT | 6 | Request timeout, such as when the server did not receive a response in time |
| REASON_TOO_MANY_REQUESTS | 7 | Too many requests, such as when the server is overloaded or too many requests are made in a short period |
| REASON_INTERNAL_SERVER_ERROR | 8 | Internal server error, such as when the server encountered an unexpected condition |
| REASON_BAD_GATEWAY | 9 | Bad gateway, such as when the server encountered an error while communicating with an upstream server |
| REASON_SERVICE_UNAVAILABLE | 10 | Service unavailable, such as when the server is currently unavailable or undergoing maintenance |
| REASON_GATEWAY_TIMEOUT | 11 | Gateway timeout, such as when the server did not receive a timely response from an upstream server |


 

 

 



<a name="yoriito_viss_v1_types_filter-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## yoriito/viss/v1/types/filter.proto



<a name="yoriito-viss-v1-ChangeFilter"></a>

### ChangeFilter
ChangeFilter can be applied to number or boolean datatype


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| logic_op | [Operator](#yoriito-viss-v1-Operator) |  | logic_op defines the logical operator for the change filter |
| diff | [sint32](#sint32) |  | diff defines the difference value for the change filter |






<a name="yoriito-viss-v1-ComboFilter"></a>

### ComboFilter
ComboFilter represents a combination of PathsFilter and MiscFilter


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| paths_parameter | [PathsFilter](#yoriito-viss-v1-PathsFilter) |  | PathsFilter is used to retrieve multiple nodes |
| misc_parameter | [MiscFilter](#yoriito-viss-v1-MiscFilter) |  | MiscFilter is used to apply additional parameters to PathsFilter |






<a name="yoriito-viss-v1-CurvelogFilter"></a>

### CurvelogFilter
CurvelogFilter is used to retrieve data with a curve log


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| maxerr | [float](#float) |  | maxerr is a float value setting the max allowed error between any data sample and the simplified curve. |
| bufsize | [uint32](#uint32) |  | bufsize is the number of buffer elements. |






<a name="yoriito-viss-v1-DefineFilter"></a>

### DefineFilter
DefineFilter represents a filter for the Define action


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| paths_parameter | [PathsFilter](#yoriito-viss-v1-PathsFilter) |  | PathsFilter is used to retrieve multiple nodes |






<a name="yoriito-viss-v1-GetFilter"></a>

### GetFilter
GetFilter represents a filter for the Get action


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| paths_parameter | [PathsFilter](#yoriito-viss-v1-PathsFilter) |  | PathsFilter is used to retrieve multiple nodes |
| history_parameter | [HistoryFilter](#yoriito-viss-v1-HistoryFilter) |  | HistoryFilter is used to retrieve historical data (Currently Not Supported) |






<a name="yoriito-viss-v1-HistoryFilter"></a>

### HistoryFilter
HistoryFilter is used to retrieve historical data


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| timePeriod | [string](#string) |  | The period must conform to the ISO8601 duration format, expressed with days, hour, minute, and second data i.e. &#34;PdddMThhHmmMssS&#34; |






<a name="yoriito-viss-v1-InspectFilter"></a>

### InspectFilter
InspectFilter represents a filter for the Inspect action


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| paths_parameter | [PathsFilter](#yoriito-viss-v1-PathsFilter) |  | PathsFilter is used to retrieve multiple nodes |






<a name="yoriito-viss-v1-MiscFilter"></a>

### MiscFilter
MiscFilter represents a miscellaneous filter


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| timebased_parameter | [TimebasedFilter](#yoriito-viss-v1-TimebasedFilter) |  | TimebasedFilter is used to retrieve data per time period |
| change_parameter | [ChangeFilter](#yoriito-viss-v1-ChangeFilter) |  | ChangeFilter is used to retrieve data when data changes |
| range_parameter | [RangeFilter](#yoriito-viss-v1-RangeFilter) |  | RangeFilter is used to retrieve data within a range |
| curvelog_parameter | [CurvelogFilter](#yoriito-viss-v1-CurvelogFilter) |  | CurvelogFilter is used to retrieve data with a curve log (Currently Not Supported) |






<a name="yoriito-viss-v1-PathsFilter"></a>

### PathsFilter
PathsFilter is used to retrieve multiple nodes


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| paths | [string](#string) | repeated | path are VSS node paths |






<a name="yoriito-viss-v1-RangeCondition"></a>

### RangeCondition
RangeCondition defines a single range condition with an operator and a boundary


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| boundary_op | [Operator](#yoriito-viss-v1-Operator) |  | boundary_op defines the operator for the boundary condition |
| boundary | [sint32](#sint32) |  | boundary defines the boundary value for the condition |






<a name="yoriito-viss-v1-RangeConditionArray"></a>

### RangeConditionArray
RangeConditionArray defines an array of range conditions with operators


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| conditions | [RangeConditionWithOp](#yoriito-viss-v1-RangeConditionWithOp) | repeated | conditions is a repeated field of RangeConditionWithOp |






<a name="yoriito-viss-v1-RangeConditionWithOp"></a>

### RangeConditionWithOp
RangeConditionWithOp defines a range condition with an operator and a boundary,


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| boundary_op | [Operator](#yoriito-viss-v1-Operator) |  | boundary_op defines the operator for the boundary condition |
| boundary | [sint32](#sint32) |  | boundary defines the boundary value for the condition |
| combination_op | [Condition](#yoriito-viss-v1-Condition) | optional | combination_op defines the logical condition for combining multiple conditions (default: AND) |






<a name="yoriito-viss-v1-RangeFilter"></a>

### RangeFilter
RangeFilter is used to retrieve data within a range


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| single | [RangeCondition](#yoriito-viss-v1-RangeCondition) |  | single is a single RangeCondition |
| multiple | [RangeConditionArray](#yoriito-viss-v1-RangeConditionArray) |  | multiple is a RangeConditionArray containing multiple RangeConditionWithOp |






<a name="yoriito-viss-v1-SubscribeFilter"></a>

### SubscribeFilter
SubscribeFilter represents a filter for the Subscribe action


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| paths_parameter | [PathsFilter](#yoriito-viss-v1-PathsFilter) |  | PathsFilter is used to retrieve multiple nodes |
| misc_parameter | [MiscFilter](#yoriito-viss-v1-MiscFilter) |  | MiscFilter is a miscellaneous filter |
| combo_filter | [ComboFilter](#yoriito-viss-v1-ComboFilter) |  | ComboFilter is a combination of PathsFilter and MiscFilter |






<a name="yoriito-viss-v1-TimebasedFilter"></a>

### TimebasedFilter
TimebasedFilter is used to retrieve data per time period


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| period | [uint32](#uint32) |  | period is an integer and represents the period time in milliseconds |





 


<a name="yoriito-viss-v1-Condition"></a>

### Condition
Condition defines the logical conditions used in range conditions

| Name | Number | Description |
| ---- | ------ | ----------- |
| CONDITION_UNDEFINED | 0 | CONDITION_UNDEFINED is used when the condition is not defined |
| CONDITION_AND | 1 | AND condition |
| CONDITION_OR | 2 | OR condition |



<a name="yoriito-viss-v1-Operator"></a>

### Operator
Operator defines the operators used in range conditions

| Name | Number | Description |
| ---- | ------ | ----------- |
| OPERATOR_UNDEFINED | 0 | OPERATOR_UNDEFINED is used when the operator is not defined |
| OPERATOR_EQ | 1 | equal |
| OPERATOR_NE | 2 | not equal |
| OPERATOR_GT | 3 | greater than |
| OPERATOR_GTE | 4 | greater than or equal |
| OPERATOR_LT | 5 | less than |
| OPERATOR_LTE | 6 | less than or equal |


 

 

 



<a name="yoriito_viss_v1_types_value-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## yoriito/viss/v1/types/value.proto



<a name="yoriito-viss-v1-BoolArray"></a>

### BoolArray
BoolArray represents an array of booleans in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [bool](#bool) | repeated | repeated field of booleans |






<a name="yoriito-viss-v1-DataPackageCurrent"></a>

### DataPackageCurrent
DataPackageCurrent is a set of VSS path and DataPoint for Current


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| path | [string](#string) |  | the VSS path |
| dp | [DataPointCurrent](#yoriito-viss-v1-DataPointCurrent) | repeated | repeated field of DataPointCurrent |






<a name="yoriito-viss-v1-DataPackageTarget"></a>

### DataPackageTarget
DataPackageTarget is a set of VSS path and DataPoint for Target


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| path | [string](#string) |  | the VSS path |
| dp | [DataPointTarget](#yoriito-viss-v1-DataPointTarget) | repeated | repeated field of DataPointTarget |






<a name="yoriito-viss-v1-DataPackagesCurrent"></a>

### DataPackagesCurrent
DataPackagesCurrent is a array of DataPackageCurrent


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| data | [DataPackageCurrent](#yoriito-viss-v1-DataPackageCurrent) | repeated | repeated field of DataPackageCurrent |






<a name="yoriito-viss-v1-DataPackagesTarget"></a>

### DataPackagesTarget
DataPackagesTarget is an array of DataPackageTarget


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| data | [DataPackageTarget](#yoriito-viss-v1-DataPackageTarget) | repeated | repeated field of DataPackageTarget |






<a name="yoriito-viss-v1-DataPointCurrent"></a>

### DataPointCurrent
DataPointCurrent represents a single data point for Current


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| storedTimestamp | [int64](#int64) |  | Timestamp when a VISS Server receive this data |
| value | [ValueType](#yoriito-viss-v1-ValueType) |  | value of tha VSS data |
| producedTimestamp | [int64](#int64) | optional | Timestamp when data are produced in a vehicle platform(sensor, actuator, ECU etc...) |
| is_available_sensor | [bool](#bool) | optional | availablity as sensor |
| is_available_actuator | [bool](#bool) | optional | availablity as actuator |






<a name="yoriito-viss-v1-DataPointTarget"></a>

### DataPointTarget
DataPointTarget represents a single data point for Target


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| value | [ValueType](#yoriito-viss-v1-ValueType) |  | value of the VSS data |






<a name="yoriito-viss-v1-DoubleArray"></a>

### DoubleArray
DoubleArray represents an array of floating point numbers 64-bit in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [double](#double) | repeated | repeated field of floating point numbers 64-bit |






<a name="yoriito-viss-v1-FloatArray"></a>

### FloatArray
FloatArray represents an array of floating point numbers 32-bit in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [float](#float) | repeated | repeated field of floating point numbers 32-bit |






<a name="yoriito-viss-v1-Int16Array"></a>

### Int16Array
Int16Array represents an array of signed integers 16-bit in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [sint32](#sint32) | repeated | repeated field of signed integers 16-bit |






<a name="yoriito-viss-v1-Int32Array"></a>

### Int32Array
Int32Array represents an array of signed integers 32-bit in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [sint32](#sint32) | repeated | repeated field of signed integers 32-bit |






<a name="yoriito-viss-v1-Int64Array"></a>

### Int64Array
Int64Array represents an array of signed integers 64-bit in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [sint64](#sint64) | repeated | repeated field of signed integers 64-bit |






<a name="yoriito-viss-v1-Int8Array"></a>

### Int8Array
Int8Array represents an array of signed integers 8-bit in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [sint32](#sint32) | repeated | repeated field of signed integers 8-bit |






<a name="yoriito-viss-v1-MetadataEntries"></a>

### MetadataEntries
MetadataEntries represents a array of MetadataEntry


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| entries | [MetadataEntry](#yoriito-viss-v1-MetadataEntry) | repeated | repeated field of MetadataEntry |






<a name="yoriito-viss-v1-MetadataEntry"></a>

### MetadataEntry
MetadataEntry represents a single metadata entry for a VSS node
See https://covesa.github.io/vehicle_signal_specification/rule_set/data_entry/sensor_actuator/index.html#mandatory-data-entry-attributes

We changed the original definition of COVESA VSS like the following.

- `pattern`
  - In the original definition, pattern can accept string or string[].
  - To simplify the definition, we use StringArray only for a single string pattern.
- `max` and `min`
  - In the original definition, max/min can accept other types like float, double, etc.
  - Reference:
    - [COVESA VSS Datatypes](https://covesa.github.io/vehicle_signal_specification/rule_set/data_entry/data_types/index.html#supported-datatypes)
    - [COVESA VSS Sensors, Actuators and Attributes](https://covesa.github.io/vehicle_signal_specification/rule_set/data_entry/sensor_actuator/index.html#optional-data-entry-attributes)
  - But, to simplify the definition, we use int32 only.
  - This means that the maximum/minimum value is expected to be an integer.
  - We choose int32 because:
    - int32 is practically sufficient to represent the maximum/minimum values for most VSS data.
    - it is a fixed-size integer type, which makes it easier to work with in terms of memory and performance.
- `allowed`
  - In the original definition, allowed can accept other types like string, int32, etc.
  - Reference:
    - [COVESA VSS Value Restrictions](https://covesa.github.io/vehicle_signal_specification/rule_set/data_entry/allowed/index.html)
  - But, to simplify the definition, we use StringArray only.
  - It&#39;s because the allowed values are represented as enum, now.
  - And, allowing other types makes the definition more comprecated.
  - If you want to support other types, you can cast the allowed strings to other types.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| path | [string](#string) |  | the VSS path |
| type | [NodeType](#yoriito-viss-v1-NodeType) |  | the node type of VSS leaf |
| datatype | [DataType](#yoriito-viss-v1-DataType) |  | the data type of the VSS data |
| deprecated | [string](#string) | optional | the flag to indicate if the node is deprecated |
| unit | [string](#string) | optional | the unit of the VSS data, e.g. &#34;km/h&#34;, &#34;Celsius&#34;, &#34;m/s^2&#34; |
| pattern | [StringArray](#yoriito-viss-v1-StringArray) | optional | allowed pattern. |
| max | [int32](#int32) | optional | the maximum value of the VSS data. |
| min | [int32](#int32) | optional | the minimum value of the VSS data. |
| description | [string](#string) |  | a human-readable description of the VSS node |
| comment | [string](#string) | optional | optional comment for the VSS node |
| allowed | [StringArray](#yoriito-viss-v1-StringArray) | optional | allowed values for the VSS data |
| arraysize | [uint64](#uint64) | optional | the size of the array |
| default | [ValueType](#yoriito-viss-v1-ValueType) | optional | default value of the VSS data |
| custom_metadata | [google.protobuf.Struct](#google-protobuf-Struct) | optional | custom metadata for the VSS node |






<a name="yoriito-viss-v1-StringArray"></a>

### StringArray
StringArray represents an array of strings in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [string](#string) | repeated | repeated field of strings |






<a name="yoriito-viss-v1-Uint16Array"></a>

### Uint16Array
Uint16Array represents an array of unsigned integers 16-bit in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [uint32](#uint32) | repeated | repeated field of unsigned integers 16-bit |






<a name="yoriito-viss-v1-Uint32Array"></a>

### Uint32Array
Uint32Array represents an array of unsigned integers 32-bit in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [uint32](#uint32) | repeated | repeated field of unsigned integers 32-bit |






<a name="yoriito-viss-v1-Uint64Array"></a>

### Uint64Array
Uint64Array represents an array of unsigned integers 64-bit in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [uint64](#uint64) | repeated | repeated field of unsigned integers 64-bit |






<a name="yoriito-viss-v1-Uint8Array"></a>

### Uint8Array
Uint8Array represents an array of unsigned integers 8-bit in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| values | [uint32](#uint32) | repeated | repeated field of unsigned integers 8-bit |






<a name="yoriito-viss-v1-ValueObject"></a>

### ValueObject
ValueObject represents Struct(a complex data type in the VISS)


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| properties | [ValueProperty](#yoriito-viss-v1-ValueProperty) | repeated | properties is a repeated field of ValueProperty |






<a name="yoriito-viss-v1-ValueProperty"></a>

### ValueProperty
ValueProperty is a key-value store


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| key | [string](#string) |  | key is the name of the property |
| value | [ValueType](#yoriito-viss-v1-ValueType) |  | value is the value of the property |






<a name="yoriito-viss-v1-ValueType"></a>

### ValueType
ValueType represents the value type in the VISS


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| string | [string](#string) |  | string value |
| bool | [bool](#bool) |  | boolean value |
| int8 | [sint32](#sint32) |  | signed integer 8-bit |
| int16 | [sint32](#sint32) |  | signed integer 16-bit |
| int32 | [sint32](#sint32) |  | signed integer 32-bit |
| int64 | [sint64](#sint64) |  | signed integer 64-bit |
| uint8 | [uint32](#uint32) |  | unsigned integer 8-bit |
| uint16 | [uint32](#uint32) |  | unsigned integer 16-bit |
| uint32 | [uint32](#uint32) |  | unsigned integer 32-bit |
| uint64 | [uint64](#uint64) |  | unsigned integer 64-bit |
| float | [float](#float) |  | floating point number 32-bit |
| double | [double](#double) |  | floating point number 64-bit |
| string_array | [StringArray](#yoriito-viss-v1-StringArray) |  | array of strings |
| bool_array | [BoolArray](#yoriito-viss-v1-BoolArray) |  | array of booleans |
| int8_array | [Int8Array](#yoriito-viss-v1-Int8Array) |  | array of signed integers 8-bit |
| int16_array | [Int16Array](#yoriito-viss-v1-Int16Array) |  | array of signed integers 16-bit |
| int32_array | [Int32Array](#yoriito-viss-v1-Int32Array) |  | array of signed integers 32-bit |
| int64_array | [Int64Array](#yoriito-viss-v1-Int64Array) |  | array of signed integers 64-bit |
| uint8_array | [Uint8Array](#yoriito-viss-v1-Uint8Array) |  | array of unsigned integers 8-bit |
| uint16_array | [Uint16Array](#yoriito-viss-v1-Uint16Array) |  | array of unsigned integers 16-bit |
| uint32_array | [Uint32Array](#yoriito-viss-v1-Uint32Array) |  | array of unsigned integers 32-bit |
| uint64_array | [Uint64Array](#yoriito-viss-v1-Uint64Array) |  | array of unsigned integers 64-bit |
| float_array | [FloatArray](#yoriito-viss-v1-FloatArray) |  | array of floating point numbers 32-bit |
| double_array | [DoubleArray](#yoriito-viss-v1-DoubleArray) |  | array of floating point numbers 64-bit |
| value_object | [ValueObject](#yoriito-viss-v1-ValueObject) |  | VSS struct (used for complex data types) |





 


<a name="yoriito-viss-v1-DataType"></a>

### DataType
DataType represents the type of data in the VISS

| Name | Number | Description |
| ---- | ------ | ----------- |
| DATATYPE_NONE | 0 | Unspecified data type |
| DATATYPE_STRING | 1 | string |
| DATATYPE_BOOL | 2 | boolean |
| DATATYPE_INT8 | 3 | integer 8-bit |
| DATATYPE_INT16 | 4 | integer 16-bit |
| DATATYPE_INT32 | 5 | integer 32-bit |
| DATATYPE_INT64 | 6 | integer 64-bit |
| DATATYPE_UINT8 | 7 | unsigned integer 8-bit |
| DATATYPE_UINT16 | 8 | unsigned integer 16-bit |
| DATATYPE_UINT32 | 9 | unsigned integer 32-bit |
| DATATYPE_UINT64 | 10 | unsigned integer 64-bit |
| DATATYPE_FLOAT | 11 | floating point number 32-bit |
| DATATYPE_DOUBLE | 12 | floating point number 64-bit |
| DATATYPE_ARRAY_STRING | 13 | array of strings |
| DATATYPE_ARRAY_BOOL | 14 | array of booleans |
| DATATYPE_ARRAY_INT8 | 15 | array of integers 8-bit |
| DATATYPE_ARRAY_INT16 | 16 | array of integers 16-bit |
| DATATYPE_ARRAY_INT32 | 17 | array of integers 32-bit |
| DATATYPE_ARRAY_INT64 | 18 | array of integers 64-bit |
| DATATYPE_ARRAY_UINT8 | 19 | array of unsigned integers 8-bit |
| DATATYPE_ARRAY_UINT16 | 20 | array of unsigned integers 16-bit |
| DATATYPE_ARRAY_UINT32 | 21 | array of unsigned integers 32-bit |
| DATATYPE_ARRAY_UINT64 | 22 | array of unsigned integers 64-bit |
| DATATYPE_ARRAY_FLOAT | 23 | array of floating point numbers 32-bit |
| DATATYPE_ARRAY_DOUBLE | 24 | array of floating point numbers 64-bit |
| DATATYPE_STRUCT | 25 | VSS struct (used for complex data types) |



<a name="yoriito-viss-v1-NodeType"></a>

### NodeType
NodeType represents the type of a node in the VISS

| Name | Number | Description |
| ---- | ------ | ----------- |
| NODE_UNKNOWN | 0 | Unspecified node type |
| NODE_BRANCH | 1 | branch node, which can have child nodes |
| NODE_ATTRIBUTE | 2 | leaf node, which is a static data node |
| NODE_SENSOR | 3 | leaf node, which is a sensor data node |
| NODE_ACTUATOR | 4 | leaf node, which is an actuator data node |


 

 

 



## Scalar Value Types

| .proto Type | Notes | C++ | Java | Python | Go | C# | PHP | Ruby |
| ----------- | ----- | --- | ---- | ------ | -- | -- | --- | ---- |
| <a name="double" /> double |  | double | double | float | float64 | double | float | Float |
| <a name="float" /> float |  | float | float | float | float32 | float | float | Float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum or Fixnum (as required) |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="bool" /> bool |  | bool | boolean | boolean | bool | bool | boolean | TrueClass/FalseClass |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode | string | string | string | String (UTF-8) |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str | []byte | ByteString | string | String (ASCII-8BIT) |

