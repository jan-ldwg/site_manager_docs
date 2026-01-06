# `/api/devicetypes/{deviceTypeId}`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns the device type.

#### Path

```HTTP
GET /api/v1/devicetypes/{deviceTypeId}
```

#### Query Parameters

None.

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
    --8<-- "json_examples/deviceTypes/POST_deviceTypes_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/deviceTypes/GET_deviceType_res.schema.json"
    ```

## `DELETE`

#### Description

Deletes the device type.

#### Path

```HTTP
DELETE /api/v1/devicetypes/{deviceTypeId}
```

#### Query Parameters

None.

#### Request Body

None.

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Success               |
| `401` | Unauthorized          |
| `500` | Internal Server Error |

#### Response Body

None.
