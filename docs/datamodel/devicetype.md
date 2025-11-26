Device types can be thought of as templates that are used to create instances of devices. In contrast to some other applications (e.g. Netbox) site_manager does not duplicate information from the device type into each device instance upon creation, but instead retrieves general information for a device by querying the device type. This means that a device type may only be deleted from the database when there are no devices of this type in the database. This also means that some information in the device type can be changed and all existing instances of this device will be updated on future queries.

!!! note

    The number of ports and module slots can not be changed afterwards.
