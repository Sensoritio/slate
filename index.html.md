---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - json
  - Javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the LetsgoWallet API
---

# Introduction

Welcome to the LetsgoWallet API! You can use our API to access LetsgoWallet API endpoints, which can expose different functionalities of the wallet like registration, cash-in, cash-out, and others.

We have language bindings in json and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Registration

> To register, use this code:

```json
{
"method":"POST",
"url": "https://us-central1-clockpay.cloudfunctions.net/ussd-auth"
},
{
 "headers": [
              {"Content-Type":"application/json"},
			  {"Accept":"application/json"}
]
},
{
"body":{
     "username" : "deo@sensorit.io",
     "accountIdentifier": "CELLPHONE",
     "phoneNumber": "+27823214215",
     "firstname": "Deo",
     "lastname": "Tshivhenga",
     "kycLevel":"LOW",
     "operation" : "register",
     "accountType": "personal"
}
}
> The above command returns JSON structured like this:

```json
{
    "user": [
        {
            "uid": "john@doe.com",
            "displayName": null,
            "photoURL": null,
            "email": "john@doe.com",
            "phoneNumber": null,
            "providerId": "password"
        }
    ],
    "wallets": {
        "user": "john@doe.com",
        "pin": 5115,
        "status": "ACTIVE",
        "summaryTransactions": [],
        "createdAt": "1631303729341",
        "type": "personal",
        "currency": "ZAR",
        "account": "udzhrlo38",
        "runningBalance": 0
    }
}
```

> Make sure to replace `meowmeowmeow` with your API key.

LetsgoWallet uses API keys to allow access to the API. The registration endpoint will respond with a refreshable token, which you can use unless you use custom authentication.

LetsgoWallet expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Profile

## Get profile

```json
{
"method":"GET",
"url": "https://us-central1-clockpay.cloudfunctions.net/wallet-api/api/v1/profile?username"
},
{
 "headers": [
              {"Content-Type":"application/json"},
			  {"Accept":"application/json"}
]
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'LetsgoWallet'

api = LetsgoWallet::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import LetsgoWallet

api = LetsgoWallet.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const LetsgoWallet = require('LetsgoWallet');

let api = LetsgoWallet.authorize('meowmeowmeow');
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
require 'LetsgoWallet'

api = LetsgoWallet::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import LetsgoWallet

api = LetsgoWallet.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const LetsgoWallet = require('LetsgoWallet');

let api = LetsgoWallet.authorize('meowmeowmeow');
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

