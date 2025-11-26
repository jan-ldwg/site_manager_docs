# `/api/devices`

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

=== "GET"

    **Description:**

    Returns a list of all devices.

    **Path:**

    ```HTTP
    GET /api/v1/devices
    ```

    **Query Parameters:**

    | Name | Type | Description |
    |------|------|---------------|
    | `rackId` | `string | string[]` | (optional) Retrieves only devices in this rack |
    | `roomId`| `string | string[]`| (optional) Retrieves only devices in this room |
    | `buildingId`| `string | string[]`| (optional) Retrieves only devices in this building |

    **Request Body:**

    None.

    **Status Codes:**

    | Code | Status |
    |------|------------|
    | `200` | Success |
    | `500` | Internal server error |

    **Response Body:**

    === "Example"
        ```json
        --8<-- "json_examples/GET_devices_res.jsonc"
        ```

    === "Schema"
        ```json
        {}
        ```

    | Name    | Type | Description | Notes |
    |---------|---|---------------| ------- |
    | `id` | `string` | UUIDv4 of the device |
    | `name`| `string | null`| human readable name of the device | limited to 16 characters
    | `deviceTypeId`| `string`| id of the type of the device |
    | `deviceTypeName` | `string` | human readable name of the device type|
    | `manufacturerId`| `string` | id of the manufacturer of the device |
    | `manufacturerName` | `string` | full name of the manufacturer |
    | `manufacturerNameShort` | `string` | colloquial name of the manufacturer |
    | `description` |`string | null` | user defined description of the device |
    | `serialNumber`|`string | null`| serial number of the device | limited to 32 characters
    | `siteId`| `string` | UUIDv4 of the site |
    | `siteName`| `string`| human readable name of the site |
    | `buildingId`| `string` | UUIDv4 of the building |
    | `buildingName`| `string`| human readable name of the building |
    | `roomId`| `string` | UUIDv4 of the room |
    | `roomName`| `string`| human readable name of the room |
    | `rackId`| `string` | UUIDv4 of the rack |
    | `rackName`| `string` | human readable name of the rack |
    | `rackElevation`| `number | null` | position of the device in RU counted from the bottom of the rack |
    | `rackPosition`| `FRONT | BACK | LOOSE`| position of the device in the rack |
    | `ports`| | |
    | `portId`| `string` | UUIDv4 of the port |
    | `portTypeId` | `string` | UUIDv4 of the port type |
    | `portTypeName` | `string` | name of the port as labeled on the device |
    | `portTypeDirection` | `"IN" | "OUT" | "BIDI"` | direction of the port type|
    | `connectorId`| `string`| id of the connector |
    | `connectorName`| `string`| human readable name of the connector |
    | `connectorGender`| `"MALE" | "FEMALE" | "HERMA“`| gender of the connector |
    | `connectorIcon`| `string`| name of the associated icon | every icon is available as svg|
    | `moduleSlots`| | |
    | `moduleSlotId`| `string` | UUIDv4 of the module slot |
    | `moduleSlotTypeId` | `string` | UUIDv4 of the module slot type |
    | `moduleSlotTypeName`| `string`| name of the slot as labeled on the device|
    | `module`| | |
    | `moduleId`| `string` | UUIDv4 of the module |
    | `moduleTypeId`| `string`| id of the module type |
    | `moduleTypeName`| `string` | human readable name of the module type |
    | `manufacturerId`| `string` | id of the manufacturer of the module |
    | `manufacturerName` | `string` | full name of the manufacturer |
    | `manufacturerNameShort` | `string` | colloquial name of the manufacturer |

=== "POST"

    **Description:**

    Creates a new device.

    **Path:**

    ```HTTP
    POST /api/v1/devices
    ```

    **Query Parameters:**

    None.

    **Request Body:**

    === "Example"
        ```json
        --8<-- "json_examples/POST_devices_req.json"
        ```

    === "Schema"
        ```json
        {}
        ```

    | Name    | Type | Description | Notes |
    |---------|---|---------------| ------- |
    | `deviceTypeId`| `string`| UUIDv4 of the device type of which to create the device
    | `rackId`| `string` | UUIDv4 of the rack in which the device should be created |
    | `name` | `string`| (optional) human readable name of the device to create|
    | `description` |`string | null` | (optional) user defined description of the device |
    | `serialNumber`|`string | null`| (optional) serial number of the device | limited to 32 characters

     **Status Codes:**

    | Code | Bedeutung |
    |------|------------|
    | `201` | Created |
    | `400` | Invalid device type |
    | `400` | Invalid rack id |
    | `500`| Internal server error |

    **Response Body:**

    === "Example"
        ```json
        --8<-- "json_examples/POST_devices_res.json"
        ```

    === "Schema"
        ```json
        {}
        ```

    | Name    | Type | Description | Notes |
    |---------|---|---------------| ------- |
    | `id` | `string` | UUIDv4 of the device |
    | `name`| `string | null`| human readable name of the device | limited to 16 characters
    | `deviceTypeId`| `string`| id of the type of the device |
    | `deviceTypeName` | `string` | human readable name of the device type|
    | `manufacturerId`| `string` | id of the manufacturer of the device |
    | `manufacturerName` | `string` | full name of the manufacturer |
    | `manufacturerNameShort` | `string` | colloquial name of the manufacturer |
    | `description` |`string | null` | user defined description of the device |
    | `serialNumber`|`string | null`| serial number of the device | limited to 32 characters
    | `siteId`| `string` | UUIDv4 of the site |
    | `siteName`| `string`| human readable name of the site |
    | `buildingId`| `string` | UUIDv4 of the building |
    | `buildingName`| `string`| human readable name of the building |
    | `roomId`| `string` | UUIDv4 of the room |
    | `roomName`| `string`| human readable name of the room |
    | `rackId`| `string` | UUIDv4 of the rack |
    | `rackName`| `string` | human readable name of the rack |
    | `rackElevation`| `number | null` | `position of the device in RU counted from the bottom of the rack` |
    | `rackPosition`| `FRONT | BACK | LOOSE`| position of the device in the rack |
    | `ports`| | |
    | `portId`| `string` | UUIDv4 of the port |
    | `portTypeId` | `string` | UUIDv4 of the port type |
    | `portTypeName` | `string` | name of the port as labeled on the device |
    | `portTypeDirection` | `"IN" | "OUT" | "BIDI"` | direction of the port type|
    | `connectorId`| `string`| id of the connector |
    | `connectorName`| `string`| human readable name of the connector |
    | `connectorGender`| `"MALE" | "FEMALE" | "HERMA“`| gender of the connector |
    | `connectorIcon`| `string`| name of the associated icon | every icon is available as svg|
    | `moduleSlots`| | |
    | `moduleSlotId`| `string` | UUIDv4 of the module slot |
    | `moduleSlotTypeId` | `string` | UUIDv4 of the module slot type |
    | `moduleSlotTypeName`| `string`| name of the slot as labeled on the device|
    | `module`| | |
    | `moduleId`| `string` | UUIDv4 of the module |
    | `moduleTypeId`| `string`| id of the module type |
    | `moduleTypeName`| `string` | human readable name of the module type |
    | `manufacturerId`| `string` | id of the manufacturer of the module |
    | `manufacturerName` | `string` | full name of the manufacturer |
    | `manufacturerNameShort` | `string` | colloquial name of the manufacturer |
