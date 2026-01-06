# `api/modules`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `POST`

#### Description

Creates a new module.

#### Path

```HTTP
POST /api/v1/modules
```

#### Query Parameters

None.

#### Request Body

=== "Example"

    ```json
    --8<-- "json_examples/modules/POST_modules_req.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/modules/POST_modules_req.schema.json"
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
    --8<-- "json_examples/modules/POST_modules_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/modules/POST_modules_res.schema.json"
    ```
