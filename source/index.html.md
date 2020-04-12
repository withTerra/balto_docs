---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - http
  # - shell
  # - ruby
  # - python
  # - javascript

toc_footers:
  - <a href='app.usebalto.com/signup'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the balto API docs. Poke around and feel free to reach out with any questions to `founders@withterra.com`

To use any of these APIs, please <a href="app.usebalto.com/signup">Sign up</a> for access to an API Key and our playground.

# Authentication

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Bearer API_KEY"
```

balto expects for the API key to be included in **all** API requests to the server in a header that looks like the following:

`Authorization: Bearer API_KEY`

<aside class="notice">
You must replace <code>API_KEY</code> with your personal API key.
</aside>

# iMessages

## Check for iMessage compatibility

Check if the given phone number is eligible for iMessages. If it's not, you can use Twilio to handle it. 

### HTTP Request

`GET https://api.usebalto.com/is_imessage/<PHONE>`

> The endpoint returns JSON as below:

```json
{
  "phone": "PHONE",  // the given phone number
  "is_imessage" : "True"
}
```

### URL Parameters

Parameter | Description
--------- | -----------
PHONE | The phone number to check. Formatted as all numerics i.e. 1234567890

## Send an iMessage

Use the following request to send an iMessage to the specified number. 

#### Using Special Effects

Special effects are an iMessage property that can be triggered in two ways.
1. Automatically when using certain phrases i.e. "Congratulations, Happy Birthday!"

### HTTP Request

`POST https://api.usebalto.com/send/message`

### Headers

HEADER | Description
--------- | -----------
Authorization: Bearer API_KEY | Your personal API_KEY

### JSON Body Parameters

Parameter | Description
--------- | -----------
PHONE | The phone number to check. Formatted as all numerics i.e. 1234567890
TEXT | The message you plan to send. i.e. "Hi!"

> The endpoint returns JSON as below:

```json
{
  "phone": "PHONE",  // the given phone number
  "message_uuid": "6e71e2af-d91d-4eb9-8af6-c1ca0f910da7"
}
```

## Check iMessage status

iMessages are queued. Use this to check if the message was delivered successfully, read, tapped_back etc.

### HTTP Request

`GET https://api.usebalto.com/message/<MESSAGE_UUID>`

Parameter | Description
--------- | -----------
MESSAGE_UUID | The message uuid returned when you first sent a message. Or given by the webhook endpoint for when a new message comes in i.e. `6e71e2af-d91d-4eb9-8af6-c1ca0f910da7`.

> The endpoint returns JSON as below:

```json
{
  "phone": "1234567890",
  "message_uuid": "<MESSAGE_UUID",
  "date_submitted": "Sun, 12 Apr 2020 05:46:48 GMT",
  "date_delivered": "Sun, 12 Apr 2020 05:46:49 GMT",
  "date_read": "Sun, 12 Apr 2020 05:47:38 GMT", // || or null if not read
  "tapped_back": "Heart", // Heart | Up | Down | Ha | Exclamation | Question
}
```

## Send videos

Documentation coming soon

## Use Tapbacks

Documentation coming soon

## Apple Cash

Documentation coming soon

# SMS

Documentation coming soon

# Webhooks

Documentation coming soon

## Status 