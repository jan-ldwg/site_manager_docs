# `/api/devicetypes`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns a list of all device types.

#### Path

```HTTP
GET /api/v1/devicetypes
```

#### Query Parameters

| Name             | Type                | Description                                                 |     |
| ---------------- | ------------------- | ----------------------------------------------------------- | --- |
| `manufacturerId` | `string / string[]` | (optional) Retrieves only devices from this manufacturer(s) |     |

See the [paragraph about query parameters](overview.md) for detailed usage.

#### Request Body

None.

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Success               |
| `401` | Unauthorized          |
| `500` | Internal Server Error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/deviceTypes/GET_deviceTypes_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/deviceTypes/GET_deviceTypes_res.schema.json"
    ```

## `POST`

#### Description

Creates a new device type.

#### Path

```HTTP
POST /api/v1/devicetypes
```

#### Query Parameters

None.

#### Request Body

=== "Example"

    ```json
    --8<-- "json_examples/deviceTypes/POST_devicetypes_req.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/deviceTypes/POST_deviceTypes_req.schema.json"
    ```

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `201` | Created               |
| `401` | Unauthorized          |
| `500` | Internal Server Error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/deviceTypes/POST_deviceTypes_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/deviceTypes/POST_deviceTypes_res.schema.json"
    ```
