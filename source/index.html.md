---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby

toc_footers:
  - <a href='https://portal.signalzen.com/sign-up' target='_blank'>Sign Up for your API Secret Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the SignalZen API! You can use our API to access SignalZen API endpoints, which can get read-only information about your widget users and messages. This is a version number 1 of the API, later we will add more endpoints to make your API experience wider.

We have language bindings in Shell and Ruby! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```ruby
require 'httparty'

api_secret = 'YOUR_API_SECRET'

response = HTTParty.get('https://api.signalzen.com/external/users', headers: { 'Authorization' => "Bearer #{api_secret}", 'Accept' => 'application/vnd.signalzen.v1+json' })

result = JSON.parse(response.body)
```

```shell
# With shell, you can just pass the correct headers with each request
curl "https://api.signalzen.com/external/users" \
  -H "Authorization: Bearer YOUR_API_SECRET" \
  -H "Accept: application/vnd.signalzen.v1+json"
```

> Make sure to replace `YOUR_API_SECRET` with your API secret key.

SignalZen uses API Secret Keys to allow access to the API. You can register a new API Secret Key for your website at our [sign up page](https://portal.signalzen.com/sign-up).

SignalZen expects for the API Secret Key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer YOUR_API_SECRET`

We also expect for the Accept header to be included in all API requests to the server:

`Accept: application/vnd.signalzen.v1+json`

Both headers MUST be sent together with each request, otherwise you can not access the resources.

<aside class="notice">
You must replace <code>YOUR_API_SECRET</code> with your API secret key that belongs to your website. You can find the API secret key in the Integrations page of your website while logged in as admin of your website at our <a href="https://portal.signalzen.com" target="_blank">portal</a>.
</aside>

# Users

## Get Users

```ruby
require 'httparty'

api_secret = 'YOUR_API_SECRET'

response = HTTParty.get('https://api.signalzen.com/external/users', headers: { 'Authorization' => "Bearer #{api_secret}", 'Accept' => 'application/vnd.signalzen.v1+json' })

result = JSON.parse(response.body)
```

```shell
curl "https://api.signalzen.com/external/users" \
  -H "Authorization: Bearer YOUR_API_SECRET" \
  -H "Accept: application/vnd.signalzen.v1+json"
```

> The above command returns JSON structured like this:

```json
{
  "limit":50,
  "offset":0,
  "total":1,
  "users":[
    {
      "id":1,
      "name":"John Smith",
      "email":"john.smith@gmail.com",
      "reference":"123",
      "created_at":"2017-11-25T20:27:42.000Z",
      "updated_at":"2017-11-25T20:27:42.000Z",
      "online_at":"2017-11-25T20:27:42.000Z",
      "last_url":"https://google.com",
      "user_attributes":[
        {"name":"company","value":"John limited"}
      ]
    }
  ]
}
```

This endpoint retrieves users.

### HTTP Request

`GET https://api.signalzen.com/external/users`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
offset    | 0       | Use it to scroll through all users list
limit     | 50      | Greater than 0 and lower than 100

<aside class="success">
Remember — "user_attributes" in the response stands for the custom properties set by the widget JavaScript code. To get more information please visit Integration page of your website in the <a href="https://portal.signalzen.com" target="_blank">portal</a>.
</aside>

## Get a Specific User

```ruby
require 'httparty'

api_secret = 'YOUR_API_SECRET'
user_id = 123

response = HTTParty.get("https://api.signalzen.com/external/users/#{user_id}", headers: { 'Authorization' => "Bearer #{api_secret}", 'Accept' => 'application/vnd.signalzen.v1+json' })

result = JSON.parse(response.body)
```

```shell
curl "https://api.signalzen.com/external/users/123" \
  -H "Authorization: Bearer YOUR_API_SECRET" \
  -H "Accept: application/vnd.signalzen.v1+json"
```

> The above command returns JSON structured like this:

```json
{
  "id":123,
  "name":"John Smith",
  "email":"john.smith@gmail.com",
  "reference":"123",
  "created_at":"2017-11-25T20:27:42.000Z",
  "updated_at":"2017-11-25T20:27:42.000Z",
  "online_at":"2017-11-25T20:27:42.000Z",
  "last_url":"https://google.com",
  "user_attributes":[
    {"name":"company","value":"John limited"}
  ]
}
```

This endpoint retrieves a specific user.

### HTTP Request

`GET https://api.signalzen.com/external/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to retrieve

# Messages

## Get Messages

```ruby
require 'httparty'

api_secret = 'YOUR_API_SECRET'
user_id = 123

response = HTTParty.get("https://api.signalzen.com/external/users/#{user_id}/messages", headers: { 'Authorization' => "Bearer #{api_secret}", 'Accept' => 'application/vnd.signalzen.v1+json' })

result = JSON.parse(response.body)
```

```shell
curl "https://api.signalzen.com/external/users/123/messages" \
  -H "Authorization: Bearer YOUR_API_SECRET" \
  -H "Accept: application/vnd.signalzen.v1+json"
```

> The above command returns JSON structured like this:

```json
{
  "limit": 50,
  "offset": 0,
  "total": 2,
  "messages": [
    {
      "id": 1,
      "body": "test chat message",
      "read_by_user": true,
      "created_at": "2018-02-09T17:18:50.000Z",
      "file_url": null,
      "auto_invitation": false,
      "sender_type": "user",
      "read_by_operator": true,
      "sender": {
        "id": 1,
        "name": "David Smith",
        "email": "visitor@gmail.com"
      }
    },
    {
      "id": 2,
      "body": "test response from operator",
      "read_by_user": false,
      "created_at": "2018-02-09T18:18:38.000Z",
      "file_url": null,
      "auto_invitation": false,
      "sender_type": "operator",
      "read_by_operator": true,
      "sender": {
        "id": 1,
        "forename": "John",
        "surname": "Smith",
        "email": "operator@gmail.com",
        "picture_thumb_url": null
      }
    }
  ]
}
```

This endpoint retrieves messages of a user chat.

### HTTP Request

`GET https://api.signalzen.com/external/users/<USER_ID>/messages`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
USER_ID    | -       | User id which owns the chat
offset    | 0       | Use it to scroll through all messages list
limit     | 50      | Greater than 0 and lower than 100

<aside class="success">
Remember — when "file_url" attribute is present, it means that the message contains attachment. The "file_url" is valid for 20 seconds from the response return time.
</aside>

## Get a Specific Message

```ruby
require 'httparty'

api_secret = 'YOUR_API_SECRET'
user_id = 123
message_id = 1234

response = HTTParty.get("https://api.signalzen.com/external/users/#{user_id}/messages/#{message_id}", headers: { 'Authorization' => "Bearer #{api_secret}", 'Accept' => 'application/vnd.signalzen.v1+json' })

result = JSON.parse(response.body)
```

```shell
curl "https://api.signalzen.com/external/users/123/messages/1234" \
  -H "Authorization: Bearer YOUR_API_SECRET" \
  -H "Accept: application/vnd.signalzen.v1+json"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1234,
  "body": "test chat message",
  "read_by_user": true,
  "created_at": "2018-02-09T17:18:50.000Z",
  "file_url": null,
  "auto_invitation": false,
  "sender_type": "user",
  "read_by_operator": true,
  "sender": {
    "id": 1,
    "name": "David Smith",
    "email": "visitor@gmail.com"
  }
}
```

This endpoint retrieves a specific message of a user chat.

### HTTP Request

`GET https://api.signalzen.com/external/users/<USER_ID>/messages/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
USER_ID | The ID of the user
ID | The ID of the message to retrieve
