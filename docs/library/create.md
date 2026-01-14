## Validating your submission using JSON schema

To ensure that your created device or module types meet the minimum technical requirements you can validate them against the following JSON schemas using a schema validator of your choice.

If you don't have any experience, we recommend [jsonschemavalidator.net](https://www.jsonschemavalidator.net/). Just copy and paste the appropriate schema from this page to the left side and your created templates to the right side. The tool will inform you of any errors.

!!! note

    This validation only ensures that basic criteria are met, like correct names of properties. Some simple regex are used to look out for obvious typos or prohibited characters. However, this validation does not check wether the ids referencing other objects like the manufacturer, connector, etc. actually exist.

??? example "JSON schema for device type"

    ```json title="Schema for device types"
        --8<-- "json_schemas/devicetypes/POST_deviceTypes_req.schema.json"
    ```

??? example "JSON schema for module type"

    ```json title="Schema for module types"
        --8<-- "json_schemas/moduletypes/POST_moduleTypes_req.schema.json"
    ```
