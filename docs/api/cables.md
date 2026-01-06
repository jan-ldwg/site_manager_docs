# `/api/cables`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns a list of all cables.

#### Path

```HTTP
GET /api/v1/cables
```

#### Query Parameters

| Name              | Type                | Description                                                |
| ----------------- | ------------------- | ---------------------------------------------------------- |
| `startRackId`     | `string / string[]` | (optional) Retrieves only cables starting in this rack     |
| `startRoomId`     | `string / string[]` | (optional) Retrieves only cables starting room             |
| `startBuildingId` | `string / string[]` | (optional) Retrieves only cables starting in this building |
| `endRackId`       | `string / string[]` | (optional) Retrieves only cables ending in this rack       |
| `endRoomId`       | `string / string[]` | (optional) Retrieves only cables ending room               |
| `endBuildingId`   | `string / string[]` | (optional) Retrieves only cables ending in this building   |

See the [paragraph about query parameters](overview.md) for detailed usage.

#### Request Body

None.

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Success               |
| `500` | Internal Server Error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/cables/GET_cables_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/cables/GET_cables_res.schema.json"
    ```

## `POST`

#### Description

Creates a new cable.

#### Path

```HTTP
POST /api/v1/cables
```

#### Query Parameters

None.

#### Request Body

=== "Example"

    ```json
    --8<-- "json_examples/cables/POST_cables_req.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/cables/POST_cables_req.schema.json"
    ```

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Success               |
| `500` | Internal server error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/cables/POST_cables_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/cables/POST_cables_res.schema.json"
    ```
