# `api/rooms/{roomId}`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns the room.

#### Path

```HTTP
GET /api/v1/rooms/{roomId}
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
    --8<-- "json_examples/rooms/POST_rooms_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/rooms/GET_room_res.schema.json"
    ```

## `DELETE`

#### Description

Deletes a room.

#### Path

```HTTP
DELETE /api/v1/rooms/{roomId}
```

#### Query Parameters

None.

#### Request Body

None.

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Ok                    |
| `401` | Unauthorized          |
| `500` | Internal Server Error |

#### Response Body

None.
