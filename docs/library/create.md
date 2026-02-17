## Validating your submission using JSON schema

To ensure that your created device or module types meet the minimum technical requirements you can validate them against the following JSON schemas using a schema validator of your choice.

If you don't have any experience, we recommend [jsonschemavalidator.net](https://www.jsonschemavalidator.net/). Just copy and paste the appropriate schema from this page to the left side and your created templates to the right side. The tool will inform you of any errors.

!!! note

    This validation only ensures that basic criteria are met, like correct names of properties. Some simple regex are used to look out for obvious typos or prohibited characters. However, this validation does not check wether the ids referencing other objects like the manufacturer, connector, etc. actually exist.

??? example "JSON schema for device type"

    ```json title="Schema for device types"
        --8<-- "json_schemas/deviceTypes/POST_deviceTypes_req.schema.json"
    ```

??? example "JSON schema for module type"

    ```json title="Schema for module types"
        --8<-- "json_schemas/moduleTypes/POST_moduleTypes_req.schema.json"
    ```

## Modeling a device

### Consumer video standards

When modeling consumer video ports like HDMI, DisplayPort, etc. care should be take to correctly model the compatibility of the ports.

site_manager does not model the different versions of these standards (e.g HDMI 1.4, HDMI 2.0, DP 1.4, DP 2.0) as these specs are always backwards compatible with all previous generations. Features like HDCP, eARC, etc. and supported resolutions are also not modeled as this would get to complex and documentation for most devices is sparse when it comes to these details.

In general the following matrix describes compatibility between the different standards.

|       | VGA | DVI-A | DVI-D | DVI-I | HDMI   | DP  |
| ----- | --- | ----- | ----- | ----- | ------ | --- |
| VGA   | x   | x     |       | x     |        |     |
| DVI-A | x   | x     |       | x     |        |     |
| DVI-D |     |       | x     | x     | x [^1] |     |
| DVI-I | x   | x     | x     | x     | x [^2] |     |
| HDMI  |     |       | x     | x     | x      |     |
| DP    |     |       |       |       | x [^3] | x   |

In general it is fine if older standards like DVI are not modeled completely for every device. site_manager is set up in a way that the templates can always be updated later if it should become necessary to model this precisely.

[^1]: without audio or HDCP

[^2]: without audio or HDCP

[^3]: only with DP++
