## Understanding devices and device types

Device types can be thought of as templates that are used to create instances of devices. They represent one specific model by a manufacturer. In contrast to some other applications (e.g. Netbox) site_manager does not duplicate information from the device type into each device instance upon creation, but instead retrieves general information for a device by querying the device type. This means that a device type may only be deleted from the database when there are no devices of this type in the database. This also means that some information in the device type can be changed and all existing instances of this device will be updated on future queries.

!!! note

    The number of ports or module slots can not be changed afterwards.

A device can have a number of ports to which cables can be connected and module slots which can host modules to expand the functionality and connectivity of the device.

## Understanding locations

Every device in site_manager has to be assigned a physical location. Locations are managed as a hierarchy.

- Sites are the top level of the hierarchy. They represent distinct locations with vast geographic distances between them. Therefore cables can not run between sites.
- Buildings and rooms are just what it sounds like. Their main use is to better organize the generated diagrams. There are no restrictions for cables running between different buildings or rooms.
- Racks are the lowest level in the hierarchy. They do not have to represent equipment racks but can also represent other places where devices are mounted like a table or a monitor wall. Devices have to be assigned to a rack.
