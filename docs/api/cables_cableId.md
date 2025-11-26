# `/api/cables`

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

=== "GET"

    **Description:**

    Returns the cables.

    **Path:**

    ```HTTP
    GET /api/v1/cables/{cableid}
    ```

    **Query Parameters:**

    None.

    **Request Body:**

    None.

    **Status Codes:**

    | Code  | Status                |
    | ----- | --------------------- |
    | `200` | Success               |
    | `404` | Cable not found       |
    | `500` | Internal server error |

    **Response Body:**

    === "Example"
        ```json
        --8<-- "json_examples/POST_cables_res.json"
        ```

    === "Schema"

    | Name                   | Type                    | Description                                     | Notes            |
    | ---------------------- | ----------------------- | ----------------------------------------------- | ---------------- |
    | `id`                   | `string`                | id of the cable                                 |                  |
    | `number`               | `string / null`         | number of the cable as printed on it            |                  |
    | `length`               | `number / null`         | length of the cable in meters                   |                  |
    | `startPortId`          | `string`                | UUIDv4 of the start port                        |                  |
    | `startPortName`        | `string`                | name of the start port as printed on the device |                  |
    | `startConnectorId`     | `string / null`         | id of the cable connector at the start side     |                  |
    | `startConnectorName`   | `string / null`         | name of the cable connector at the start side   |                  |
    | `startConnectorGender` | `MALE / FEMALE / HERMA` | gender of the cable connector at the start side |                  |
    | `startConnectorIcon`   | `string`                | icon of the cable connector at the start side   | available as svg |
    | `startConnectorColor`  | `string / null`         | color of the cable connector at the start side  |                  |
    | `startDeviceId`        | `string`                | UUIDv4 of the device on the start side          |                  |
    | `startDeviceName`      | `string`                | name of the device on the start side            |                  |
    | `startRackId`          | `string`                | UUIDv4 of the rack on the start side            |                  |
    | `startRackName`        | `string`                | name of the rack on the start side              |                  |
    | `endPortId`            | `string`                | UUIDv4 of the end port                          |                  |
    | `endPortName`          | `string`                | name of the end port as printed on the device   |                  |
    | `endConnectorId`       | `string / null`         | id of the cable connector at the end side       |                  |
    | `endConnectorName`     | `string / null`         | name of the cable connector at the end side     |                  |
    | `endConnectorGender`   | `MALE / FEMALE / HERMA` | gender of the cable connector at the end side   |                  |
    | `endConnectorIcon`     | `string`                | icon of the cable connector at the end side     | available as svg |
    | `endConnectorColor`    | `string / null`         | color of the cable connector at the end side    |                  |
    | `endDeviceId`          | `string`                | UUIDv4 of the device on the end side            |                  |
    | `endDeviceName`        | `string`                | name of the device on the end side              |                  |
    | `endRackId`            | `string`                | UUIDv4 of the rack on the end side              |                  |
    | `endRackName`          | `string`                | name of the rack on the end side                |                  |

=== "PATCH"

    **Description:**

    Changes an existing cable.

    **Path:**

    ```HTTP
    PATCH /api/v1/cables/{cableid}
    ```

    **Query Parameters:**

    None.

     **Request Body:**

    === "Example"

        ```json
        --8<-- "json_examples/PATCH_devices_device_req.json"
        ```
    === "Schema"

        ```json
        {}
        ```
    | Name                  | Type            | Description                                               |
    | --------------------- | --------------- | --------------------------------------------------------- |
    | `number`              | `string / null` | number of the cable as printed on it                      |
    | `length`              | `number / null` | (optional) length of the cable in meters                  |
    | `startConnector`      | `string / null` | (optional) id of the cable connector at the start side    |
    | `startConnectorColor` | `string / null` | (optional) color of the cable connector at the start side |
    | `endConnector`        | `string / null` | (optional) id of the cable connector at the end side      |
    | `endConnectorColor`   | `string / null` | (optional) color of the cable connector at the end side   |

    **Status Codes:**

    | Code  | Status                |
    | ----- | --------------------- |
    | `200` | Success               |
    | `404` | Cable not found       |
    | `500` | Internal server error |

    **Response Body:**

    === "Example"
        ```json
        --8<-- "json_examples/POST_cables_res.json"
        ```

    === "Schema"
        ```json
        {}
        ```

    | Name                   | Type                    | Description                                     | Notes            |
    | ---------------------- | ----------------------- | ----------------------------------------------- | ---------------- |
    | `id`                   | `string`                | id of the cable                                 |                  |
    | `number`               | `string / null`         | number of the cable as printed on it            |                  |
    | `length`               | `number / null`         | length of the cable in meters                   |                  |
    | `startPortId`          | `string`                | UUIDv4 of the start port                        |                  |
    | `startPortName`        | `string`                | name of the start port as printed on the device |                  |
    | `startConnectorId`     | `string / null`         | id of the cable connector at the start side     |                  |
    | `startConnectorName`   | `string / null`         | name of the cable connector at the start side   |                  |
    | `startConnectorGender` | `MALE / FEMALE / HERMA` | gender of the cable connector at the start side |                  |
    | `startConnectorIcon`   | `string`                | icon of the cable connector at the start side   | available as svg |
    | `startConnectorColor`  | `string / null`         | color of the cable connector at the start side  |                  |
    | `startDeviceId`        | `string`                | UUIDv4 of the device on the start side          |                  |
    | `startDeviceName`      | `string`                | name of the device on the start side            |                  |
    | `startRackId`          | `string`                | UUIDv4 of the rack on the start side            |                  |
    | `startRackName`        | `string`                | name of the rack on the start side              |                  |
    | `endPortId`            | `string`                | UUIDv4 of the end port                          |                  |
    | `endPortName`          | `string`                | name of the end port as printed on the device   |                  |
    | `endConnectorId`       | `string / null`         | id of the cable connector at the end side       |                  |
    | `endConnectorName`     | `string / null`         | name of the cable connector at the end side     |                  |
    | `endConnectorGender`   | `MALE / FEMALE / HERMA` | gender of the cable connector at the end side   |                  |
    | `endConnectorIcon`     | `string`                | icon of the cable connector at the end side     | available as svg |
    | `endConnectorColor`    | `string / null`         | color of the cable connector at the end side    |                  |
    | `endDeviceId`          | `string`                | UUIDv4 of the device on the end side            |                  |
    | `endDeviceName`        | `string`                | name of the device on the end side              |                  |
    | `endRackId`            | `string`                | UUIDv4 of the rack on the end side              |                  |
    | `endRackName`          | `string`                | name of the rack on the end side                |                  |

=== "DELETE"

    **Description:**

    Deletes a cable.

    **Path:**

    ```HTTP
    DELETE /api/v1/cables/{cableid}
    ```

    **Query Parameters:**

    None.

    **Request Body:**

    None.

    **Status Codes:**

    | Code  | Status                |
    | ----- | --------------------- |
    | `200` | Success               |
    | `404` | Cable not found       |
    | `500` | Internal server error |

    **Response Body:**

    === "Example"

        ```json
        {
            "deletedCable": "c0ec2b68-94a7-421b-9dfe-10619f1b125a"
        }
        ```

    === "Schema"

        ```json
        {}
        ```

    | Name           | Type     | Description                 |
    | -------------- | -------- | --------------------------- |
    | `deletedCable` | `string` | UUIDv4 of the deleted cable |
