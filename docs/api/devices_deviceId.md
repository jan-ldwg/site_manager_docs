# `/api/devices`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns the device.

#### Path

```HTTP
GET /api/v1/devices/{deviceId}
```

#### Query Parameters

None.

#### Request Body

None.

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Success               |
| `400` | Bad Request           |
| `401` | Unauthorized          |
| `404` | Not Found             |
| `500` | Internal Server Error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/devices/POST_devices_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/devices/GET_device_res.schema.json"
    ```

## `PATCH`

#### Description

Updates values of an existing device.

#### Path

```HTTP
PATCH /api/v1/devices/{deviceId}
```

#### Query Parameters

None.

#### Request Body

=== "Example"

    ```json
    --8<-- "json_examples/devices/PATCH_devices_req.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/devices/PATCH_device_req.schema.json"
    ```

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Success               |
| `400` | Bad Request           |
| `401` | Unauthorized          |
| `404` | Not Found             |
| `500` | Internal Server Error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/devices/POST_devices_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/devices/PATCH_device_res.schema.json"
    ```

## `DELETE`

#### Description

Deletes a device, all its associated modules and the connected cables.

#### Path

```HTTP
DELETE /api/v1/devices/{deviceId}
```

#### Query Parameters

None.

#### Request Body

None.

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Success               |
| `400` | Bad Request           |
| `401` | Unauthorized          |
| `404` | Not Found             |
| `500` | Internal Server Error |

#### Response Body

None.
