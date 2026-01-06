# `/api/manufacturers/{manufacturerId}`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns the manufacturer.

#### Path

```HTTP
GET /api/v1/manufacturers/{manufacturerId}
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
| `404` | Not Found             |
| `500` | Internal Server Error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/manufacturers/POST_manufacturers_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/manufacturers/GET_manufacturer_res.schema.json"
    ```

| Name        | Type         | Description                       | Notes |
| ----------- | ------------ | --------------------------------- | ----- |
| `id`        | `string(32)` | id of the manufacturer            |       |
| `name`      | `string`     | human readable name of the device |       |
| `nameShort` | `string(16)` | abbreviated version of the name   |       |

## `DELETE`

#### Description

Deletes the manufacturer.

#### Path

```HTTP
DELETE /api/v1/manufacturers/{manufacturerId}
```

#### Query Parameters

None.

#### Request Body

None.

#### Status Codes

| Code  | Meaning               |
| ----- | --------------------- |
| `200` | Ok                    |
| `401` | Unauthorized          |
| `404` | Not Found             |
| `500` | Internal Server Error |

#### Response Body

None.
