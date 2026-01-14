# Overview

site_manager uses a curated library of device types, manufacturers, signal types and connectors. These are not packaged into the container image, but are instead automatically loaded from the GitHub repository on startup and written into the database. site_manager also continuously looks for new templates and automatically loads them into the database.

The update process is controlled by the two environment variables `TEMPLATE_URL` and `REFETCH_INTERVAL`. By default `TEMPLATE_URL`points to the [site_manager_templates repo](https://github.com/jan-ldwg/site_manager_templates). The `REFETCH_INTERVAL` is set to 10 minutes. However, HTTP ETag is used to only download and go through the update process if there are changes to the repo. Therefore the performance gain from reducing this interval is negligible.

If you need templates that are not currently available you can open a new issue [here](https://github.com/jan-ldwg/site_manager_templates/issues/new?template=new-device-or-module-type.md). Alternatively you can [create new templates](create.md) yourself. After that you can either [contribute these to the GitHub repo](contribute.md), load them [into your local database via the API]() or [set up your own repo]().

!!! warning

    We generally recommend to only go through the official GitHub repo to ensure that you do not run into compatibility issues in the future.
