# `/api/cables/{cableId}`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns the cable.

#### Path

```HTTP
GET /api/v1/cables/{cableId}
```

#### Query Parameters

None.

#### Request Body

None.

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Success               |
| `404` | Not Found             |
| `500` | Internal Server Error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/cables/POST_cables_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/cables/GET_cable_res.schema.json"
    ```

## `PATCH`

#### Description

Changes an existing cable.

#### Path

```HTTP
PATCH /api/v1/cables/{cableId}
```

#### Query Parameters

None.

#### Request Body

=== "Example"

    ```json
    --8<-- "json_examples/cables/PATCH_cables_req.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/cables/PATCH_cables_req.schema.json"
    ```

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Success               |
| `404` | Not found             |
| `500` | Internal Server Error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/cables/POST_cables_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/cables/PATCH_cables_res.schema.json"
    ```

## `DELETE`

#### Description

Deletes a cable.

#### Path

```HTTP
DELETE /api/v1/cables/{cableId}
```

#### Query Parameters

None.

#### Request Body

None.

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `200` | Success               |
| `404` | Not found             |
| `500` | Internal Server Error |

#### Response Body

None.
