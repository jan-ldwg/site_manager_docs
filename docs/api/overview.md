# Overview

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

    Currently missing features:

    - general improvements to structure
    - unified naming of properties and parameters
    - search params
    - authentication and authorization

site_manager is designed to be flexible and easy to integrate into overarching workflows. To allow connection to external systems, a fully featured API is available. This API provides endpoints to take every action that is available in the GUI. In fact all interaction between the server and the GUI is handled by the API.

## General design

The API follows the traditional REST paradigm. Access is possible via HTTP using tools such as [curl](https://www.curl.se), [Postman](https://www.postman.com) or your favorite scripting language. The base path for all API endpoints is `{YourSiteMangerInstance}/api/v1`.

These 5 methods are supported. Note that not every endpoint supports every method. See the documentation of the individual endpoints to learn about there supported methods.

| Method | Usage                                                                                                    |
| ------ | -------------------------------------------------------------------------------------------------------- |
| GET    | read one or many database objects                                                                        |
| POST   | create a new database object                                                                             |
| PATCH  | update an existing object in the database                                                                |
| PUT    | replace an existing object. The existing object will be deleted and new one will be created in its place |
| DELETE | delete an object from the database                                                                       |

`POST`, `PATCH` and `PUT` return the full object on success.

## Authentication

site_manager uses cookies for authentication. Every request to protected api endpoints (e.g. everything except `api/auth/sign-in/email`) has to include a valid session cookie. The cookie is called `site-manager.session_data`.

To make direct requests to the server without using the frontend authentication is required. This can done by sending the email and password to `api/auth/sign-in/email`. The api will respond with the cookie, which can then be sent with all future requests.

!!! warning

    Better Auth is strict when it comes to requests send to `api/auth/*`. Make sure to set the origin header!

## About this documentation

Optional parameters in the request body are marked with an `?` at the end of their key. This has to be omitted in the request.
