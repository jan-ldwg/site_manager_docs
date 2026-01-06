# `/api/buildings/{buildingId}`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns the building.

#### Path

```HTTP
GET /api/v1/buildings/{buildingId}
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
    --8<-- "json_examples/buildings/POST_buildings_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/buildings/GET_building_res.schema.json"
    ```

## `DELETE`

#### Description

Deletes a building.

#### Path

```HTTP
DELETE /api/v1/buildings/{buildingId}
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
