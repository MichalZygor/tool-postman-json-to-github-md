Example 1

# API Documentation #reference

## Contents

<a name="contents"></a>

### User

- [User » GET `https://api.getpostman.com/me?foo=bar`](#user-get-https-api-getpostman-com-me-foo-bar)

### Collections

- [Collections » POST `https://api.getpostman.com/collections`](#collections-post-https-api-getpostman-com-collections)
- [Collections » GET `https://api.getpostman.com/collections/{{collectionId}}`](#collections-get-https-api-getpostman-com-collections-collectionid)
- [Collections » DELETE `https://api.getpostman.com/collections/{{collectionId}}`](#collections-delete-https-api-getpostman-com-collections-collectionid)
- [Collections » PUT `https://api.getpostman.com/collections/{{collectionId}}`](#collections-put-https-api-getpostman-com-collections-collectionid)
- [Collections » GET `https://api.getpostman.com/collections`](#collections-get-https-api-getpostman-com-collections)

---

<a name="user-get-https-api-getpostman-com-me-foo-bar"></a>

## User » GET `https://api.getpostman.com/me?foo=bar`

Gets information about the authenticated user.

### Query

| Key | Value |
|---|---|
| foo | bar |

### Responses

#### Successful Response [200]

```json
{
    "user": {
        "id": 12345678,
        "username": "taylor-lee",
        "email": "taylor.lee@example.com",
        "fullName": "Taylor Lee",
        "avatar": "https://example.com/user/r5u9qpvmujfjf6lbqmga.jpg",
        "isPublic": true
    },
    "operations": [
```
<details><summary>Show all (54 lines)</summary>

```json
{
    "user": {
        "id": 12345678,
        "username": "taylor-lee",
        "email": "taylor.lee@example.com",
        "fullName": "Taylor Lee",
        "avatar": "https://example.com/user/r5u9qpvmujfjf6lbqmga.jpg",
        "isPublic": true
    },
    "operations": [
        {
            "name": "mock_usage",
            "limit": 1000000,
            "usage": 110276,
            "overage": 0
        },
        {
            "name": "monitor_request_runs",
            "limit": 10000000,
            "usage": 1141750,
            "overage": 0
        },
        {
            "name": "api_usage",
            "limit": 1000000,
            "usage": 16240,
            "overage": 0
        },
        {
            "name": "custom_domains",
            "limit": 25,
            "usage": 25,
            "overage": 0
        },
        {
            "name": "serverless_requests",
            "limit": 10000,
            "usage": 0,
            "overage": 0
        },
        {
            "name": "integrations",
            "limit": 5000,
            "usage": 1018,
            "overage": 0
        },
        {
            "name": "cloud_agent_requests",
            "limit": 1000000,
            "usage": 1615,
            "overage": 0
        }
    ]
}
```
</details>

#### Rate Limit Exceeded [429]

```json
{
    "error": "rateLimited",
    "message": "Rate limit exceeded. Please retry after 1669048687"
}
```
[⬆ Back to menu](#contents)

---

<a name="collections-post-https-api-getpostman-com-collections"></a>

## Collections » POST `https://api.getpostman.com/collections`

Creates a collection using the [Postman Collection v2 schema format](https://schema.postman.com/json/collection/v2.1.0/docs/index.html). Include a `collection` object in the request body that contains the following required properties:

*   `info` — An **object** that contains the following properties:
    *   `name` — A **string** value that contains the collection's name.
    *   `schema` — A **string** that contains a URL to the collection's schema. For example, the `https://schema.getpostman.com/collection/v1` URL.
*   `item` — An **object** that contains the HTTP request and response information.
    *   `request` — An **object** that contains the collection's request information. For a complete list of values, refer to the `definitions.request` entry in the [collection.json schema file](https://schema.postman.com/json/collection/v2.1.0/collection.json). If you pass an empty object for this value, the system defaults to an untitled GET request.

**Note:**

*   For a complete list of available property values for this endpoint, use the following references available in the [collection.json schema file](https://schema.postman.com/json/collection/v2.1.0/collection.json):
    *   `info` object — Use the `definitions.info` entry.
    *   `item` object — Use the `definitions.items` entry.
*   For all other possible values, refer to the [collection.json schema file](https://schema.postman.com/json/collection/v2.1.0/collection.json).

### Query

| Key | Value |
|---|---|
| workspace | {{workspaceId}} |

### Headers

| Header | Value |
|---|---|
| Content-Type | application/json |

### Body

```json
{
    "collection": {
        "info": {
            "name": "{{collectionName}}",
            "schema": "{{collectionSchemaUrl}}"
        },
        "item": [
            {
                "request": {}
            }
```
<details><summary>Show all (13 lines)</summary>

```json
{
    "collection": {
        "info": {
            "name": "{{collectionName}}",
            "schema": "{{collectionSchemaUrl}}"
        },
        "item": [
            {
                "request": {}
            }
        ]
    }
}
```
</details>

### Responses

#### Successful Response [200]

```json
{
    "collection": {
        "id": "12ece9e1-2abf-4edc-8e34-de66e74114d2",
        "name": "Test Collection",
        "uid": "12345678-12ece9e1-2abf-4edc-8e34-de66e74114d2"
    }
}
```
#### Bad Request [400]

```json
{
    "error": {
        "name": "instanceFoundError",
        "message": "The specified item already exists.",
        "details": {
            "item": "collection",
            "id": "12ece9e1-2abf-4edc-8e34-de66e74114d2"
        }
    }
}
```
#### Malformed Request [400]

```json
{
    "error": {
        "name": "malformedRequestError",
        "message": "Found 1 errors with the supplied collection.",
        "details": [
            ": must have required property 'info'"
        ]
    }
}
```
#### Rate Limit Exceeded [429]

```json
{
    "error": "rateLimited",
    "message": "Rate limit exceeded. Please retry after 1669048687"
}
```
[⬆ Back to menu](#contents)

---

<a name="collections-get-https-api-getpostman-com-collections-collectionid"></a>

## Collections » GET `https://api.getpostman.com/collections/{{collectionId}}`

Gets information about a collection. For a complete list of this endpoint's possible values, use the [collection.json schema file](https://schema.postman.com/json/collection/v2.1.0/collection.json).

### Query

| Key | Value |
|---|---|
| access_key | {{accessKey}} |

### Responses

#### Successful Response [200]

```json
{
    "collection": {
        "info": {
            "name": "Test Collection",
            "description": "This is a test collection that makes a tiny request to Postman Echo service to get the list of request headers sent by a HTTP client.",
            "_postman_id": "12ece9e1-2abf-4edc-8e34-de66e74114d2",
            "schema": "https://schema.getpostman.com/json/collection/v2.0.0/collection.json",
            "updatedAt": "2022-06-16T20:21:13.000Z",
            "fork": {
                "label": "Test Fork",
```
<details><summary>Show all (47 lines)</summary>

```json
{
    "collection": {
        "info": {
            "name": "Test Collection",
            "description": "This is a test collection that makes a tiny request to Postman Echo service to get the list of request headers sent by a HTTP client.",
            "_postman_id": "12ece9e1-2abf-4edc-8e34-de66e74114d2",
            "schema": "https://schema.getpostman.com/json/collection/v2.0.0/collection.json",
            "updatedAt": "2022-06-16T20:21:13.000Z",
            "fork": {
                "label": "Test Fork",
                "createdAt": "2022-06-16T19:51:44.069Z",
                "from": "12345678-12ece9e1-2abf-4edc-8e34-de66e74114d2"
            }
        },
        "item": [
            {
                "name": "Test GET Response",
                "id": "82ee981b-e19f-962a-401e-ea34ebfb4848",
                "event": [
                    {
                        "listen": "test",
                        "script": {
                            "id": "7d2334fc-a84a-4c3d-b26c-7529afa4c0ae",
                            "exec": [
                                "pm.test(\"Status code is 200\", function () {",
                                "    pm.response.to.have.status(200);",
                                "});"
                            ],
                            "type": "text/javascript"
                        }
                    }
                ],
                "request": {
                    "url": "https://echo.getpostman.com/headers",
                    "method": "GET",
                    "header": [
                        {
                            "key": "Content-Type",
                            "value": "application/json"
                        }
                    ]
                },
                "response": []
            }
        ]
    }
}
```
</details>

#### Get Collection with Access Token [200]

```json
{
    "collection": {
        "info": {
            "name": "Test Collection",
            "description": "This is a test collection that makes a tiny request to Postman Echo service to get the list of request headers sent by a HTTP client.",
            "_postman_id": "12ece9e1-2abf-4edc-8e34-de66e74114d2",
            "schema": "https://schema.getpostman.com/json/collection/v2.0.0/collection.json",
            "updatedAt": "2022-06-16T20:21:13.000Z",
            "fork": {
                "label": "Test Fork",
```
<details><summary>Show all (47 lines)</summary>

```json
{
    "collection": {
        "info": {
            "name": "Test Collection",
            "description": "This is a test collection that makes a tiny request to Postman Echo service to get the list of request headers sent by a HTTP client.",
            "_postman_id": "12ece9e1-2abf-4edc-8e34-de66e74114d2",
            "schema": "https://schema.getpostman.com/json/collection/v2.0.0/collection.json",
            "updatedAt": "2022-06-16T20:21:13.000Z",
            "fork": {
                "label": "Test Fork",
                "createdAt": "2022-06-16T19:51:44.069Z",
                "from": "12345678-12ece9e1-2abf-4edc-8e34-de66e74114d2"
            }
        },
        "item": [
            {
                "name": "Test GET Response",
                "id": "82ee981b-e19f-962a-401e-ea34ebfb4848",
                "event": [
                    {
                        "listen": "test",
                        "script": {
                            "id": "7d2334fc-a84a-4c3d-b26c-7529afa4c0ae",
                            "exec": [
                                "pm.test(\"Status code is 200\", function () {",
                                "    pm.response.to.have.status(200);",
                                "});"
                            ],
                            "type": "text/javascript"
                        }
                    }
                ],
                "request": {
                    "url": "https://echo.getpostman.com/headers",
                    "method": "GET",
                    "header": [
                        {
                            "key": "Content-Type",
                            "value": "application/json"
                        }
                    ]
                },
                "response": []
            }
        ]
    }
}
```
</details>

#### Not Found [404]

```json
{
    "error": {
        "name": "instanceNotFoundError",
        "message": "We could not find the collection you are looking for"
    }
}
```
#### Rate Limit Exceeded [429]

```json
{
    "error": "rateLimited",
    "message": "Rate limit exceeded. Please retry after 1669048687"
}
```
[⬆ Back to menu](#contents)

---

<a name="collections-delete-https-api-getpostman-com-collections-collectionid"></a>

## Collections » DELETE `https://api.getpostman.com/collections/{{collectionId}}`

Deletes a collection.

### Responses

#### Successful Response [200]

```json
{
    "collection": {
        "id": "12ece9e1-2abf-4edc-8e34-de66e74114d2",
        "uid": "12345678-12ece9e1-2abf-4edc-8e34-de66e74114d2"
    }
}
```
#### Not Found [404]

```json
{
    "error": {
        "name": "instanceNotFoundError",
        "message": "The specified item does not exist.",
        "details": {
            "item": "collection",
            "id": "12ece9e1-2abf-4edc-8e34-de66e74114d2"
        }
    }
}
```
#### Rate Limit Exceeded [429]

```json
{
    "error": "rateLimited",
    "message": "Rate limit exceeded. Please retry after 1669048687"
}
```
[⬆ Back to menu](#contents)

---

<a name="collections-put-https-api-getpostman-com-collections-collectionid"></a>

## Collections » PUT `https://api.getpostman.com/collections/{{collectionId}}`

Updates a collection using the [Postman Collection v2 schema format](https://schema.postman.com/json/collection/v2.1.0/docs/index.html). Include a `collection` object in the request body that contains the following required properties:

- `info` — An **object** that contains the following properties:
    - `name` — A **string** value that contains the collection's name.
    - `schema` — A **string** that contains a URL to the collection's schema. For example, the `https://schema.getpostman.com/collection/v1` URL.
- `item` — An **object** that contains the HTTP request and response information.
    - `request` — An **object** that contains the collection's request information. For a complete list of values, refer to the `definitions.request` entry in the [collection.json schema file](https://schema.postman.com/json/collection/v2.1.0/collection.json). If you pass an empty object for this value, the system defaults to an untitled GET request.

**Note:**

- For a complete list of available property values for this endpoint, use the following references available in the [collection.json schema file](https://schema.postman.com/json/collection/v2.1.0/collection.json):
    - `info` object — Use the `definitions.info` entry.
    - `item` object — Use the `definitions.items` entry.
- For all other possible values, refer to the [collection.json schema file](https://schema.postman.com/json/collection/v2.1.0/collection.json).
    

### Important

Use caution when using this endpoint. The system will replace the existing collection with the values passed in the request body.

### Headers

| Header | Value |
|---|---|
| Content-Type | application/json |

### Body

```json
{
    "collection": {
        "info": {
            "name": "{{collectionName}}",
            "schema": "{{collectionSchemaUrl}}"
        },
        "item": [
            {
                "request": {}
            }
```
<details><summary>Show all (13 lines)</summary>

```json
{
    "collection": {
        "info": {
            "name": "{{collectionName}}",
            "schema": "{{collectionSchemaUrl}}"
        },
        "item": [
            {
                "request": {}
            }
        ]
    }
}
```
</details>

### Responses

#### Successful Response [200]

```json
{
    "collection": {
        "id": "12ece9e1-2abf-4edc-8e34-de66e74114d2",
        "name": "Test Collection",
        "uid": "12345678-12ece9e1-2abf-4edc-8e34-de66e74114d2"
    }
}
```
#### Forbidden [403]

```json
{
    "error": {
        "name": "forbiddenError",
        "message": "You do not have enough permissions to perform this action."
    }
}
```
#### Not Found [404]

```json
{
    "error": {
        "name": "instanceNotFoundError",
        "message": "The specified item does not exist.",
        "details": {
            "item": "collection",
            "id": "12ece9e1-2abf-4edc-8e34-de66e74114d2"
        }
    }
}
```
#### Malformed Request [400]

```json
{
    "error": {
        "name": "malformedRequestError",
        "message": "Found 2 errors with the supplied collection.",
        "details": [
            ": must have required property 'item'",
            "info: must have required property 'schema'"
        ]
    }
}
```
#### Collection ID Mismatch [400]

```json
{
    "error": {
        "name": "collectionMismatchError",
        "message": "The collection ID in the path does not match the collection ID in the request body."
    }
}
```
#### Rate Limit Exceeded [429]

```json
{
    "error": "rateLimited",
    "message": "Rate limit exceeded. Please retry after 1669048687"
}
```
[⬆ Back to menu](#contents)

---

<a name="collections-get-https-api-getpostman-com-collections"></a>

## Collections » GET `https://api.getpostman.com/collections`

Gets all of your [collections](https://www.getpostman.com/docs/collections). The response includes all of your subscribed collections.

### Query

| Key | Value |
|---|---|
| workspace | {{workspaceId}} |

### Responses

#### Successful Response [200]

```json
{
    "collections": [
        {
            "id": "dac5eac9-148d-a32e-b76b-3edee9da28f7",
            "name": "Cloud API",
            "owner": "12345678",
            "createdAt": "2022-04-12T10:29:46.000Z",
            "updatedAt": "2022-04-12T10:29:56.000Z",
            "uid": "12345678-dac5eac9-148d-a32e-b76b-3edee9da28f7",
            "isPublic": true
```
<details><summary>Show all (36 lines)</summary>

```json
{
    "collections": [
        {
            "id": "dac5eac9-148d-a32e-b76b-3edee9da28f7",
            "name": "Cloud API",
            "owner": "12345678",
            "createdAt": "2022-04-12T10:29:46.000Z",
            "updatedAt": "2022-04-12T10:29:56.000Z",
            "uid": "12345678-dac5eac9-148d-a32e-b76b-3edee9da28f7",
            "isPublic": true
        },
        {
            "id": "12ece9e1-2abf-4edc-8e34-de66e74114d2",
            "name": "Test Collection",
            "owner": "12345678",
            "createdAt": "2022-01-13T10:21:46.000Z",
            "updatedAt": "2022-02-12T11:29:56.000Z",
            "uid": "12345678-12ece9e1-2abf-4edc-8e34-de66e74114d2",
            "isPublic": false,
            "fork": {
                "label": "Test Fork",
                "createdAt": "2022-06-16T19:51:44.069Z",
                "from": "12345678-12ece9e1-2abf-4edc-8e34-de66e74114d2"
            }
        },
        {
            "id": "f695cab7-6878-eb55-7943-ad88e1ccfd65",
            "name": "Postman Echo",
            "owner": "12345678",
            "createdAt": "2021-04-11T09:18:26.000Z",
            "updatedAt": "2022-05-01T15:29:32.000Z",
            "uid": "12345678-f695cab7-6878-eb55-7943-ad88e1ccfd65",
            "isPublic": true
        }
    ]
}
```
</details>

#### Filter by Workspace [200]

```json
{
    "collections": [
        {
            "id": "dac5eac9-148d-a32e-b76b-3edee9da28f7",
            "name": "Cloud API",
            "owner": "12345678",
            "createdAt": "2022-04-12T10:29:46.000Z",
            "updatedAt": "2022-04-12T10:29:56.000Z",
            "uid": "12345678-dac5eac9-148d-a32e-b76b-3edee9da28f7",
            "isPublic": true
```
<details><summary>Show all (13 lines)</summary>

```json
{
    "collections": [
        {
            "id": "dac5eac9-148d-a32e-b76b-3edee9da28f7",
            "name": "Cloud API",
            "owner": "12345678",
            "createdAt": "2022-04-12T10:29:46.000Z",
            "updatedAt": "2022-04-12T10:29:56.000Z",
            "uid": "12345678-dac5eac9-148d-a32e-b76b-3edee9da28f7",
            "isPublic": true
        }
    ]
}
```
</details>

#### Rate Limit Exceeded [429]

```json
{
    "error": "rateLimited",
    "message": "Rate limit exceeded. Please retry after 1669048687"
}
```
[⬆ Back to menu](#contents)

---

