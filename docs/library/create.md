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

### MADI standards

MADI (Multichannel Audio Digital Interface) can be run over a variety of physical layers. The most common are 75 Ohm coaxial cable, single mode or multi mode fiber and twisted pair cabling.

Single mode fiber is almost always 1310 nm, same as SDI. For multi mode fiber it is more complicated. The standard calls for 1300 nm over 62.5 micrometer fiber, same as FDDI. However, most manufacturers seem to have switched to 1310 nm over 50 micrometer fiber, as is common in modern ethernet. In theory both variants should be compatible, so site_manager does not differentiate them. 850 nm is also sometimes used, which is not compatible and therefore its own signal type. CWDM optics are also available from some vendors.

### LC couplers

LC couplers as used in keystone panels are often differentiated with different colors for different fiber types and polishes.

| Type    | Polish | Color   |
| ------- | ------ | ------- |
| OS2     | PC/UPC | blue    |
| OS2     | APC    | green   |
| OM1/OM2 |        | beige   |
| OM3     |        | aqua    |
| OM4     |        | violett |
| OM5     |        | lime    |

However, mechanically these couplers are all the same, as they include no optical components at all. The connection between fibers is simply made by aligning the ferrules, which are always the same diameter.

site_manager still differentiates these different couplers and will not let you use a OS2 APC coupler to connect OM3 fiber for example. This decision was made since there is no other mechanism in site_manager to ensure that compatible connectors are used on both side of the coupler.

Neutrik only has one SKU for their OpticalCON Duo couplers, however, site_manager models these as three different module types to allow for better compatibility checks.

### Euroblock connectors

Euroblock connectors (also know as Phoenix connectors) are popular in installed AV for audio and control wiring and are also becoming more popular in broadcast devices for GPIO and serial connections. There are many different styles of these connectors, mostly differentiated by their pitch and number of positions/contacts. While a wide range of these connectors exists, the most commonly used ones are 3.5mm, 3.81mm and 5.08mm pitch. Unfortunately most manufacturers do not specify the connector for their equipment. Therefore site_manager also supports an unknown pitch which should be used if the correct pitch can not be determined with absolute certainty.

| Pitch   | Example part from Phoenix | Id            |
| ------- | ------------------------- | ------------- |
| 3.5mm   | MC 1,5/ 2-ST-3,5          | EURO_35_2p_f  |
| 3.81mm  | MC 1,5/ 2-ST-3,81         | EURO_381_2p_f |
| 5.08mm  | MSTB 2,5/ 2-ST-5,08       | EURO_508_2p_f |
| unknown | n/a                       | EURO_XX_2p_f  |
