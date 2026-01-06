# `/api/devices`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns a list of all devices.

#### Path

```HTTP
GET /api/v1/devices
```

#### Query Parameters

| Name         | Type             | Description                                        |
| ------------ | ---------------- | -------------------------------------------------- |
| `rackId`     | `string(UUIDv4)` | (optional) Retrieves only devices in this rack     |
| `roomId`     | `string(UUIDv4)` | (optional) Retrieves only devices in this room     |
| `buildingId` | `string(UUIDv4)` | (optional) Retrieves only devices in this building |
| `siteId`     | `string(UUIDv4)` | (optional) Retrieves only devices at this site     |

See the [paragraph about query parameters](overview.md) for detailed usage.

#### Request Body

None.

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Success               |
| `400` | Bad Request           |
| `401` | Unauthorized          |
| `500` | Internal Server Error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/devices/GET_devices_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/devices/GET_devices_res.schema.json"
    ```

| Name                    | Type                          | Description                               |
| ----------------------- | ----------------------------- | ----------------------------------------- |
| `id`                    | `string(UUIDv4)`              | UUIDv4 of the device                      |
| `name`                  | `string(16) / null`           | human readable name of the device         |
| `deviceTypeId`          | `string(48)`                  | id of the type of the device              |
| `deviceTypeName`        | `string(256)`                 | human readable name of the device type    |
| `manufacturerId`        | `string(16)`                  | id of the manufacturer of the device      |
| `manufacturerName`      | `string`                      | full name of the manufacturer             |
| `manufacturerNameShort` | `string`                      | colloquial name of the manufacturer       |
| `description`           | `string / null`               | user defined description of the device    |
| `serialNumber`          | `string(32) / null`           | serial number of the device               |
| `siteId`                | `string(UUIDv4)`              | UUIDv4 of the site                        |
| `siteName`              | `string`                      | human readable name of the site           |
| `buildingId`            | `string(UUIDv4)`              | UUIDv4 of the building                    |
| `buildingName`          | `string`                      | human readable name of the building       |
| `roomId`                | `string(UUIDv4)`              | UUIDv4 of the room                        |
| `roomName`              | `string`                      | human readable name of the room           |
| `rackId`                | `string(UUIDv4)`              | UUIDv4 of the rack                        |
| `rackName`              | `string`                      | human readable name of the rack           |
| `ports`                 |                               |                                           |
| `id`                    | `string(UUIDv4)`              | UUIDv4 of the port                        |
| `portTypeId`            | `string(UUIDv4)`              | UUIDv4 of the port type                   |
| `portTypeName`          | `string`                      | name of the port as labeled on the device |
| `portTypeDirection`     | `DIRECTION`                   | direction of the port type                |
| `connectorId`           | `string`                      | id of the connector                       |
| `connectorName`         | `string`                      | human readable name of the connector      |
| `connectorGender`       | `"MALE" / "FEMALE" / "HERMA“` | gender of the connector                   |
| `connectorIcon`         | `string`                      | name of the associated icon               |
| `moduleSlots`           |                               |                                           |
| `id`                    | `string(UUIDv4)`              | UUIDv4 of the module slot                 |
| `moduleSlotTypeId`      | `string(UUIDv4)`              | UUIDv4 of the module slot type            |
| `moduleSlotTypeName`    | `string`                      | name of the slot as labeled on the device |
| `module`                |                               |                                           |
| `id`                    | `string(UUIDv4)`              | UUIDv4 of the module                      |
| `moduleTypeId`          | `string`                      | id of the module type                     |
| `moduleTypeName`        | `string`                      | human readable name of the module type    |
| `manufacturerId`        | `string(16)`                  | id of the manufacturer of the module      |
| `manufacturerName`      | `string`                      | full name of the manufacturer             |
| `manufacturerNameShort` | `string`                      | colloquial name of the manufacturer       |
| `ports`                 |                               |                                           |
| `moduleSlots`           |                               |                                           |

## `POST`

#### Description

Creates a new device.

#### Path

```HTTP
POST /api/v1/devices
```

#### Query Parameters

None.

#### Request Body

=== "Example"

    ```json
    --8<-- "json_examples/devices/POST_devices_req.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/devices/POST_devices_req.schema.json"
    ```

| Name           | Type                | Description                                              |
| -------------- | ------------------- | -------------------------------------------------------- |
| `deviceTypeId` | `string`            | id of the device type of which to create the device      |
| `rackId`       | `string(UUIDv4)`    | UUIDv4 of the rack in which the device should be created |
| `name`         | `string / null`     | (optional) human readable name of the device to create   |
| `description`  | `string / null`     | (optional) user defined description of the device        |
| `serialNumber` | `string(32) / null` | (optional) serial number of the device                   |

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `201` | Created               |
| `400` | Bad Request           |
| `401` | Unauthorized          |
| `500` | Internal Server Error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/devices/POST_devices_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/devices/POST_devices_res.schema.json"
    ```
