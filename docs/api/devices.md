# `/api/devices`

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

=== "GET"

    **Description:**

    Returns a list of all devices.

    **Path:**

    ```HTTP
    GET /api/devices
    ```

    **Query Parameters:**

    | Name | Type | Description |
    |------|------|---------------|
    | `rackId` | `string` | (optional) Retrieves only devices in this rack |
    | `roomId`| `string`| (optional) Retrieves only devices in this room |

    **Response:**

    === "Example"
        ```json
        [
            {
                "deviceId": "02d323ae-7282-4521-b810-086337d5d9ee",
                "deviceName": "DSP01",
                "deviceTypeId": "lawo_powercore_rev3",
                "deviceTypeName": "Power Core Rev.3",
                "manufacturerId": "lawo",
                "manufacturerName": "Lawo AG",
                "manufacturerNameShort": "Lawo",
                "deviceDescription": "The main audio dsp for Studio 1.",
                "deviceSerialNumber": "x2025-096",
                "ports": [
                    {
                        "portId": "ae2ee1e7-45f4-4f9a-8f33-b54310e3400b",
                        "portTypeId": "1ae17240-bd09-4c7f-a33a-4f01a3533b73",
                        "portTypeName": "Audio In 1",
                        "portTypeDirection": "IN",
                        "connectorId": "XLR3p_f",
                        "connectorName": "XLR 3pole female",
                        "connectorGender": "FEMALE",
                        "connectorIcon": "XLR3p_f"
                    },
                    ...
                ],
                "moduleSlots": [
                    {
                        "moduleSlotId": "5de0a7a0-2d85-4b77-a134-0b88caf4e56e",
                        "moduleSlotTypeId": "254067f1-d7ba-42a0-8478-f7b3897538d1",
                        "moduleSlotTypeName": "MADI 1",
                        "module": {
                            "moduleId": "e0b5147b-9442-4d01-9548-04504eedc8d9",
                            "moduleTypeId": "lawo_981_60-82",
                            "moduleTypeName": "981/60-82",
                            "manufacturerId": "lawo",
                            "manufacturerName": "Lawo AG",
                            "manufacturerShort": "lawo",
                            "ports": [...],
                            "moduleSlots": [...],
                        }
                    },
                    ...
                ]

            }
        ]
        ```


    === "Schema"
        ```json
        {}
        ```

    **Parameters**

    | Name    | Type | Description | Notes |
    |---------|---|---------------| ------- |
    | `deviceId` | `string` | UUIDv4 of the device |
    | `deviceName`| `string | null`| human readable name of the device | limited to 16 characters
    | `deviceTypeId`| `string`| id of the type of the device |
    | `deviceTypeName` | `string` | human readable name of the device type|
    | `manufacturerId`| `string` | id of the manufacturer of the device |
    | `manufacturerName` | `string` | full name of the manufacturer |
    | `manufacturerNameShort` | `string` | colloquial name of the manufacturer |
    | `deviceDescription` |`string | null` | user defined description of the device |
    | `deviceSerialNumber`|`string | null`| serial number of the device | limited to 32 characters
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




    **Status codes:**

    | Code | Status |
    |------|------------|
    | `200` | Success |
    | `500` | Internal server error |

=== "POST"

    **Description:**
    Creates a new device.

    **Path:**

    ```HTTP
    POST /api/devices
    ```

    **Request body:**

    === "Example"

        ```json
        {
            "deviceTypeId": "blackmagic_Videohub_10x10_12G",
            "rackId": "bc8cf910-0fdc-49ba-8212-f6e8e3a4c90e",
            "deviceName": "Video Router",
            "deviceDescription": "Video router for monitor wall",
            "deviceSerialNumber": "x2025-065"
        }
        ```

    === "Schema"

        ```json
        {
        }
        ```

    **Parameter**

    | Name    | Type | Description | Notes |
    |---------|---|---------------| ------- |
    | `deviceTypeId`| `string`| UUIDv4 of the device type of which to create the device
    | `rackId`| `string` | UUIDv4 of the rack in which the device should be created |
    | `deviceName` | `string`| (optional) human readable name of the device to create|
    | `deviceDescription` |`string | null` | (optional) user defined description of the device |
    | `deviceSerialNumber`|`string | null`| (optional) serial number of the device | limited to 32 characters
    | | | |
    | | | |

    **Antwort:**

    ```json
    {
    "id": 42,
    "name": "New Device",
    "type": "Router",
    "rackUnit": 4
    }
    ```

    **Status codes:**
    | Code | Bedeutung |
    |------|------------|
    | `201` | Created |
    | `400` | Invalid device type |

=== "PATCH"

    **Description:**
    Changes an existing device

    **Path:**

    ```HTTP
    PATCH /api/devices/{id}
    ```

    **Request Body:**

    ```json
     {
        "rackId": "bc8cf910-0fdc-49ba-8212-f6e8e3a4c90e",
        "deviceName": "Video Router",
        "deviceDescription": "Video router for monitor wall",
        "deviceSerialNumber": "x2025-065"
    }
    ```

    **Parameters**

    | Name    | Type | Description | Notes |
    |---------|---|---------------| ------- |
    | `rackId`| `string` | (optional) UUIDv4 of the rack in which the device should be created |
    | `deviceName` | `string`| (optional) human readable name of the device to create|
    | `deviceDescription` |`string | null` | (optional) user defined description of the device |
    | `deviceSerialNumber`|`string | null`| (optional) serial number of the device | limited to 32 characters

    **Response:**

    ```json
    {
        "id": 42,
        "name": "Updated Device Name",
        "type": "Router",
        "rackUnit": 3
    }
    ```

    **Status codes:**
    | Code | Bedeutung |
    |------|------------|
    | `200` | Erfolgreich aktualisiert |
    | `404` | Gerät nicht gefunden |

=== "DELETE"

    **Description:**
    Deletes a device, all its associated modules and the connected cables.

    **Path:**

    ```HTTP
    DELETE /api/devices/{id}
    ```

    **Request Body:**

    ```json
     {
        "rackId": "bc8cf910-0fdc-49ba-8212-f6e8e3a4c90e",
        "deviceName": "Video Router",
        "deviceDescription": "Video router for monitor wall",
        "deviceSerialNumber": "x2025-065"
    }
    ```

    **Parameters**

    | Name    | Type | Description | Notes |
    |---------|---|---------------| ------- |
    | `rackId`| `string` | (optional) UUIDv4 of the rack in which the device should be created |
    | `deviceName` | `string`| (optional) human readable name of the device to create|
    | `deviceDescription` |`string | null` | (optional) user defined description of the device |
    | `deviceSerialNumber`|`string | null`| (optional) serial number of the device | limited to 32 characters

    **Response:**

    ```json
    {
        "id": 42,
        "name": "Updated Device Name",
        "type": "Router",
        "rackUnit": 3
    }
    ```

    **Status codes:**
    | Code | Bedeutung |
    |------|------------|
    | `200` | Erfolgreich aktualisiert |
    | `404` | Gerät nicht gefunden |
