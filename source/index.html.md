---
title: API Reference

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Smootbox API! You can use our API to access Smootbox API endpoints, which can help you plan your next trip, by suggesting attractions to visit, check the schedules and discover fun things to do on your deserved vacations :)

This example API documentation page was created with [Slate](https://github.com/lord/slate)

# User Authentication

> Example request:

```json
POST /api/v1/auth/sign_in
{
	"email": "user@example.com",
	"password": "password"
}
```

> Example of a valid response:

```json
{
    "status": "ok",
    "auth_token": "<your token here>"
}
```

> Example of an invalid response:

```json
{
    "status": "error",
    "message": "invalid credentials"
}
```

Smootbox uses API keys to allow access to the API.
You can register a new User API key at our [developer portal](http://example.com/developers).

### Endpoint

POST /api/v1/auth/sign_in

### Http Headers

Content-type: application/json

### Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | true | User email
password | true | User password

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>


# User registration


> Example request:

```json
POST /api/v1/auth/register

{
	"email": "foobar@example.com",
	"name": "Foo Bar",
	"password": "password"
}
```

> Example of a valid response:

```json
{
    "status": "ok",
    "user": {
		"id": 1,
		"name": "Foo Bar",
		"email": "foobar@example.com",
		"created_at": "2018-03-10T01:05:56.041Z",
		"updated_at": "2018-03-10T01:05:56.041Z"
	}
}
```

> Example of an invalid response:

```json
{
    "status": "error",
    "message": "Invalid Request",
    "errors": {
        "email": [
            "has already been taken"
        ]
    }
}
```

Creates a new user account.

### Endpoint

`POST /api/v1/auth/register`

### Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | true | User email
name | true | User name
password | true | User password. Should be at least 6 characters long


<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
