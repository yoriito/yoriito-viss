# Define/Delete

## Initialization of VSS Nodes

VSS nodes are initially configured when the VISS server starts, based on a definition file derived from vspec (commonly in JSON format, referred to here as "vspec json").

Each VSS node has its properties defined through this vspec json, including max/min values, units, data types, and other attributes.

These VSS nodes remain unchanged during normal server operation.

## Modifying VSS Node Definitions

There may be situations where you need to add new VSS nodes or update VSS node metadata—for example, when vehicle equipment is updated, or when a software update expands the controllable range of the equipment.

In such cases, to modify existing VSS node definitions, you must replace the current vspec json with a new one and restart the server.

A typical method for replacing the vspec json is OTA.

By creating a new vspec json outside the vehicle, delivering it via OTA, and then restarting the VISS server, you can use the new VSS node definitions.

However, for vehicles that cannot fully benefit from OTA, or when you only want to change a small portion of existing VSS node definitions, generating a vspec json from scratch outside the vehicle can be costly.
Yoriito VISS provides functionality for such cases.

This is the `Define`/`Delete` action.

`Define`/`Delete` is an action provided only to Producers.
The `Define` action is used to create new VSS nodes or overwrite existing ones.
The `Delete` action is used to delete VSS nodes.

By executing `Define`/`Delete` actions, you can generate a new vspec json based on the existing vspec json.
To use `Define`/`Delete` actions, you must first place the VISS server into an "initializable" state.

There are two ways to enable this state:
* Use a SetCurrent request to set the `Server.Initializing` node to `true`.
* Start the VISS server with an option that allows initialization. (In this case, the initial value of the `Server.Initializing` node will be `true`.)

When `Server.Initializing` is set to `true`, the VISS server performs the following:
* Transitions its internal state to the "initializable" state.
   * In this state, all requests except `Define`, `Delete` and `SetCurrent` to `Server.Initializing` will return an error.
   * VSS node modifications via `Define` and `Delete` are permitted only in this state.
   * All streams created before entering the initializable state are discarded.
   * All normal VISS server functionality is suspended.

Producers can use `Define` or `Delete` to overwrite existing VSS node definitions, add new nodes, or delete existing nodes.
After completing the node definition process, the Producer must set `Server.Initializing` to `false`.

When `Server.Initializing` changes from `true` to `false`, the VISS server performs the following:
* Dumps all VSS nodes as a vspec json file.
* Transitions from the initializable state to the "vspec json load" state.
   * In this state, the server reloads VSS nodes using the dumped vspec json.
   * After reloading, the server transitions to the "normal" state, where it accepts standard actions such as `Get`, `Set*`, and `Subscribe`, and stops accepting `Define`/`Delete`.

Note: The VISS server is only responsible for dumping the vspec json file.  
Management, redundancy, and distribution of the dumped file are the responsibility of the system.
