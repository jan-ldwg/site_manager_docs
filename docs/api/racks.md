# `api/racks`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns a list of all racks.

#### Path

```HTTP
GET /api/v1/racks
```

#### Query Parameters

| Name     | Type             | Description                                  |
| -------- | ---------------- | -------------------------------------------- |
| `roomId` | `string(UUIDv4)` | (optional) Retrieves only racks in this room |

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
    --8<-- "json_examples/racks/GET_racks_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/racks/GET_racks_res.schema.json"
    ```

## `POST`

#### Description

Creates a new rack.

#### Path

```HTTP
POST /api/v1/racks
```

#### Query Parameters

None.

#### Request Body

=== "Example"

    ```json
    --8<-- "json_examples/racks/POST_racks_req.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/racks/POST_racks_req.schema.json"
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
    --8<-- "json_examples/racks/POST_racks_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/racks/POST_racks_res.schema.json"
    ```
