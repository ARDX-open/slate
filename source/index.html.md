---
title: ARDX Open API Reference

language_tabs:
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='http://ardx.net/connect/'>Contact ARDX</a>
  

includes:
  - errors

search: true
---

# Introduction

Welcome to the ARDX open API. You can use this API to access ARDX project API endpoints, which can provide access information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.



# Authentication

> To authorize, use this code:

```ruby
require 'ardxopen'

api = Ardxopen::APIClient.authorize!('ardxopenapikey')
```

```python
import ardxopen

api = kittn.authorize('ardxopenapikey')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: ardxopenapikey"
```

```javascript
const ardxopen = require('ardxopen');

let api = kittn.authorize('ardxopenapikey');
```

> Make sure to replace `ardxopenapikey` with your API key.

ARDX uses API keys to allow access to the API. You can request a new API key from your project director or by [contacting us](http://ardx.net/connect/).

ARDX expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: ardxopenapikey`

<aside class="notice">
You must replace <code> ardxopenapikey </code> with your personal API key.
</aside>

# Results

## Get All Results

```ruby
require 'ardxopen'

api = Ardxopen::APIClient.authorize!('ardxopenapikey')
api.reqults.get
```

```python
import ardxopen

api = ardxopen.authorize('ardxopenapikey')
api.results.get()
```

```shell
curl "https://ardxopen.net/api/results"
  -H "Authorization: ardxopenapikey"
```

```javascript
const ardxopen = require('ardxopen');

let api = ardxopen.authorize('ardxopenapikey');
let results = api.results.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "survey-alpha",
    "type": "inperson",
    "cohortsize": "623",
    "responserate": "72"
  },
  {
    "id": 2,
    "name": "survey-bravo",
    "type": "email",
    "cohortsize": "1512",
    "responserate": "46"
  }
]
```

This endpoint retrieves all result sets.

### HTTP Request

`GET https://ardxopen.net/api/results`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_retired | false | If set to true, the result will also include inactive (retired) survey result sets.
returnsize | 0 | If set to > 0, request will return first X results

<aside class="success">
Success - survey result list retrieved
</aside>
<aside class="warning">Error message</aside>

## Get a Specific Result set

```ruby
require 'ardxopen'

api = Ardxopen::APIClient.authorize!('ardxopenapikey')
api.results.get(2)
```

```python
import ardxopen

api = ardxopen.authorize('ardxopenapikey')
api.results.get(2)
```

```shell
curl "https://ardxopen.net/api/results/2"
  -H "Authorization: ardxopenapikey"
```

```javascript
const ardxopen = require('ardxopen');

let api = ardxopen.authorize('ardxopenapikey');
let max = api.results.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "survey-bravo",
  "type": "email",
  "cohortsize": "1512",
  "responserate": "46"
}
```

This endpoint retrieves a specific result set.


### HTTP Request

`GET https://ardxopen.net/api/results/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the result set to retrieve

<aside class="success">
Success - survey result list retrieved
</aside>
<aside class="warning">Result set not found</aside>


# ResultItem

## Get All Result Items for a Survey Result

```ruby
require 'ardxopen'

api = Ardxopen::APIClient.authorize!('ardxopenapikey')
api.resultitemss.get(2)
```

```python
import ardxopen

api = ardxopen.authorize('ardxopenapikey')
api.resultitemss.get(2)
```

```shell
curl "https://ardxopen.net/api/resultitemss/2"
  -H "Authorization: ardxopenapikey"
```

```javascript
const ardxopen = require('ardxopen');

let api = ardxopen.authorize('ardxopenapikey');
let max = api.resultitemss.get(2);
```

> The above command returns JSON structured like this:

```json
[
{
    "id": 123456,
    "name": "survey-alpha",
    "response": "true",
    "question1": "yes",
    "question2": "2"
  },
  {
    "id": 234567,
    "name": "survey-bravo",
    "response": "false",
    "question1": "no",
    "question2": "1"
  }
  ]
```

This endpoint retrieves a specific result item.


### HTTP Request

`GET https://ardxopen.net/api/resultitemss/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the result set to retrieve items for

<aside class="success">
Success - survey result item list retrieved
</aside>
<aside class="warning">Result set not found</aside>