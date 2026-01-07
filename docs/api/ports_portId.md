# `api/ports/{portId}`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns the port.

#### Path

```HTTP
GET /api/v1/ports/{portId}
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
    --8<-- "json_examples/ports/GET_port_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/ports/GET_port_res.schema.json"
    ```
