# `/api/sites`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns a list of all sites.

#### Path

```HTTP
GET /api/v1/sites
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
    --8<-- "json_examples/sites/GET_sites_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/sites/GET_sites_res.schema.json"
    ```

| Name   | Type             | Description                     |
| ------ | ---------------- | ------------------------------- |
| `id`   | `string(UUIDv4)` | id of the site                  |
| `name` | `string`         | human readable name of the site |

## `POST`

#### Description

Creates a new site.

#### Path

```HTTP
POST /api/v1/sites
```

#### Query Parameters

None.

#### Request Body

=== "Example"

    ```json
    --8<-- "json_examples/sites/POST_sites_req.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/sites/POST_sites_req.schema.json"
    ```

| Name   | Type     | Description                     | Notes |
| ------ | -------- | ------------------------------- | ----- |
| `name` | `string` | human readable name of the site |       |

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `201` | Created               |
| `401` | Unauthorized          |
| `500` | Internal Server Error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/sites/POST_sites_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/sites/POST_sites_res.schema.json"
    ```

| Name   | Type             | Description                     | Notes |
| ------ | ---------------- | ------------------------------- | ----- |
| `id`   | `string(UUIDv4)` | id of the site                  |       |
| `name` | `string`         | human readable name of the site |       |
