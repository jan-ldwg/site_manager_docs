# `/api/manufacturers`

!!! success "Up to date"

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

## `GET`

#### Description

Returns a list of all manufacturers.

#### Path

```HTTP
GET /api/v1/manufacturers
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
| `500` | Internal server error |

#### Response Body

=== "Example"

    ```json
    --8<-- "json_examples/manufacturers/GET_manufacturers_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/manufacturers/GET_manufacturers_res.schema.json"
    ```

| Name        | Type         | Description                             | Notes |
| ----------- | ------------ | --------------------------------------- | ----- |
| `id`        | `string(32)` | id of the manufacturer                  |       |
| `name`      | `string`     | human readable name of the manufacturer |       |
| `nameShort` | `string(16)` | abbreviated version of the name         |       |

## `POST`

#### Description

Creates a new manufacturer.

#### Path

```HTTP
POST /api/v1/manufacturers
```

#### Query Parameters

None.

#### Request Body

=== "Example"

    ```json
    --8<-- "json_examples/manufacturers/POST_manufacturers_req.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/manufacturers/POST_manufacturers_req.schema.json"
    ```

| Name        | Type         | Description                       | Notes |
| ----------- | ------------ | --------------------------------- | ----- |
| `id`        | `string(32)` | id of the manufacturer            |       |
| `name`      | `string`     | human readable name of the device |       |
| `nameShort` | `string(16)` | abbreviated version of the name   |       |

#### Status Codes

| Code  | Status                |
| ----- | --------------------- |
| `201` | Created               |
| `401` | Unauthorized          |
| `409` | Conflict              |
| `500` | Internal Server Error |

**Response Body:**

=== "Example"

    ```json
    --8<-- "json_examples/manufacturers/POST_manufacturers_res.json"
    ```

=== "Schema"

    ```json
    --8<-- "json_schemas/manufacturers/POST_manufacturers_res.schema.json"
    ```

| Name        | Type         | Description                       | Notes |
| ----------- | ------------ | --------------------------------- | ----- |
| `id`        | `string(32)` | id of the manufacturer            |       |
| `name`      | `string`     | human readable name of the device |       |
| `nameShort` | `string(16)` | abbreviated version of the name   |       |
