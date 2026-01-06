# `api/modules/{moduleId}`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns the module.

#### Path

```HTTP
GET /api/v1/modules/{moduleId}
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
    --8<-- "json_examples/modules/POST_modules_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/modules/GET_module_res.schema.json"
    ```

## `DELETE`

#### Description

Deletes a module.

#### Path

```HTTP
DELETE /api/v1/modules/{moduleId}
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
