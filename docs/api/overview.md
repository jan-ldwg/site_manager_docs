# Overview

!!! warning

    The api is still under active development. The documentation might not reflect the current implementation. The documentation represents the current end goal for the v1.0 release. Feel free to leave feedback in the site_manager_server repo.

    Currently missing features:

    - general improvements to structure
    - unified naming of properties and parameters
    - search params
    - authentication and authorization

site_manager is designed to be flexible and easy to integrate into overarching workflows. To allow connection to external systems, a fully featured API is available. This API provides endpoints to take every action that is available in the GUI.

## General design

The API follows the traditional REST paradigm. Access is possible via HTTP using tools such as [curl](https://www.curl.se), [Postman](https://www.postman.com) or your favorite scripting language. The base path for all API endpoints is `{YourSiteMangerInstance}/api/v1`.

These 5 methods are supported. Note that not every endpoint supports every method. See the documentation of the individual endpoints to learn about their supported methods.

| Method | Usage                                                                                                    |
| ------ | -------------------------------------------------------------------------------------------------------- |
| GET    | read one or many database objects                                                                        |
| POST   | create a new database object                                                                             |
| PATCH  | update an existing object in the database                                                                |
| PUT    | replace an existing object. The existing object will be deleted and new one will be created in its place |
| DELETE | delete an object from the database                                                                       |

A `GET` for a single database object, e.g. `GET api/v1/devices/{deviceId}`, will return a 404 error if the object does not exist. However, a `GET` for a group of objects, e.g. `GET api/v1/devices`, will return an empty array if no matching object is found.

`POST`, `PATCH` and `PUT` return the full object on success.

## Authentication

site_manager uses cookies for authentication. Every request to protected API endpoints (e.g. everything except `api/auth/sign-in/email`) has to include a valid session cookie. The cookie is called `site-manager.session_data`.

To make direct requests to the server without using the frontend authentication is required. This can done by sending the email and password to `api/auth/sign-in/email`. The api will respond with the cookie, which can then be sent with all future requests.

!!! warning

    Better Auth is strict when it comes to requests send to `api/auth/*`. Make sure to set the origin header!

## Query parameters

Some of the endpoints accept query parameters. These are mostly used to filter the results.

```HTTP
GET api/v1/devices?siteId=7829eb19-3f4f-4935-b5c3-2ce3aef53de2
```

If the query parameter is an id for filtering multiple ids can be specified to be used in a logical OR.

```HTTP
GET api/v1/devices?siteId=7829eb19-3f4f-4935-b5c3-2ce3aef53de2&siteId=5caa58cb-9a0b-46d8-9f15-dc4020412471
```

## Status codes

The API uses the following HTTP status codes:

| Code | Status                |     |
| ---- | --------------------- | --- |
| 200  | Ok                    |     |
| 201  | Created               |     |
| 400  | Bad Request           |     |
| 401  | Unauthorized          |     |
| 403  | Forbidden             |     |
| 404  | Not Found             |     |
| 409  | Conflict              |     |
| 500  | Internal Server Error |     |

## Error messages

## About this documentation

Optional parameters in the request body are marked with an `?` at the end of their key. This has to be omitted in the request.
