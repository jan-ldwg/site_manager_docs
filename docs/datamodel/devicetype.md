Device types can be thought of as templates that are used to create instances of devices. In contrast to some other applications (e.g. Netbox) site_manager does not duplicate information from the device type into each device instance upon creation, but instead retrieves general information for a device by querying the device type. This means that a device type may only be deleted from the database when there are no devices of this type in the database. This also means that some information in the device type can be changed and all existing instances of this device will be updated on future queries.

!!! note

    The number of ports or module slots can not be changed afterwards.

#### Manufacturers

id: all lowercase, - allowed
name: Everything allowed
nameShort: Lower and Uppercase, max. 16 char

#### Id

Each device type is identified by a human readable, unique id.

The rules to generate this id are as follows:

1. Start with the id of the manufacturer
2. Convert the device name to lowercase
3. Replace all spaces, dots and underscores with -
4. Remove all remaining special characters

The id has to be a maximum of 48 characters

To make this clearer here a some examples:

| Device name                                   | Device id                               |
| --------------------------------------------- | --------------------------------------- |
| Lawo Power Core Rev.3                         | `lawo-power-core-rev-3`                 |
| DirectOut MAVEN.A                             | `directout-maven-a`                     |
| Sony HDC-5500                                 | `sony-hdc-5500`                         |
| Blackmagic Design ATEM 1 M/E Constellation HD | `blackmagic-atem-1-me-constellation-hd` |

#### Port Type

Each device type can have a number of port types. Every port type represents a specific port on a specific device type. A port type is never reused for multiple different ports. This means a port type does not represent a concept like an generic SDI input, but a specific SDI input on a specific device (or module). The name of the port type should be as it is labeled on the device. If there is no labeling on the device, the name as used in the device´s manual should be used. If this is also not possible a logical name should be chosen.

Every port type has a list of signal types it supports. These are important to validate connections between ports.

Every port also has a direction.

| Label   | Meaning                 | Explanation                                                                             |
| ------- | ----------------------- | --------------------------------------------------------------------------------------- |
| `IN`    | Input                   | Source of strictly unidirectional signals like SDI, analog Audio, etc.                  |
| `OUT`   | Output                  | Sink of strictly unidirectional signals like SDI, analog Audio, etc.                    |
| `INOUT` | Input/Output Switchable | Source or sink of strictly unidirectional signals depending on configuration            |
| `BIDI`  | Bidirectional           | Used for bidirectional signals where no device is the clear leader, e.g. GPIO           |
| `UP`    | Uplink                  | Used on the follower device in a bidirectional signal e.g. ethernet ports on enddevices |
| `DOWN`  | Downlink                | Used on the leader device in a bidirectional signal e.g. ethernet ports on switches     |
| `REAR`  | Passive rear            | Ports on passive components that mostly connect to structured cabling                   |
| `FRONT` | Passive front           | Ports on passive components that mostly connect to patch cabling                        |

|         | `IN` | `OUT` | `INOUT` | `BIDI` | `UP` | `DOWN` | `REAR` | `FRONT` |
| ------- | ---- | ----- | ------- | ------ | ---- | ------ | ------ | ------- |
| `IN`    | ❌   | ✅    | ✅      | ❌     | ❌   | ❌     | ✅     | ✅      |
| `OUT`   | ✅   | ❌    | ✅      | ❌     | ❌   | ❌     | ✅     | ✅      |
| `INOUT` | ✅   | ✅    | ✅      | ❌     | ❌   | ❌     | ✅     | ✅      |
| `BIDI`  | ❌   | ❌    | ❌      | ✅     | ❌   | ❌     | ✅     | ✅      |
| `UP`    | ❌   | ❌    | ❌      | ❌     | ✅   | ✅     | ✅     | ✅      |
| `DOWN`  | ❌   | ❌    | ❌      | ❌     | ✅   | ✅     | ✅     | ✅      |
| `REAR`  | ✅   | ✅    | ✅      | ✅     | ✅   | ✅     | ✅     | ✅      |
| `FRONT` | ✅   | ✅    | ✅      | ✅     | ✅   | ✅     | ✅     | ✅      |

#### Module Slot Type
