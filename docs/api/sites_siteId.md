# `/api/manufacturers/{id}`

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns the site.

#### Path

```HTTP
GET /api/v1/sites/{id}
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
    --8<-- "json_examples/POST_sites_res.json"
    ```

=== "Schema"

    ```json
    {}
    ```

| Name   | Type             | Description                     | Notes |
| ------ | ---------------- | ------------------------------- | ----- |
| `id`   | `string(UUIDv4)` | id of the site                  |       |
| `name` | `string`         | human readable name of the site |       |

## `DELETE`

#### Description

Deletes the site.

#### Path

```HTTP
DELETE /api/v1/site/{id}
```

#### Query Parameters

None.

#### Request Body

None.

#### Status Codes

| Code  | Meaning               |
| ----- | --------------------- |
| `200` | Ok                    |
| `400` | Bad Request           |
| `401` | Unauthorized          |
| `404` | Not Found             |
| `500` | Internal Server Error |

#### Response Body

None.
