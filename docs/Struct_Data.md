# VISS Service example Pattern 

This document provides practical JSON examples for VISS APIs when VSS struct data types are used.
It covers two patterns:

- Struct Pattern (Normal): a signal/attribute directly uses a struct type.
- Struct Pattern (Struct in Struct): a struct member itself is another struct.

All payload samples are written using protobuf JSON field naming.


## Struct Pattern (Normal)

In this pattern, a node such as `Delivery` or `ReturnAddress` uses `Types.DeliveryInfo` as its datatype.
The struct value is represented as `valueObject.properties` in runtime payloads.



### vspec Sample


The following VSPEC defines one struct type (`Types.DeliveryInfo`) and two nodes that use it.
`Delivery` is a sensor node, and `ReturnAddress` is an attribute node with a default value.


inline struct is not allowed!.

```yaml
Types:
  type: branch

Types.DeliveryInfo:
  type: struct
  description: A struct datatype containing info for each delivery

Types.DeliveryInfo.Address:
  datatype: string
  type: property
  description: Destination address
Types.DeliveryInfo.Receiver:
  datatype: string
  type: property
  description: Name of receiver
Delivery:
  datatype: Types.DeliveryInfo
  type: sensor
ReturnAddress:
  datatype: Types.DeliveryInfo
  type: attribute
  description: Where to send returns
  default:
    Address: "221B Baker Street"
    Receiver: "Sherlock Holmes"
```



### Get

Use GetCurrent to retrieve the current value of a struct node.
The returned value is encoded as key-value properties inside `valueObject`.

#### Request


```json
{
  "path": "Delivery"
}
```

#### Response

The response includes the timestamp (`ts`), data package list (`data.data`), and datapoints (`dp`).
For struct values, each member is represented by `key` and typed `value`.

```json
{
  "ts": 1718179200000,
  "data": {
    "data": [
      {
        "path": "Delivery",
        "dp": [
          {
            "storedTimestamp": 1718179199000,
            "value": {
              "valueObject": {
                "properties": [
                  {
                    "key": "Address",
                    "value": {
                      "string": "1-2-3 Tokyo"
                    }
                  },
                  {
                    "key": "Receiver",
                    "value": {
                      "string": "Taro Yamada"
                    }
                  }
                ]
              }
            },
            "isAvailableSensor": true
          }
        ]
      }
    ]
  }
}
```

### Set

Use SetTarget to update target values for writable nodes.
For struct payloads, keep the same `valueObject.properties` structure used in Get responses.

#### Request

```json
{
  "SetTargetRequest": {
    "data": {
      "data": [
        {
          "path": "Delivery",
          "dp": [
            {
              "value": {
                "valueObject": {
                  "properties": [
                    {
                      "key": "Address",
                      "value": {
                        "string": "1-2-3 Tokyo"
                      }
                    },
                    {
                      "key": "Receiver",
                      "value": {
                        "string": "Taro Yamada"
                      }
                    }
                  ]
                }
              }
            }
          ]
        }
      ]
    }
  }
}
```

#### Response

An empty `success` object means the request was accepted.

```json
{
  "SetTargetResponseSuccess": {
    "ts": 1718179201000,
    "success": {}
  }
}
```

### Inspect

Use Inspect to retrieve metadata for both node-level entries and struct type definitions.

#### Respnse Data 

```json
{
  "InspectRequest": {
    "path": "ReturnAddress"
  }
}
```

#### Response Data 

- Both node attribute metadata and datatype metadata are required.
- Since clients query VSS signals/attributes, returning signal metadata together with struct type metadata is recommended.

```json
{
  "InspectResponseSuccess": {
    "ts": 1718179202000,
    "metadata": {
      "metadataEntries": [
        {
          "path": "ReturnAddress",
          "type": "NODE_ATTRIBUTE",
          "datatype": "DATATYPE_NONE",
          "description": "Where to send returns",
          "datatypePath": "Types.DeliveryInfo",
          "default": {
            "valueObject": {
              "properties": [
                {
                  "key": "Address",
                  "value": {
                    "string": "221B Baker Street"
                  }
                },
                {
                  "key": "Receiver",
                  "value": {
                    "string": "Sherlock Holmes"
                  }
                }
              ]
            }
          }
        }
      ],
      "structMetadataEntries": [
        {
          "path": "Types.DeliveryInfo",
          "description": "A struct datatype containing info for each delivery",
          "members": [
            {
              "property": {
                "name": "Address",
                "datatype": "DATATYPE_STRING",
                "description": "Destination address"
              }
            },
            {
              "property": {
                "name": "Receiver",
                "datatype": "DATATYPE_STRING",
                "description": "Name of receiver"
              }
            }
          ]
        }
      ]
    }
  }
}
```

### Define

Use Define to register or overwrite metadata entries.
For struct-based nodes, define the node entry in `metadataEntries` and the struct schema in `structMetadataEntries`.

#### Request Data

```json
{
  "DefineRequest": {
    "entries": {
      "metadataEntries": [
        {
          "path": "Delivery",
          "type": "NODE_SENSOR",
          "datatype": "DATATYPE_NONE",
          "datatypePath": "Types.DeliveryInfo",
          "description": "A struct datatype containing info for each delivery"
        },
        {
          "path": "ReturnAddress",
          "type": "NODE_ATTRIBUTE",
          "datatype": "DATATYPE_NONE",
          "datatypePath": "Types.DeliveryInfo",
          "description": "Where to send returns",
          "default": {
            "valueObject": {
              "properties": [
                {
                  "key": "Address",
                  "value": {
                    "string": "221B Baker Street"
                  }
                },
                {
                  "key": "Receiver",
                  "value": {
                    "string": "Sherlock Holmes"
                  }
                }
              ]
            }
          }
        }
      ],
      "structMetadataEntries": [
        {
          "path": "Types.DeliveryInfo",
          "description": "A struct datatype containing info for each delivery",
          "members": [
            {
              "property": {
                "name": "Address",
                "datatype": "DATATYPE_STRING",
                "description": "Destination address"
              }
            },
            {
              "property": {
                "name": "Receiver",
                "datatype": "DATATYPE_STRING",
                "description": "Name of receiver"
              }
            }
          ]
        }
      ]
    }
  }
}
```


#### Response

An empty `success` object indicates that metadata was updated successfully.

```json
{
  "DefineResponseSuccess": {
    "ts": 1718179203000,
    "success": {}
  }
}
```

## Struct Pattern (Struct in Struct)

In this pattern, one struct contains another struct as a member.
Here, `Types.DeliveryInfo` contains `Open` whose datatype is `Types.OpenHours`.
Runtime values are nested `valueObject` structures.

https://covesa.github.io/vehicle_signal_specification/rule_set/data_entry/data_types_struct/index.html

inline struct is not allowed.



```yaml
OpenHours:
  type: struct
  description: A struct datatype containing information on open hours

OpenHours.Open:
  datatype: uint8
  type: property
  max: 24
  description: Time the address opens

OpenHours.Close:
  datatype: uint8
  type: property
  max: 24
  description: Time the address close

DeliveryInfo:
  type: struct
  description: A struct datatype containing info for each delivery

DeliveryInfo.Address:
  datatype: string
  type: property
  description: Destination address

DeliveryInfo.Receiver:
  datatype: string
  type: property
  description: Name of receiver

DeliveryInfo.Open:
  datatype: OpenHours
  type: property
  description: When is receiver available

ReturnAddress:
  datatype: Types.DeliveryInfo
  type: attribute
  description: Where to send returns
  default:
    Address: "221B Baker Street"
    Receiver: "Sherlock Holmes"
    Open:
        Open: 9
        Close: 17
```




### Get

GetCurrent returns nested struct values recursively.
When a member is also a struct, that member value is another `valueObject`.

#### Request


```json
{
  "GetCurrentRequest": {
    "path": "ReturnAddress"
  }
}
```

#### Response

In this example, `Open` is a nested struct that includes `Open` and `Close` members.

```json
{
  "GetCurrentResponseSuccess": {
    "ts": 1718179204000,
    "data": {
      "data": [
        {
          "path": "ReturnAddress",
          "dp": [
            {
              "storedTimestamp": 1718179203000,
              "value": {
                "valueObject": {
                  "properties": [
                    {
                      "key": "Address",
                      "value": {
                        "string": "221B Baker Street"
                      }
                    },
                    {
                      "key": "Receiver",
                      "value": {
                        "string": "Sherlock Holmes"
                      }
                    },
                    {
                      "key": "Open",
                      "value": {
                        "valueObject": {
                          "properties": [
                            {
                              "key": "Open",
                              "value": {
                                "uint8": 9
                              }
                            },
                            {
                              "key": "Close",
                              "value": {
                                "uint8": 17
                              }
                            }
                          ]
                        }
                      }
                    }
                  ]
                }
              }
            }
          ]
        }
      ]
    }
  }
}
```

### Set

SetTarget for nested structs follows the same recursive representation as GetCurrent.
Each nested level is represented by `valueObject.properties`.

#### Request

```json
{
  "SetTargetRequest": {
    "data": {
      "data": [
        {
          "path": "ReturnAddress",
          "dp": [
            {
              "value": {
                "valueObject": {
                  "properties": [
                    {
                      "key": "Address",
                      "value": {
                        "string": "221B Baker Street"
                      }
                    },
                    {
                      "key": "Receiver",
                      "value": {
                        "string": "Sherlock Holmes"
                      }
                    },
                    {
                      "key": "Open",
                      "value": {
                        "valueObject": {
                          "properties": [
                            {
                              "key": "Open",
                              "value": {
                                "uint8": 9
                              }
                            },
                            {
                              "key": "Close",
                              "value": {
                                "uint8": 17
                              }
                            }
                          ]
                        }
                      }
                    }
                  ]
                }
              }
            }
          ]
        }
      ]
    }
  },
}
```

#### Response

An empty `success` object means the target update request was accepted.


```json
{
  "SetTargetResponseSuccess": {
    "ts": 1718179205000,
    "success": {}
  }
}
```


### Inspect

Inspect for this pattern returns:

- node metadata (`metadataEntries`) for `ReturnAddress`.
- struct metadata (`structMetadataEntries`) for both `Types.DeliveryInfo` and `Types.OpenHours`.

#### Respnse Data 

```json
{
  "InspectRequest": {
    "path": "ReturnAddress"
  }
}
```

#### Response Data 

The metadata response below demonstrates how nested struct relationships are expressed through `datatypePath`.



```json
{
  "InspectResponseSuccess": {
    "ts": 1718179206000,
    "metadata": {
      "metadataEntries": [
        {
          "path": "ReturnAddress",
          "type": "NODE_ATTRIBUTE",
          "datatype": "DATATYPE_NONE",
          "datatypePath": "Types.DeliveryInfo",
          "description": "Where to send returns",
          "default": {
            "valueObject": {
              "properties": [
                {
                  "key": "Address",
                  "value": {
                    "string": "221B Baker Street"
                  }
                },
                {
                  "key": "Receiver",
                  "value": {
                    "string": "Sherlock Holmes"
                  }
                },
                {
                  "key": "Open",
                  "value": {
                    "valueObject": {
                      "properties": [
                        {
                          "key": "Open",
                          "value": {
                            "uint8": 9
                          }
                        },
                        {
                          "key": "Close",
                          "value": {
                            "uint8": 17
                          }
                        }
                      ]
                    }
                  }
                }
              ]
            }
          }
        }
      ],
      "structMetadataEntries": [
        {
          "path": "Types.OpenHours",
          "description": "A struct datatype containing information on open hours",
          "members": [
            {
              "property": {
                "name": "Open",
                "datatype": "DATATYPE_UINT8",
                "max": 24,
                "description": "Time the address opens"
              }
            },
            {
              "property": {
                "name": "Close",
                "datatype": "DATATYPE_UINT8",
                "max": 24,
                "description": "Time the address close"
              }
            }
          ]
        },
        {
          "path": "Types.DeliveryInfo",
          "description": "A struct datatype containing info for each delivery",
          "members": [
            {
              "property": {
                "name": "Address",
                "datatype": "DATATYPE_STRING",
                "description": "Destination address"
              }
            },
            {
              "property": {
                "name": "Receiver",
                "datatype": "DATATYPE_STRING",
                "description": "Name of receiver"
              }
            },
            {
              "property": {
                "name": "Open",
                "datatype": "DATATYPE_NONE",
                "datatypePath": "Types.OpenHours",
                "description": "When is receiver available"
              }
            }
          ]
        }
      ]
    }
  }
}
```

### Define

Define must include all relevant struct schemas used by the target node.
In this example, `Types.DeliveryInfo` references `Types.OpenHours`, so both are provided in `structMetadataEntries`.

#### Request Data

```json
{
  "DefineRequest": {
    "entries": {
      "metadataEntries": [
        {
          "path": "ReturnAddress",
          "type": "NODE_ATTRIBUTE",
          "datatype": "DATATYPE_NONE",
          "datatypePath": "Types.DeliveryInfo",
          "description": "Where to send returns",
          "default": {
            "valueObject": {
              "properties": [
                {
                  "key": "Address",
                  "value": {
                    "string": "221B Baker Street"
                  }
                },
                {
                  "key": "Receiver",
                  "value": {
                    "string": "Sherlock Holmes"
                  }
                },
                {
                  "key": "Open",
                  "value": {
                    "valueObject": {
                      "properties": [
                        {
                          "key": "Open",
                          "value": {
                            "uint8": 9
                          }
                        },
                        {
                          "key": "Close",
                          "value": {
                            "uint8": 17
                          }
                        }
                      ]
                    }
                  }
                }
              ]
            }
          }
        }
      ],
      "structMetadataEntries": [
        {
          "path": "Types.OpenHours",
          "description": "A struct datatype containing information on open hours",
          "members": [
            {
              "property": {
                "name": "Open",
                "datatype": "DATATYPE_UINT8",
                "max": 24,
                "description": "Time the address opens"
              }
            },
            {
              "property": {
                "name": "Close",
                "datatype": "DATATYPE_UINT8",
                "max": 24,
                "description": "Time the address close"
              }
            }
          ]
        },
        {
          "path": "Types.DeliveryInfo",
          "description": "A struct datatype containing info for each delivery",
          "members": [
            {
              "property": {
                "name": "Address",
                "datatype": "DATATYPE_STRING",
                "description": "Destination address"
              }
            },
            {
              "property": {
                "name": "Receiver",
                "datatype": "DATATYPE_STRING",
                "description": "Name of receiver"
              }
            },
            {
              "property": {
                "name": "Open",
                "datatype": "DATATYPE_NONE",
                "datatypePath": "Types.OpenHours",
                "description": "When is receiver available"
              }
            }
          ]
        }
      ]
    }
  }
}
```

#### Response

An empty `success` object indicates that the Define operation completed without errors.

```json
{
  "DefineResponseSuccess": {
    "ts": 1718179207000,
    "success": {}
  }
}
```

