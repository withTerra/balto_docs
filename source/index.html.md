---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - http
  # - shell
  # - ruby
  # - python
  # - javascript

includes:
  - errors

search: true
---

# Introduction

Welcome to the balto API docs. Poke around and feel free to reach out with any questions to `founders@withterra.com`

Reach out for access to the playground.


# iMessages

## Check for iMessage compatibility

Check if the given phone number is eligible for iMessages. If it's not, you can use Twilio to handle it. 

### HTTP Request

`POST https://www.usebalto.com/api/is_imessage`

### JSON Body Parameters

Parameter | Description
--------- | -----------
phone | The phone number to check. Formatted as all numerics i.e. 1234567890

> The endpoint returns JSON as below:

```json
{
  "is_imessage" : true
}
```

## Send an iMessage

Use the following request to send an iMessage to the specified number. 

#### Using Special Effects

Special effects are an iMessage property that can be triggered via special keywords "Congratulations, Happy Birthday!"

### HTTP Request

`POST https://www.usebalto.com/api/send`

### JSON Body Parameters

Parameter | Description
--------- | -----------
phone | The phone number to check. Formatted as all numerics i.e. 1234567890
text | The message you plan to send. i.e. "Hi!"

> The endpoint returns JSON as below:

```json
{
  "phone": "PHONE",  // the given phone number
  "message_uuid": "6e71e2af-d91d-4eb9-8af6-c1ca0f910da7"
}
```

## Check iMessage status

iMessages are queued. Use this to check if the message was delivered successfully, read

### HTTP Request

`GET https://www.usebalto.com/api/message/<MESSAGE_UUID>`

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
}
```
