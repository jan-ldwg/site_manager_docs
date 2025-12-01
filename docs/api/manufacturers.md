# `/api/manufacturers`

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

=== "GET"

    **Description:**

    Returns a list of all manufacturers.

    **Path:**

    ```HTTP
    GET /api/v1/manufacturers
    ```

    **Query Parameters:**

    None.

    **Request Body:**

    None.

    **Status Codes:**

    | Code | Status |
    |------|------------|
    | `200` | Success |
    | `500` | Internal server error |

    **Response Body:**

    === "Example"
        ```json
        --8<-- "json_examples/GET_manufacturers_res.json"
        ```

    === "Schema"
        ```json
        {}
        ```

    | Name        | Type          | Description                       | Notes |
    | ----------- | ------------- | --------------------------------- | ----- |
    | `id`        | `string(32)`  | id of the manufacturer            |       |
    | `name`      | `string`      | human readable name of the device |       |
    | `nameShort` | `string(16)`  | abbreviated version of the name   |       |
    | `email`     | `string/null` | email to contact the manufacturer |       |

=== "POST"

    **Description:**

    Creates a new manufacturer.

    **Path:**

    ```HTTP
    POST /api/v1/manufacturers
    ```

    **Query Parameters:**

    None.

    **Request Body:**

    === "Example"
        ```json
        --8<-- "json_examples/POST_manufacturers_req.json"
        ```

    === "Schema"
        ```json
        {}
        ```

    | Name        | Type          | Description                                  | Notes |
    | ----------- | ------------- | -------------------------------------------- | ----- |
    | `id`        | `string(32)`  | id of the manufacturer                       |       |
    | `name`      | `string`      | human readable name of the device            |       |
    | `nameShort` | `string(16)`  | abbreviated version of the name              |       |
    | `email?`    | `string/null` | (optional) email to contact the manufacturer |       |

     **Status Codes:**

    | Code  | Status                |
    | ----- | --------------------- |
    | `201` | Created               |
    | `409` | Conflict              |
    | `500` | Internal Server Error |

    **Response Body:**

    === "Example"
        ```json
        --8<-- "json_examples/POST_manufacturers_res.json"
        ```

    === "Schema"
        ```json
        {}
        ```

    | Name        | Type          | Description                                  | Notes |
    | ----------- | ------------- | -------------------------------------------- | ----- |
    | `id`        | `string(32)`  | id of the manufacturer                       |       |
    | `name`      | `string`      | human readable name of the device            |       |
    | `nameShort` | `string(16)`  | abbreviated version of the name              |       |
    | `email`     | `string/null` | (optional) email to contact the manufacturer |       |
