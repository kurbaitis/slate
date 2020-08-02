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

Welcome to the SignalZen API! You can use our Frontend (JavaScript) API to do advanced integration on your website or use backend API to access SignalZen API endpoints, which can get read-only information about your widget users and messages. This page includes a version number 1 Frontend (JavaScript) API and a version number 1 of the Backend API, later we will add more endpoints to make your API experience wider.

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# JS API
```javascript
<script type="text/javascript">
var _sz=_sz||{};_sz.appId="YOUR_APP_ID",function(){var e=document.createElement("script");e.src="https://cdn.signalzen.com/signalzen.js",e.setAttribute("async","true"),document.documentElement.firstChild.appendChild(e);var t=setInterval(function(){"undefined"!=typeof SignalZen&&(clearInterval(t),new SignalZen(_sz).load())},10)}();
</script>
```
As stated in the Integration page of your website inside the portal, you need to initialize our widget by a simple command which looks like on the right side of this page.


However, there are more advanced options to initialize and work with the widget. We separated the concerns of working with the widget into a few sections (see below).

## Language
```javascript
<script type="text/javascript">
var _sz = {
  language: 'danish'
};
var _sz=_sz||{};_sz.appId="YOUR_APP_ID",function(){var e=document.createElement("script");e.src="https://cdn.signalzen.com/signalzen.js",e.setAttribute("async","true"),document.documentElement.firstChild.appendChild(e);var t=setInterval(function(){"undefined"!=typeof SignalZen&&(clearInterval(t),new SignalZen(_sz).load())},10)}();
</script>
```
Usually by creating translations of the widget, we determine the language that the visitors see by their browser settings.
There is an alternative way for this purpose, you can set the language by the integration code which takes precedence over the browser language. See the code example on the right how to do this.

## Metadata about a visitor
```javascript
<script type="text/javascript">
var _sz = {
  userData: {
    reference: "your-visitor-user-id",
    email: 'your-visitor@email.com',
    name: 'Your visitor name',
    'some custom attribute': 'your visitor custom attribute'
  }
};
var _sz=_sz||{};_sz.appId="YOUR_APP_ID",function(){var e=document.createElement("script");e.src="https://cdn.signalzen.com/signalzen.js",e.setAttribute("async","true"),document.documentElement.firstChild.appendChild(e);var t=setInterval(function(){"undefined"!=typeof SignalZen&&(clearInterval(t),new SignalZen(_sz).load())},10)}();
</script>
```
Some websites have login area, where you have certain context which you want to be visible in a chat page in order to recognise the chat owner in more comfortable way. It's possible to set that data by JS configuration and send each time the chat owner sends a message. See the code example on the right how to do this.
## Widget colors
```javascript
<script type="text/javascript">
var _sz = {
  colors: {
    primary: '#046ee5',
    secondary: '#f5f7f8',
    footer: '#ffffff',
    error: '#cccccc',
    popup: '#ffffff',
    popupClose: '#ffffff',
    popupCloseSymbol: '#9c9c9c',
    popupFormInputBorder: '#9c9c9c',
    badge: '#c30606',
    footerEmojisPopup: '#ffffff',
    footerOptions: '#b2b3b4',
    operatorMessages: '#ebeff0',
    formInput: '#ffffff',
    formInputBorder: '#ffffff',
    formButton: '#0fc306',
    formPlaceholder: '#949595',
    textPrimary: '#ffffff',
    textError: '#ffffff',
    textTime: '#b5b7b8',
    textTimeSeparator: '#8e9192',
    textUserMessage: '#ffffff',
    textFormInput: '#000000',
    textFormTitle: '#8e9192',
    textFormButton: '#ffffff',
  }
};
var _sz=_sz||{};_sz.appId="YOUR_APP_ID",function(){var e=document.createElement("script");e.src="https://cdn.signalzen.com/signalzen.js",e.setAttribute("async","true"),document.documentElement.firstChild.appendChild(e);var t=setInterval(function(){"undefined"!=typeof SignalZen&&(clearInterval(t),new SignalZen(_sz).load())},10)}();
</script>
```
You might not like the default color palette of the widget, so you can configure it yourself by a big variety of settings which are self explanatory and you can experiment with the colors of your choice. See the code example on the right how to do this.
## Invisibility
```javascript
<script type="text/javascript">
var _sz = {
  invisible: true
};
var _sz=_sz||{};_sz.appId="YOUR_APP_ID",function(){var e=document.createElement("script");e.src="https://cdn.signalzen.com/signalzen.js",e.setAttribute("async","true"),document.documentElement.firstChild.appendChild(e);var t=setInterval(function(){"undefined"!=typeof SignalZen&&(clearInterval(t),new SignalZen(_sz).load())},10)}();
</script>
```
Depending on your needs, you can start the widget in invisibility mode, which means that all the widget will be hidden until the point you decide differently. See the code example on the right how to start the widget invisible.

In order to make the widget visible, just call `SignalZen.show()` or `SignalZen.hide()` if you want to hide it again.

## Hiding on mobile
```javascript
<script type="text/javascript">
var _sz = {
  hideOnMobile: true
};
var _sz=_sz||{};_sz.appId="YOUR_APP_ID",function(){var e=document.createElement("script");e.src="https://cdn.signalzen.com/signalzen.js",e.setAttribute("async","true"),document.documentElement.firstChild.appendChild(e);var t=setInterval(function(){"undefined"!=typeof SignalZen&&(clearInterval(t),new SignalZen(_sz).load())},10)}();
</script>
```
You may want to disable your chat widget on mobile devices in order not to make your webpage too stuffy.
Achieving that is simple as a flag to pass into the widget's initialization options.

## Positioning
```javascript
<script type="text/javascript">
var _sz = {
  layout: {
    horizontalOffset: 100, // Allows to tune the position your chat box to right or left in pixels
    verticalOffset: 100, // Allows to tune the position your chat box to top or bottom in pixels
    horizontalPosition: 'left', // Possible values: 'left', 'right'
    verticalPosition: 'top', // Possible values: 'top', 'bottom'
  }
};
var _sz=_sz||{};_sz.appId="YOUR_APP_ID",function(){var e=document.createElement("script");e.src="https://cdn.signalzen.com/signalzen.js",e.setAttribute("async","true"),document.documentElement.firstChild.appendChild(e);var t=setInterval(function(){"undefined"!=typeof SignalZen&&(clearInterval(t),new SignalZen(_sz).load())},10)}();
</script>
```
Depending on your needs, you can change position of the chat widget trigger button and chat box.

Just add the `layout` options that should be sufficient to position SignalZen widget at the right part of your website.

## CSS for trigger button
```html
<style>
// Changing the size of the button:
#signalzen_widget__root a {
  width: 50px !important;
  height: 50px !important;
}
</style>
<script type="text/javascript">
var _sz=_sz||{};_sz.appId="YOUR_APP_ID",function(){var e=document.createElement("script");e.src="https://cdn.signalzen.com/signalzen.js",e.setAttribute("async","true"),document.documentElement.firstChild.appendChild(e);var t=setInterval(function(){"undefined"!=typeof SignalZen&&(clearInterval(t),new SignalZen(_sz).load())},10)}();
</script>
```
Sometimes you may want to change the widget trigger button CSS. You can do that by using `#signalzen_widget__root a` CSS selector.

Please don't forget to use `!important` declaration for each of your new style settings.

## Expand and Suspend
The command `SignalZen.expand()` will open the widget chat window instead of showing just the chat circle with the chat icon.
The command `SignalZen.suspend()` will minimise the chat window to display only chat circle with the chat icon.
## Events
We support multiple events that come with metadata about each of them. This could be used for an advanced integration if you want to know in your JavaScript implementation when the chat is opened, a message is received or sent. Let's start with the events list and wrap up with a single example how to catch an event.

### signalzen.collapse
This event is called when the chat is expanded or suspended and by capturing it, you can get an object with key `status` which will return the action nature. Currently, the status value can be `opened` or `closed`.

### signalzen.messageReceived
This event is called when a visitor receives a chat message not depending on the message nature, it means it can be even an auto invitation message. The event metadata contains message information which you can check yourself while dealing with the implementation.

### signalzen.messageSent
This event is called when a visitor sends a chat message. The event metadata contains message information which you can check yourself while dealing with the implementation.

### Real world example
```javascript
window.addEventListener('signalzen.collapse', function (e) {
  if (e.detail.status === 'opened') {
    alert('The chat is opened!');
  } else {
    alert('The chat is closed!');
  }
}, false);
```
Let's say you have a webpage where you need to react somehow when the widget collapse event happens. In this case, you need to put an event listener in your code and wait for the event to happen. Once the event happens, you can execute appropriate your own JS code. See the example on the right of this page. Be aware, that the metadata is contained in the listener function argument, under the `.detail` scope.
## Troubleshooting
Please don't hesitate to contact us directly, but before doing that, take a look to these mostly common questions.

### 1. The widget icon stucks at the loading state forever.
Double check if your integration code is placed correctly according to our guidance in the Integration Wizard page.
It might be that our integration implementation is conflicting with your other JavaScript libraries used in your website.
The best known case is Pace library which is incompatible with our service, so if you have it or other libraries dependent on it installed, please add this (right side of the screen) before SignalZen integration snippet in your webpage:

```html
<script type="text/javascript">
  window.paceOptions = {
    ajax: {
      trackWebSockets: false,
      ignoreURLs: [/signalzen/]
    }
  };
</script>
```
### 2. I enabled "Ask visitors for email and name before displaying live chat" but can't see the form in the widget.
Sometimes our clients put the code from "Additional customisation" section of this guide into webpages and use "name" and "email" variables as in the code snippet.
This means that you preset the name and email instead allowing for your visitors to fill in by themselves.
To avoid that, please don't use "name" and "email" variable names in the "Additional customisation" code section.

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

SignalZen uses API Secret Keys to allow access to the Backend API. You can register a new API Secret Key for your website at our [sign up page](https://portal.signalzen.com/sign-up).

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
