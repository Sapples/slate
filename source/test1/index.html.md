---
title: QAPI Services v1.0
language_tabs:
  - ruby: Ruby
  - python: Python
language_clients:
  - ruby: ""
  - python: ""
toc_footers: []
includes: []
search: false
highlight_theme: darkula
headingLevel: 2
generator: widdershins v4.0.1

---

<h1 id="qapi-services">TEST</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Base URLs:

* <a href="/qapi">/qapi</a>

Web: <a href="https://github.com/Iotic-Labs/iotic-spec-qapi">QAPI Spec project</a>

# Authentication

- HTTP Authentication, scheme: bearer

<h1 id="qapi-services-entityservice">EntityService</h1>

## list_all_entities

<a id="opIdlist_all_entities"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.get '/qapi/entities',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.get('/qapi/entities', headers = headers)

print(r.json())

```

`GET /entities`

<h3 id="list_all_entities-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|limit|query|integer(int64)|false|Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:|
|offset|query|integer(int64)|false|Offset from the backend list to start returning values from. In conjunction with limit to control what results the list returns.|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

**limit**: Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:

  - if limit is not supplied or supplied with no limit value, assume default=500

  - if limit is supplied assume max number of entries is whatever specified. The limit value is capped to 1000.

> Example responses

> 200 Response

```json
{
  "entities": [
    {
      "id": {
        "value": "value"
      },
      "name": "name"
    },
    {
      "id": {
        "value": "value"
      },
      "name": "name"
    }
  ]
}
```

<h3 id="list_all_entities-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[entityListAllResponsePayload](#schemaentitylistallresponsepayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## create_entity

<a id="opIdcreate_entity"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.post '/qapi/entities',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.post('/qapi/entities', headers = headers)

print(r.json())

```

`POST /entities`

> Body parameter

```json
{
  "entityId": {
    "value": "value"
  },
  "name": "string"
}
```

<h3 id="create_entity-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|body|body|[entityCreateRequestPayload](#schemaentitycreaterequestpayload)|true|none|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

> Example responses

> 201 Response

```json
{
  "alreadyCreated": true,
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  }
}
```

<h3 id="create_entity-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|A successful response.|[entityCreatedPayload](#schemaentitycreatedpayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|201|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|201|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|201|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|201|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## delete_entity

<a id="opIddelete_entity"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.delete '/qapi/entities/{entityId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.delete('/qapi/entities/{entityId}', headers = headers)

print(r.json())

```

`DELETE /entities/{entityId}`

<h3 id="delete_entity-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|unique id of the entity to delete|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

> Example responses

> 200 Response

```json
{
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  }
}
```

<h3 id="delete_entity-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[entityDeletedPayload](#schemaentitydeletedpayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## describe_entity

<a id="opIddescribe_entity"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.get '/qapi/entities/{entityId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.get('/qapi/entities/{entityId}', headers = headers)

print(r.json())

```

`GET /entities/{entityId}`

<h3 id="describe_entity-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|unique id of the entity to describe|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|lang|query|string|false|Language code for labels and comments (but not values and tags, apart from for value comments).|
|scope|query|[commonScope](#schemacommonscope)|false|- LOCAL: container-local describe - LOCAL_OWN: container-local search of own entities only. Scoped to the user associated to this request - AUTO: equivalent to local and if not found, global|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

#### Enumerated Values

|Parameter|Value|
|---|---|
|scope|GLOBAL|
|scope|LOCAL|
|scope|LOCAL_OWN|
|scope|AUTO|

> Example responses

> 200 Response

```json
{
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  },
  "result": {
    "comment": "comment",
    "label": "label",
    "location": {
      "lat": 0.8008281904610115,
      "lon": 6.027456183070403
    },
    "properties": [
      {
        "key": "key",
        "values": [
          {
            "bvalue": true,
            "dvalue": 1.4658129805029452,
            "ivalue": "ivalue",
            "svalue": "svalue",
            "type": "type"
          },
          {
            "bvalue": true,
            "dvalue": 1.4658129805029452,
            "ivalue": "ivalue",
            "svalue": "svalue",
            "type": "type"
          }
        ]
      },
      {
        "key": "key",
        "values": [
          {
            "bvalue": true,
            "dvalue": 1.4658129805029452,
            "ivalue": "ivalue",
            "svalue": "svalue",
            "type": "type"
          },
          {
            "bvalue": true,
            "dvalue": 1.4658129805029452,
            "ivalue": "ivalue",
            "svalue": "svalue",
            "type": "type"
          }
        ]
      }
    ],
    "tags": [
      "tags",
      "tags"
    ],
    "values": [
      {
        "label": "label",
        "pointId": {
          "value": "value"
        },
        "storesRecent": true
      },
      {
        "label": "label",
        "pointId": {
          "value": "value"
        },
        "storesRecent": true
      }
    ]
  }
}
```

<h3 id="describe_entity-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[entityDescriptionResponsePayload](#schemaentitydescriptionresponsepayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## update_entity

<a id="opIdupdate_entity"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.put '/qapi/entities/{entityId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.put('/qapi/entities/{entityId}', headers = headers)

print(r.json())

```

`PUT /entities/{entityId}`

> Body parameter

```json
{
  "metadata": {
    "format": "string",
    "value": "string"
  },
  "newVisibility": {
    "visibility": "PRIVATE"
  },
  "tags": {
    "added": [
      "string"
    ],
    "deleted": [
      "string"
    ]
  }
}
```

<h3 id="update_entity-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|unique id of the entity to delete|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|body|body|[entityUpdateRequestPayload](#schemaentityupdaterequestpayload)|true|none|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

> Example responses

> 200 Response

```json
{
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  }
}
```

<h3 id="update_entity-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[entityUpdatedPayload](#schemaentityupdatedpayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## list_entity_meta

<a id="opIdlist_entity_meta"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.get '/qapi/entities/{entityId}/meta',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.get('/qapi/entities/{entityId}/meta', headers = headers)

print(r.json())

```

`GET /entities/{entityId}/meta`

<h3 id="list_entity_meta-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|unique id of the entity to describe|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|format|query|string|false|Metadata format.|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

> Example responses

> 200 Response

```json
{
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  },
  "metadata": "metadata"
}
```

<h3 id="list_entity_meta-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[entityMetadataResponsePayload](#schemaentitymetadataresponsepayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## list_entity_tags

<a id="opIdlist_entity_tags"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.get '/qapi/entities/{entityId}/tags',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.get('/qapi/entities/{entityId}/tags', headers = headers)

print(r.json())

```

`GET /entities/{entityId}/tags`

<h3 id="list_entity_tags-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|unique id of the entity to describe|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|limit|query|integer(int64)|false|Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:|
|offset|query|integer(int64)|false|Offset from the backend list to start returning values from. In conjunction with limit to control what results the list returns.|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

**limit**: Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:

  - if limit is not supplied or supplied with no limit value, assume default=500

  - if limit is supplied assume max number of entries is whatever specified. The limit value is capped to 1000.

> Example responses

> 200 Response

```json
{
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  },
  "tags": [
    "tags",
    "tags"
  ]
}
```

<h3 id="list_entity_tags-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[entityTagsResponsePayload](#schemaentitytagsresponsepayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="qapi-services-pointservice">PointService</h1>

## create_control

<a id="opIdcreate_control"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.post '/qapi/entities/{entityId}/controls',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.post('/qapi/entities/{entityId}/controls', headers = headers)

print(r.json())

```

`POST /entities/{entityId}/controls`

> Body parameter

```json
{
  "pointId": {
    "value": "value"
  }
}
```

<h3 id="create_control-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|entity unique ID|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|body|body|[pointCreateControlRequestPayload](#schemapointcreatecontrolrequestpayload)|true|none|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

> Example responses

> 200 Response

```json
{
  "alreadyCreated": true,
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  }
}
```

<h3 id="create_control-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[pointCreatedPayload](#schemapointcreatedpayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## create_feed

<a id="opIdcreate_feed"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.post '/qapi/entities/{entityId}/feeds',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.post('/qapi/entities/{entityId}/feeds', headers = headers)

print(r.json())

```

`POST /entities/{entityId}/feeds`

> Body parameter

```json
{
  "maxSamples": 0,
  "pointId": {
    "value": "value"
  }
}
```

<h3 id="create_feed-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|entity unique ID|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|body|body|[pointCreateFeedRequestPayload](#schemapointcreatefeedrequestpayload)|true|none|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

> Example responses

> 200 Response

```json
{
  "alreadyCreated": true,
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  }
}
```

<h3 id="create_feed-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[pointCreatedPayload](#schemapointcreatedpayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## list_all_points

<a id="opIdlist_all_points"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.get '/qapi/entities/{entityId}/points',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.get('/qapi/entities/{entityId}/points', headers = headers)

print(r.json())

```

`GET /entities/{entityId}/points`

<h3 id="list_all_points-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|entity unique ID|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|pointType|query|string|false|Point Type filter. - FEED - CONTROL|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

#### Enumerated Values

|Parameter|Value|
|---|---|
|pointType|FEED|
|pointType|CONTROL|

> Example responses

> 200 Response

```json
{
  "infoList": [
    {
      "interestCount": 0,
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      }
    },
    {
      "interestCount": 0,
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      }
    }
  ]
}
```

<h3 id="list_all_points-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[pointListAllResponsePayload](#schemapointlistallresponsepayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## delete_point

<a id="opIddelete_point"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.delete '/qapi/entities/{entityId}/points/{pointId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.delete('/qapi/entities/{entityId}/points/{pointId}', headers = headers)

print(r.json())

```

`DELETE /entities/{entityId}/points/{pointId}`

<h3 id="delete_point-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|entity unique ID|
|pointId|path|string|true|point unique ID|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

> Example responses

> 200 Response

```json
{
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  }
}
```

<h3 id="delete_point-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[pointDeletedPayload](#schemapointdeletedpayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## describe_point

<a id="opIddescribe_point"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.get '/qapi/entities/{entityId}/points/{pointId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.get('/qapi/entities/{entityId}/points/{pointId}', headers = headers)

print(r.json())

```

`GET /entities/{entityId}/points/{pointId}`

<h3 id="describe_point-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|entity unique ID|
|pointId|path|string|true|point unique ID|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|lang|query|string|false|Language code for labels and comments (but not values and tags, apart from for value comments).|
|scope|query|[commonScope](#schemacommonscope)|false|- LOCAL: container-local describe - LOCAL_OWN: container-local search of own entities only. Scoped to the user associated to this request - AUTO: equivalent to local and if not found, global|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

#### Enumerated Values

|Parameter|Value|
|---|---|
|scope|GLOBAL|
|scope|LOCAL|
|scope|LOCAL_OWN|
|scope|AUTO|

> Example responses

> 200 Response

```json
{
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  },
  "result": {
    "comment": "comment",
    "label": "label",
    "storesRecent": true,
    "tags": [
      "tags",
      "tags"
    ],
    "values": [
      {
        "comment": "comment",
        "dataType": "dataType",
        "label": "label",
        "unit": "unit"
      },
      {
        "comment": "comment",
        "dataType": "dataType",
        "label": "label",
        "unit": "unit"
      }
    ]
  }
}
```

<h3 id="describe_point-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[pointDescriptionResponsePayload](#schemapointdescriptionresponsepayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## update_point

<a id="opIdupdate_point"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.put '/qapi/entities/{entityId}/points/{pointId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.put('/qapi/entities/{entityId}/points/{pointId}', headers = headers)

print(r.json())

```

`PUT /entities/{entityId}/points/{pointId}`

> Body parameter

```json
{
  "maxSamples": 0,
  "metadata": {
    "format": "string",
    "value": "string"
  },
  "tags": {
    "added": [
      "string"
    ],
    "deleted": [
      "string"
    ]
  }
}
```

<h3 id="update_point-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|entity unique ID|
|pointId|path|string|true|point unique ID|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|body|body|[pointUpdateConfigRequestPayload](#schemapointupdateconfigrequestpayload)|true|none|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

> Example responses

> 200 Response

```json
{
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  }
}
```

<h3 id="update_point-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[pointUpdatedPayload](#schemapointupdatedpayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## list_point_metadata

<a id="opIdlist_point_metadata"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.get '/qapi/entities/{entityId}/points/{pointId}/meta',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.get('/qapi/entities/{entityId}/points/{pointId}/meta', headers = headers)

print(r.json())

```

`GET /entities/{entityId}/points/{pointId}/meta`

<h3 id="list_point_metadata-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|entity unique ID|
|pointId|path|string|true|point unique ID|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|format|query|string|false|Metadata format.|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

> Example responses

> 200 Response

```json
{
  "metadata": "metadata",
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  }
}
```

<h3 id="list_point_metadata-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[pointMetadataResponsePayload](#schemapointmetadataresponsepayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## list_point_tags

<a id="opIdlist_point_tags"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.get '/qapi/entities/{entityId}/points/{pointId}/tags',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.get('/qapi/entities/{entityId}/points/{pointId}/tags', headers = headers)

print(r.json())

```

`GET /entities/{entityId}/points/{pointId}/tags`

<h3 id="list_point_tags-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|entity unique ID|
|pointId|path|string|true|point unique ID|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|limit|query|integer(int64)|false|Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:|
|offset|query|integer(int64)|false|Offset from the backend list to start returning values from. In conjunction with limit to control what results the list returns.|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

**limit**: Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:

  - if limit is not supplied or supplied with no limit value, assume default=500

  - if limit is supplied assume max number of entries is whatever specified. The limit value is capped to 1000.

> Example responses

> 200 Response

```json
{
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  },
  "tags": [
    "tags",
    "tags"
  ]
}
```

<h3 id="list_point_tags-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[pointTagsResponsePayload](#schemapointtagsresponsepayload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="qapi-services-interestservice">InterestService</h1>

## list_all_interests

<a id="opIdlist_all_interests"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.get '/qapi/entities/{entityId}/interests',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.get('/qapi/entities/{entityId}/interests', headers = headers)

print(r.json())

```

`GET /entities/{entityId}/interests`

<h3 id="list_all_interests-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|entityId|path|string|true|Entity unique ID|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|limit|query|integer(int64)|false|Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:|
|offset|query|integer(int64)|false|Offset from the backend list to start returning values from. In conjunction with limit to control what results the list returns.|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

**limit**: Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:

  - if limit is not supplied or supplied with no limit value, assume default=500

  - if limit is supplied assume max number of entries is whatever specified. The limit value is capped to 1000.

> Example responses

> 200 Response

```json
{
  "interests": [
    {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      },
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      }
    },
    {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      },
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      }
    }
  ]
}
```

<h3 id="list_all_interests-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[qapiinterestListAllResponsePayload](#schemaqapiinterestlistallresponsepayload)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="qapi-services-pingservice">PingService</h1>

## ping

<a id="opIdping"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get '/qapi/ping',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('/qapi/ping', headers = headers)

print(r.json())

```

`GET /ping`

> Example responses

> 200 Response

```json
{
  "serverTime": "2000-01-23T04:56:07Z",
  "version": {
    "patch": 1,
    "major": 0,
    "minor": 6,
    "build": "build"
  },
  "status": {
    "code": 0,
    "details": [
      {
        "type_url": "type_url",
        "value": "value"
      },
      {
        "type_url": "type_url",
        "value": "value"
      }
    ],
    "message": "message"
  }
}
```

<h3 id="ping-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.|[pingPingResponse](#schemapingpingresponse)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="qapi-services-searchservice">SearchService</h1>

## dispatch

<a id="opIddispatch"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string'
}

result = RestClient.post '/qapi/searches/dispatches',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string'
}

r = requests.post('/qapi/searches/dispatches', headers = headers)

print(r.json())

```

`POST /searches/dispatches`

> Body parameter

```json
{
  "expiryTimeout": "2019-08-24T14:15:22Z",
  "location": {
    "location": {
      "lat": 0.8008281904610115,
      "lon": 6.027456183070403
    },
    "radiusKm": 0
  },
  "responseType": "FULL",
  "text": "string",
  "unit": "string"
}
```

<h3 id="dispatch-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|lang|query|string|false|Language code for labels and comments (but not values and tags, apart from for value comments).|
|scope|query|[commonScope](#schemacommonscope)|false|- LOCAL: container-local describe - LOCAL_OWN: container-local search of own entities only. Scoped to the user associated to this request - AUTO: equivalent to local and if not found, global|
|limit|query|integer(int64)|false|Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:|
|offset|query|integer(int64)|false|Offset from the backend list to start returning values from. In conjunction with limit to control what results the list returns.|
|body|body|[searchRequestPayload](#schemasearchrequestpayload)|true|none|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

**limit**: Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:

  - if limit is not supplied or supplied with no limit value, assume default=500

  - if limit is supplied assume max number of entries is whatever specified. The limit value is capped to 1000.

#### Enumerated Values

|Parameter|Value|
|---|---|
|scope|GLOBAL|
|scope|LOCAL|
|scope|LOCAL_OWN|
|scope|AUTO|

> Example responses

> 400 Response

```json
{
  "code": 0,
  "details": [
    {
      "type_url": "string",
      "value": {}
    }
  ],
  "error": "string",
  "message": "string"
}
```

<h3 id="dispatch-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|A successful response.|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|202|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|202|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|202|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|202|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

## receive_for

<a id="opIdreceive_for"></a>

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Iotics-ClientRef' => 'string',
  'Iotics-ClientAppId' => 'string',
  'Iotics-TransactionRef' => 'string',
  'Iotics-ConsumerGroup' => 'string',
  'Iotics-RequestTimeout' => '2019-08-24T14:15:22Z'
}

result = RestClient.post '/qapi/searches/requests',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Iotics-ClientRef': 'string',
  'Iotics-ClientAppId': 'string',
  'Iotics-TransactionRef': 'string',
  'Iotics-ConsumerGroup': 'string',
  'Iotics-RequestTimeout': '2019-08-24T14:15:22Z'
}

r = requests.post('/qapi/searches/requests', headers = headers)

print(r.json())

```

`POST /searches/requests`

> Body parameter

```json
{
  "expiryTimeout": "2019-08-24T14:15:22Z",
  "location": {
    "location": {
      "lat": 0.8008281904610115,
      "lon": 6.027456183070403
    },
    "radiusKm": 0
  },
  "responseType": "FULL",
  "text": "string",
  "unit": "string"
}
```

<h3 id="receive_for-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|Iotics-ClientRef|header|string|true|Applies to all requests and solicited responses|
|Iotics-ClientAppId|header|string|true|Applies to requests to provide a namespace for the application within which all the requests/responses are grouped irrespective of the clientRef|
|Iotics-TransactionRef|header|string|false|Used to loosely link requests/responses in a distributed environment each layer can add its own id to the list. Transaction ref is limited to a max of 16 elements per list and, for each list item, a max length of 36 characters|
|Iotics-ConsumerGroup|header|string|false|consumer group (for group listener, optional)|
|Iotics-RequestTimeout|header|string(date-time)|true|client request timeout TODO: verify if we want this here|
|lang|query|string|false|Language code for labels and comments (but not values and tags, apart from for value comments).|
|scope|query|[commonScope](#schemacommonscope)|false|- LOCAL: container-local describe - LOCAL_OWN: container-local search of own entities only. Scoped to the user associated to this request - AUTO: equivalent to local and if not found, global|
|limit|query|integer(int64)|false|Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:|
|offset|query|integer(int64)|false|Offset from the backend list to start returning values from. In conjunction with limit to control what results the list returns.|
|body|body|[searchRequestPayload](#schemasearchrequestpayload)|true|none|

#### Detailed descriptions

**Iotics-ClientRef**: Applies to all requests and solicited responses
modelled as list to allow clients to represent the ref
as a linked set of elements
we will be using this to map to internal queues and
provide namespace scopes

**limit**: Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results. The use of "Limit" is:

  - if limit is not supplied or supplied with no limit value, assume default=500

  - if limit is supplied assume max number of entries is whatever specified. The limit value is capped to 1000.

#### Enumerated Values

|Parameter|Value|
|---|---|
|scope|GLOBAL|
|scope|LOCAL|
|scope|LOCAL_OWN|
|scope|AUTO|

> Example responses

> 200 Response

```json
{
  "error": {
    "details": [
      {
        "type_url": "type_url",
        "value": "value"
      },
      {
        "type_url": "type_url",
        "value": "value"
      }
    ],
    "grpc_code": 5,
    "http_code": 5,
    "http_status": "http_status",
    "message": "message"
  },
  "result": {
    "headers": {
      "clientAppId": "clientAppId",
      "clientRef": "clientRef",
      "consumerGroup": "consumerGroup",
      "requestTimeout": "2000-01-23T04:56:07Z",
      "transactionRef": [
        "transactionRef",
        "transactionRef"
      ]
    },
    "payload": {
      "entities": [
        {
          "id": {
            "value": "value"
          },
          "label": "label",
          "location": {
            "lat": 6.027456183070403,
            "lon": 1.4658129805029452
          },
          "points": [
            {
              "label": "label",
              "point": {
                "key": {
                  "entityId": {
                    "value": "value"
                  },
                  "id": {
                    "value": "value"
                  }
                }
              },
              "storesRecent": true
            },
            {
              "label": "label",
              "point": {
                "key": {
                  "entityId": {
                    "value": "value"
                  },
                  "id": {
                    "value": "value"
                  }
                }
              },
              "storesRecent": true
            }
          ]
        },
        {
          "id": {
            "value": "value"
          },
          "label": "label",
          "location": {
            "lat": 6.027456183070403,
            "lon": 1.4658129805029452
          },
          "points": [
            {
              "label": "label",
              "point": {
                "key": {
                  "entityId": {
                    "value": "value"
                  },
                  "id": {
                    "value": "value"
                  }
                }
              },
              "storesRecent": true
            },
            {
              "label": "label",
              "point": {
                "key": {
                  "entityId": {
                    "value": "value"
                  },
                  "id": {
                    "value": "value"
                  }
                }
              },
              "storesRecent": true
            }
          ]
        }
      ],
      "status": {
        "code": 0,
        "details": [
          {
            "type_url": "type_url",
            "value": "value"
          },
          {
            "type_url": "type_url",
            "value": "value"
          }
        ],
        "message": "message"
      }
    }
  }
}
```

<h3 id="receive_for-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A successful response.(streaming responses)|[Stream_result_of_qapisearchResponse](#schemastream_result_of_qapisearchresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Invalid request|[runtimeError](#schemaruntimeerror)|
|422|[Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)|Unprocessable entity|[runtimeError](#schemaruntimeerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal server error|[runtimeError](#schemaruntimeerror)|
|default|Default|An unexpected error response|[runtimeError](#schemaruntimeerror)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|200|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|200|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|200|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|400|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|400|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|400|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|400|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|422|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|422|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|422|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|422|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|500|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|500|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|500|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|500|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|
|default|Iotics-ClientAppId|string||Iotics-ClientAppId from the request|
|default|Iotics-ClientRef|string||Iotics-ClientRef from the request|
|default|Iotics-ConsumerGroup|string||Iotics-ConsumerGroup from the request|
|default|Iotics-TransactionRef|string||Iotics-TransactionRef from the request (optionnally enriched accross the layers)|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocS_ListAllRequestPointTypeValue">ListAllRequestPointTypeValue</h2>

<a id="schemalistallrequestpointtypevalue"></a>
<a id="schema_ListAllRequestPointTypeValue"></a>
<a id="tocSlistallrequestpointtypevalue"></a>
<a id="tocslistallrequestpointtypevalue"></a>

```json
{
  "pointType": "FEED"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|pointType|[commonPointType](#schemacommonpointtype)|false|none|A point type|

<h2 id="tocS_PayloadVisibilityValue">PayloadVisibilityValue</h2>

<a id="schemapayloadvisibilityvalue"></a>
<a id="schema_PayloadVisibilityValue"></a>
<a id="tocSpayloadvisibilityvalue"></a>
<a id="tocspayloadvisibilityvalue"></a>

```json
{
  "visibility": "PRIVATE"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|visibility|[commonVisibility](#schemacommonvisibility)|false|none|none|

<h2 id="tocS_PointKey">PointKey</h2>

<a id="schemapointkey"></a>
<a id="schema_PointKey"></a>
<a id="tocSpointkey"></a>
<a id="tocspointkey"></a>

```json
{
  "entityId": {
    "value": "value"
  },
  "id": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|
|id|[commonPointID](#schemacommonpointid)|false|none|none|

<h2 id="tocS_ResponseEntityDetails">ResponseEntityDetails</h2>

<a id="schemaresponseentitydetails"></a>
<a id="schema_ResponseEntityDetails"></a>
<a id="tocSresponseentitydetails"></a>
<a id="tocsresponseentitydetails"></a>

```json
{
  "id": {
    "value": "value"
  },
  "label": "label",
  "location": {
    "lat": 6.027456183070403,
    "lon": 1.4658129805029452
  },
  "points": [
    {
      "label": "label",
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      },
      "storesRecent": true
    },
    {
      "label": "label",
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      },
      "storesRecent": true
    }
  ]
}

```

details of the entity found

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|[commonEntityID](#schemacommonentityid)|false|none|none|
|label|string|false|none|a human readable label in the language specified in the request (if available)|
|location|[commonGeoLocation](#schemacommongeolocation)|false|none|Location of e.g. Iotic Things|
|points|[[ResponsePointDetails](#schemaresponsepointdetails)]|false|none|points' details (mandatory in REDUCED)|

<h2 id="tocS_ResponsePointDetails">ResponsePointDetails</h2>

<a id="schemaresponsepointdetails"></a>
<a id="schema_ResponsePointDetails"></a>
<a id="tocSresponsepointdetails"></a>
<a id="tocsresponsepointdetails"></a>

```json
{
  "label": "label",
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  },
  "storesRecent": true
}

```

details of a point found

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|label|string|false|none|a human readable label in the language specified in the request (if available)|
|point|[pointPoint](#schemapointpoint)|false|none|A point (alias for feed or control)|
|storesRecent|boolean(boolean)|false|none|whether offers recent data|

<h2 id="tocS_Stream_result_of_qapisearchResponse">Stream_result_of_qapisearchResponse</h2>

<a id="schemastream_result_of_qapisearchresponse"></a>
<a id="schema_Stream_result_of_qapisearchResponse"></a>
<a id="tocSstream_result_of_qapisearchresponse"></a>
<a id="tocsstream_result_of_qapisearchresponse"></a>

```json
{
  "error": {
    "details": [
      {
        "type_url": "type_url",
        "value": "value"
      },
      {
        "type_url": "type_url",
        "value": "value"
      }
    ],
    "grpc_code": 5,
    "http_code": 5,
    "http_status": "http_status",
    "message": "message"
  },
  "result": {
    "headers": {
      "clientAppId": "clientAppId",
      "clientRef": "clientRef",
      "consumerGroup": "consumerGroup",
      "requestTimeout": "2000-01-23T04:56:07Z",
      "transactionRef": [
        "transactionRef",
        "transactionRef"
      ]
    },
    "payload": {
      "entities": [
        {
          "id": {
            "value": "value"
          },
          "label": "label",
          "location": {
            "lat": 6.027456183070403,
            "lon": 1.4658129805029452
          },
          "points": [
            {
              "label": "label",
              "point": {
                "key": {
                  "entityId": {
                    "value": "value"
                  },
                  "id": {
                    "value": "value"
                  }
                }
              },
              "storesRecent": true
            },
            {
              "label": "label",
              "point": {
                "key": {
                  "entityId": {
                    "value": "value"
                  },
                  "id": {
                    "value": "value"
                  }
                }
              },
              "storesRecent": true
            }
          ]
        },
        {
          "id": {
            "value": "value"
          },
          "label": "label",
          "location": {
            "lat": 6.027456183070403,
            "lon": 1.4658129805029452
          },
          "points": [
            {
              "label": "label",
              "point": {
                "key": {
                  "entityId": {
                    "value": "value"
                  },
                  "id": {
                    "value": "value"
                  }
                }
              },
              "storesRecent": true
            },
            {
              "label": "label",
              "point": {
                "key": {
                  "entityId": {
                    "value": "value"
                  },
                  "id": {
                    "value": "value"
                  }
                }
              },
              "storesRecent": true
            }
          ]
        }
      ],
      "status": {
        "code": 0,
        "details": [
          {
            "type_url": "type_url",
            "value": "value"
          },
          {
            "type_url": "type_url",
            "value": "value"
          }
        ],
        "message": "message"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|error|[runtimeStreamError](#schemaruntimestreamerror)|false|none|none|
|result|[qapisearchResponse](#schemaqapisearchresponse)|false|none|the search response. In the registrar based iotic platform a Respose contains ALL matching entities in the local <br />subspace and all public in the registrar.<br />In the decentralised iotics operating env, each node in the network generates a response and the client is expected to <br />receive a stream of response messages.<br />`matches` and `owner` attributes have been removed from the original qapi spec in infra/v1 as they're not used.<br />depending on the desired ResponseType in the request, not all attributes in the entity details are specified (see comments).<br />Another difference between results from centralised v decentralised backends is the interpretation of range. The single <br />response provided by the centralised backend has the entities ordered and produced according to the (optional) range<br />in the request. In a decentralised network, range has limited use and the offset attribute is ignored.|

<h2 id="tocS_commonEntityID">commonEntityID</h2>

<a id="schemacommonentityid"></a>
<a id="schema_commonEntityID"></a>
<a id="tocScommonentityid"></a>
<a id="tocscommonentityid"></a>

```json
{
  "value": "value"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|value|string|false|none|Entity Identifier (in V1 the EntityID is always the UUID)|

<h2 id="tocS_commonFeedDataItem">commonFeedDataItem</h2>

<a id="schemacommonfeeddataitem"></a>
<a id="schema_commonFeedDataItem"></a>
<a id="tocScommonfeeddataitem"></a>
<a id="tocscommonfeeddataitem"></a>

```json
{
  "data": "string",
  "feedId": "string",
  "mime": "string",
  "time": "2019-08-24T14:15:22Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|string(byte)|false|none|feed data|
|feedId|string|false|none|globally unique id of feed which has shared this data|
|mime|string|false|none|Mime type of data. ASCII encoded of length 1 <= n <= 64 bytes|
|time|string(date-time)|false|none|UTC timestamp for share, in ISO 8601 format (YYYY-MM-DDTHH:MM:SS.ssssssZ), e.g. 2016-10-23T15:22:37.500000Z.|

<h2 id="tocS_commonGeoCircle">commonGeoCircle</h2>

<a id="schemacommongeocircle"></a>
<a id="schema_commonGeoCircle"></a>
<a id="tocScommongeocircle"></a>
<a id="tocscommongeocircle"></a>

```json
{
  "location": {
    "lat": 0.8008281904610115,
    "lon": 6.027456183070403
  },
  "radiusKm": 0
}

```

Approximate location, e.g. for search reduction

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|location|[commonGeoLocation](#schemacommongeolocation)|false|none|Location of e.g. Iotic Things|
|radiusKm|number(double)|false|none|none|

<h2 id="tocS_commonGeoLocation">commonGeoLocation</h2>

<a id="schemacommongeolocation"></a>
<a id="schema_commonGeoLocation"></a>
<a id="tocScommongeolocation"></a>
<a id="tocscommongeolocation"></a>

```json
{
  "lat": 0.8008281904610115,
  "lon": 6.027456183070403
}

```

Location of e.g. Iotic Things

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|lat|number(double)|false|none|none|
|lon|number(double)|false|none|none|

<h2 id="tocS_commonHeaders">commonHeaders</h2>

<a id="schemacommonheaders"></a>
<a id="schema_commonHeaders"></a>
<a id="tocScommonheaders"></a>
<a id="tocscommonheaders"></a>

```json
{
  "clientAppId": "clientAppId",
  "clientRef": "clientRef",
  "consumerGroup": "consumerGroup",
  "requestTimeout": "2000-01-23T04:56:07Z",
  "transactionRef": [
    "transactionRef",
    "transactionRef"
  ]
}

```

Common Header definitions
Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|clientAppId|string|false|none|Applies to requests to provide a namespace for the application<br />within which all the requests/responses are grouped irrespective <br />of the clientRef|
|clientRef|string|false|none|Applies to all requests and solicited responses<br />modelled as list to allow clients to represent the ref<br />as a linked set of elements<br />we will be using this to map to internal queues and<br />provide namespace scopes|
|consumerGroup|string|false|none|consumer group (for group listener, optional)|
|requestTimeout|string(date-time)|false|none|client request timeout TODO: verify if we want this here|
|transactionRef|[string]|false|none|Used to loosely link requests/responses in a distributed environment<br />each layer can add its own id to the list. Transaction ref is limited to<br />a max of 16 elements per list and, for each list item, a max length of 36 <br />characters|

<h2 id="tocS_commonInterestID">commonInterestID</h2>

<a id="schemacommoninterestid"></a>
<a id="schema_commonInterestID"></a>
<a id="tocScommoninterestid"></a>
<a id="tocscommoninterestid"></a>

```json
{
  "value": "value"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|value|string|false|none|Interest Identifier (in V1 the PointID is always the UUID)|

<h2 id="tocS_commonLimit">commonLimit</h2>

<a id="schemacommonlimit"></a>
<a id="schema_commonLimit"></a>
<a id="tocScommonlimit"></a>
<a id="tocscommonlimit"></a>

```json
{
  "value": 0
}

```

Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results.
The use of "Limit" is:
- if limit is not supplied or supplied with no limit value, assume default=500
- if limit is supplied assume max number of entries is whatever specified. The limit value is capped to 1000.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|value|integer(int64)|false|none|max number of results|

<h2 id="tocS_commonMetadata">commonMetadata</h2>

<a id="schemacommonmetadata"></a>
<a id="schema_commonMetadata"></a>
<a id="tocScommonmetadata"></a>
<a id="tocscommonmetadata"></a>

```json
{
  "format": "string",
  "value": "string"
}

```

metadata type - generic databag for setting metadata of resources.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|format|string|false|none|format of metadata value <br />Metadata for points and values cannot be set here - this request is for describing the entity itself only.|
|value|string|false|none|new metadata value|

<h2 id="tocS_commonOffset">commonOffset</h2>

<a id="schemacommonoffset"></a>
<a id="schema_commonOffset"></a>
<a id="tocScommonoffset"></a>
<a id="tocscommonoffset"></a>

```json
{
  "value": 0
}

```

Offset from the backend list to start returning values from. In conjunction with limit to control what results the list returns.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|value|integer(int64)|false|none|none|

<h2 id="tocS_commonPointID">commonPointID</h2>

<a id="schemacommonpointid"></a>
<a id="schema_commonPointID"></a>
<a id="tocScommonpointid"></a>
<a id="tocscommonpointid"></a>

```json
{
  "value": "value"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|value|string|false|none|Point Identifier (in V1 the PointID is always the UUID)|

<h2 id="tocS_commonPointType">commonPointType</h2>

<a id="schemacommonpointtype"></a>
<a id="schema_commonPointType"></a>
<a id="tocScommonpointtype"></a>
<a id="tocscommonpointtype"></a>

```json
"FEED"

```

A point type

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|A point type|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|FEED|
|*anonymous*|CONTROL|

<h2 id="tocS_commonPropertyList">commonPropertyList</h2>

<a id="schemacommonpropertylist"></a>
<a id="schema_commonPropertyList"></a>
<a id="tocScommonpropertylist"></a>
<a id="tocscommonpropertylist"></a>

```json
{
  "key": "key",
  "values": [
    {
      "bvalue": true,
      "dvalue": 1.4658129805029452,
      "ivalue": "ivalue",
      "svalue": "svalue",
      "type": "type"
    },
    {
      "bvalue": true,
      "dvalue": 1.4658129805029452,
      "ivalue": "ivalue",
      "svalue": "svalue",
      "type": "type"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|key|string|false|none|none|
|values|[[commonPropertyValue](#schemacommonpropertyvalue)]|false|none|none|

<h2 id="tocS_commonPropertyValue">commonPropertyValue</h2>

<a id="schemacommonpropertyvalue"></a>
<a id="schema_commonPropertyValue"></a>
<a id="tocScommonpropertyvalue"></a>
<a id="tocscommonpropertyvalue"></a>

```json
{
  "bvalue": true,
  "dvalue": 1.4658129805029452,
  "ivalue": "ivalue",
  "svalue": "svalue",
  "type": "type"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bvalue|boolean(boolean)|false|none|none|
|dvalue|number(double)|false|none|none|
|ivalue|string(int64)|false|none|none|
|svalue|string|false|none|none|
|type|string|false|none|none|

<h2 id="tocS_commonRange">commonRange</h2>

<a id="schemacommonrange"></a>
<a id="schema_commonRange"></a>
<a id="tocScommonrange"></a>
<a id="tocscommonrange"></a>

```json
{
  "limit": {
    "value": 0
  },
  "offset": {
    "value": 0
  }
}

```

Range if specified *may* be obliged by the backend

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|limit|[commonLimit](#schemacommonlimit)|false|none|Configuration for result limits. Some requests may return many results; in such cases the client may ask to limit the number of results.<br />The use of "Limit" is:<br />- if limit is not supplied or supplied with no limit value, assume default=500<br />- if limit is supplied assume max number of entries is whatever specified. The limit value is capped to 1000.|
|offset|[commonOffset](#schemacommonoffset)|false|none|Offset from the backend list to start returning values from. In conjunction with limit to control what results the list returns.|

<h2 id="tocS_commonScope">commonScope</h2>

<a id="schemacommonscope"></a>
<a id="schema_commonScope"></a>
<a id="tocScommonscope"></a>
<a id="tocscommonscope"></a>

```json
"GLOBAL"

```

- LOCAL: container-local describe
 - LOCAL_OWN: container-local search of own entities only. Scoped to the user associated to this request
 - AUTO: equivalent to local and if not found, global

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|- LOCAL: container-local describe<br /> - LOCAL_OWN: container-local search of own entities only. Scoped to the user associated to this request<br /> - AUTO: equivalent to local and if not found, global|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|GLOBAL|
|*anonymous*|LOCAL|
|*anonymous*|LOCAL_OWN|
|*anonymous*|AUTO|

<h2 id="tocS_commonTags">commonTags</h2>

<a id="schemacommontags"></a>
<a id="schema_commonTags"></a>
<a id="tocScommontags"></a>
<a id="tocscommontags"></a>

```json
{
  "added": [
    "string"
  ],
  "deleted": [
    "string"
  ]
}

```

list of tags to be added and deleted. if a tag appears in both lists,
applications may choose to ignore the tags or throw some error

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|added|[string]|false|none|list of tags to be added|
|deleted|[string]|false|none|list of tags to be deleted|

<h2 id="tocS_commonVersion">commonVersion</h2>

<a id="schemacommonversion"></a>
<a id="schema_commonVersion"></a>
<a id="tocScommonversion"></a>
<a id="tocscommonversion"></a>

```json
{
  "patch": 1,
  "major": 0,
  "minor": 6,
  "build": "build"
}

```

Version represents the version of this API

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|build|string|false|none|none|
|major|integer(int64)|false|none|none|
|minor|integer(int64)|false|none|none|
|patch|integer(int64)|false|none|none|

<h2 id="tocS_commonVisibility">commonVisibility</h2>

<a id="schemacommonvisibility"></a>
<a id="schema_commonVisibility"></a>
<a id="tocScommonvisibility"></a>
<a id="tocscommonvisibility"></a>

```json
"PRIVATE"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|PRIVATE|
|*anonymous*|PUBLIC|

<h2 id="tocS_entityCreateRequest">entityCreateRequest</h2>

<a id="schemaentitycreaterequest"></a>
<a id="schema_entityCreateRequest"></a>
<a id="tocSentitycreaterequest"></a>
<a id="tocsentitycreaterequest"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "entityId": {
      "value": "value"
    },
    "name": "string"
  }
}

```

Create an interest in a global or local point

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[entityCreateRequestPayload](#schemaentitycreaterequestpayload)|false|none|none|

<h2 id="tocS_entityCreateRequestPayload">entityCreateRequestPayload</h2>

<a id="schemaentitycreaterequestpayload"></a>
<a id="schema_entityCreateRequestPayload"></a>
<a id="tocSentitycreaterequestpayload"></a>
<a id="tocsentitycreaterequestpayload"></a>

```json
{
  "entityId": {
    "value": "value"
  },
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|
|name|string|false|none|none|

<h2 id="tocS_entityCreated">entityCreated</h2>

<a id="schemaentitycreated"></a>
<a id="schema_entityCreated"></a>
<a id="tocSentitycreated"></a>
<a id="tocsentitycreated"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "alreadyCreated": true,
    "entity": {
      "id": {
        "value": "value"
      },
      "name": "name"
    }
  }
}

```

Event sent to the requestor when the request of create is OK.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[entityCreatedPayload](#schemaentitycreatedpayload)|false|none|none|

<h2 id="tocS_entityCreatedPayload">entityCreatedPayload</h2>

<a id="schemaentitycreatedpayload"></a>
<a id="schema_entityCreatedPayload"></a>
<a id="tocSentitycreatedpayload"></a>
<a id="tocsentitycreatedpayload"></a>

```json
{
  "alreadyCreated": true,
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|alreadyCreated|boolean(boolean)|false|none|whether the entity exists already (creating an existing entity is idempotent). Optional, with default=false|
|entity|[entityEntity](#schemaentityentity)|false|none|An entity is the virtual representation of a (physical, purely virtual or hybrid) device,<br />is only ever located in the node it was created. <br />API-visible (non-metadata) attributes of an entity are: id, label, visibility<br />when visibility=public, any metadata set for this entity (and thus also for its feeds, controls, etc.) <br />should be visible to the world.|

<h2 id="tocS_entityDeleteRequest">entityDeleteRequest</h2>

<a id="schemaentitydeleterequest"></a>
<a id="schema_entityDeleteRequest"></a>
<a id="tocSentitydeleterequest"></a>
<a id="tocsentitydeleterequest"></a>

```json
{
  "args": {
    "entityId": {
      "value": "value"
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  }
}

```

Delete an entity.  Any EPs containing at least one entity which has a subscription to a point
belonging to the deleted entity (including entity-assigned EP) will receive an unsolicited Deleted
message containing a list of interests which have been deleted. See also interestss deletion.
The Entity-assigned EP will not be notified about deleted interests where the subscriber is not in the same EP.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[entityDeleteRequestArguments](#schemaentitydeleterequestarguments)|false|none|none|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|

<h2 id="tocS_entityDeleteRequestArguments">entityDeleteRequestArguments</h2>

<a id="schemaentitydeleterequestarguments"></a>
<a id="schema_entityDeleteRequestArguments"></a>
<a id="tocSentitydeleterequestarguments"></a>
<a id="tocsentitydeleterequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|

<h2 id="tocS_entityDeleted">entityDeleted</h2>

<a id="schemaentitydeleted"></a>
<a id="schema_entityDeleted"></a>
<a id="tocSentitydeleted"></a>
<a id="tocsentitydeleted"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "entity": {
      "id": {
        "value": "value"
      },
      "name": "name"
    }
  }
}

```

Event sent to the requestor when the request of delete is OK.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[entityDeletedPayload](#schemaentitydeletedpayload)|false|none|none|

<h2 id="tocS_entityDeletedPayload">entityDeletedPayload</h2>

<a id="schemaentitydeletedpayload"></a>
<a id="schema_entityDeletedPayload"></a>
<a id="tocSentitydeletedpayload"></a>
<a id="tocsentitydeletedpayload"></a>

```json
{
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entity|[entityEntity](#schemaentityentity)|false|none|An entity is the virtual representation of a (physical, purely virtual or hybrid) device,<br />is only ever located in the node it was created. <br />API-visible (non-metadata) attributes of an entity are: id, label, visibility<br />when visibility=public, any metadata set for this entity (and thus also for its feeds, controls, etc.) <br />should be visible to the world.|

<h2 id="tocS_entityDescriptionRequest">entityDescriptionRequest</h2>

<a id="schemaentitydescriptionrequest"></a>
<a id="schema_entityDescriptionRequest"></a>
<a id="tocSentitydescriptionrequest"></a>
<a id="tocsentitydescriptionrequest"></a>

```json
{
  "args": {
    "entityId": {
      "value": "value"
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "lang": "string",
  "scope": "GLOBAL"
}

```

Description of entities: Provides public metadata lookup for individual resources

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[entityDescriptionRequestArguments](#schemaentitydescriptionrequestarguments)|false|none|Only one action argument is necessary.|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|lang|string|false|none|Language code for labels and comments (but not values and tags, apart from for value comments).|
|scope|[commonScope](#schemacommonscope)|false|none|- LOCAL: container-local describe<br /> - LOCAL_OWN: container-local search of own entities only. Scoped to the user associated to this request<br /> - AUTO: equivalent to local and if not found, global|

<h2 id="tocS_entityDescriptionRequestArguments">entityDescriptionRequestArguments</h2>

<a id="schemaentitydescriptionrequestarguments"></a>
<a id="schema_entityDescriptionRequestArguments"></a>
<a id="tocSentitydescriptionrequestarguments"></a>
<a id="tocsentitydescriptionrequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  }
}

```

Only one action argument is necessary.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|

<h2 id="tocS_entityDescriptionResponse">entityDescriptionResponse</h2>

<a id="schemaentitydescriptionresponse"></a>
<a id="schema_entityDescriptionResponse"></a>
<a id="tocSentitydescriptionresponse"></a>
<a id="tocsentitydescriptionresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "entity": {
      "id": {
        "value": "value"
      },
      "name": "name"
    },
    "result": {
      "comment": "comment",
      "label": "label",
      "location": {
        "lat": 0.8008281904610115,
        "lon": 6.027456183070403
      },
      "properties": [
        {
          "key": "key",
          "values": [
            {
              "bvalue": true,
              "dvalue": 1.4658129805029452,
              "ivalue": "ivalue",
              "svalue": "svalue",
              "type": "type"
            },
            {
              "bvalue": true,
              "dvalue": 1.4658129805029452,
              "ivalue": "ivalue",
              "svalue": "svalue",
              "type": "type"
            }
          ]
        },
        {
          "key": "key",
          "values": [
            {
              "bvalue": true,
              "dvalue": 1.4658129805029452,
              "ivalue": "ivalue",
              "svalue": "svalue",
              "type": "type"
            },
            {
              "bvalue": true,
              "dvalue": 1.4658129805029452,
              "ivalue": "ivalue",
              "svalue": "svalue",
              "type": "type"
            }
          ]
        }
      ],
      "tags": [
        "tags",
        "tags"
      ],
      "values": [
        {
          "label": "label",
          "pointId": {
            "value": "value"
          },
          "storesRecent": true
        },
        {
          "label": "label",
          "pointId": {
            "value": "value"
          },
          "storesRecent": true
        }
      ]
    }
  }
}

```

the response for a description request on this entity

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[entityDescriptionResponsePayload](#schemaentitydescriptionresponsepayload)|false|none|none|

<h2 id="tocS_entityDescriptionResponsePayload">entityDescriptionResponsePayload</h2>

<a id="schemaentitydescriptionresponsepayload"></a>
<a id="schema_entityDescriptionResponsePayload"></a>
<a id="tocSentitydescriptionresponsepayload"></a>
<a id="tocsentitydescriptionresponsepayload"></a>

```json
{
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  },
  "result": {
    "comment": "comment",
    "label": "label",
    "location": {
      "lat": 0.8008281904610115,
      "lon": 6.027456183070403
    },
    "properties": [
      {
        "key": "key",
        "values": [
          {
            "bvalue": true,
            "dvalue": 1.4658129805029452,
            "ivalue": "ivalue",
            "svalue": "svalue",
            "type": "type"
          },
          {
            "bvalue": true,
            "dvalue": 1.4658129805029452,
            "ivalue": "ivalue",
            "svalue": "svalue",
            "type": "type"
          }
        ]
      },
      {
        "key": "key",
        "values": [
          {
            "bvalue": true,
            "dvalue": 1.4658129805029452,
            "ivalue": "ivalue",
            "svalue": "svalue",
            "type": "type"
          },
          {
            "bvalue": true,
            "dvalue": 1.4658129805029452,
            "ivalue": "ivalue",
            "svalue": "svalue",
            "type": "type"
          }
        ]
      }
    ],
    "tags": [
      "tags",
      "tags"
    ],
    "values": [
      {
        "label": "label",
        "pointId": {
          "value": "value"
        },
        "storesRecent": true
      },
      {
        "label": "label",
        "pointId": {
          "value": "value"
        },
        "storesRecent": true
      }
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entity|[entityEntity](#schemaentityentity)|false|none|An entity is the virtual representation of a (physical, purely virtual or hybrid) device,<br />is only ever located in the node it was created. <br />API-visible (non-metadata) attributes of an entity are: id, label, visibility<br />when visibility=public, any metadata set for this entity (and thus also for its feeds, controls, etc.) <br />should be visible to the world.|
|result|[entityMetaResult](#schemaentitymetaresult)|false|none|Metadata result data bag for this point|

<h2 id="tocS_entityEntity">entityEntity</h2>

<a id="schemaentityentity"></a>
<a id="schema_entityEntity"></a>
<a id="tocSentityentity"></a>
<a id="tocsentityentity"></a>

```json
{
  "id": {
    "value": "value"
  },
  "name": "name"
}

```

An entity is the virtual representation of a (physical, purely virtual or hybrid) device,
is only ever located in the node it was created.
API-visible (non-metadata) attributes of an entity are: id, label, visibility
when visibility=public, any metadata set for this entity (and thus also for its feeds, controls, etc.)
should be visible to the world.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|[commonEntityID](#schemacommonentityid)|false|none|none|
|name|string|false|none|Is assigned to an entity by its creator as a user friendly label.|
|visibility|[commonVisibility](#schemacommonvisibility)|false|none|none|

<h2 id="tocS_entityListAllRequest">entityListAllRequest</h2>

<a id="schemaentitylistallrequest"></a>
<a id="schema_entityListAllRequest"></a>
<a id="tocSentitylistallrequest"></a>
<a id="tocsentitylistallrequest"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "range": {
    "limit": {
      "value": 0
    },
    "offset": {
      "value": 0
    }
  }
}

```

List all entities

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|range|[commonRange](#schemacommonrange)|false|none|Range if specified *may* be obliged by the backend|

<h2 id="tocS_entityListAllResponse">entityListAllResponse</h2>

<a id="schemaentitylistallresponse"></a>
<a id="schema_entityListAllResponse"></a>
<a id="tocSentitylistallresponse"></a>
<a id="tocsentitylistallresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "entities": [
      {
        "id": {
          "value": "value"
        },
        "name": "name"
      },
      {
        "id": {
          "value": "value"
        },
        "name": "name"
      }
    ]
  }
}

```

response of the list all request. Note this is useful for sync responses. In case the entities are too many (millions)
this request may fail. Better opt for async behaviour via stomp/websocket.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[entityListAllResponsePayload](#schemaentitylistallresponsepayload)|false|none|none|

<h2 id="tocS_entityListAllResponsePayload">entityListAllResponsePayload</h2>

<a id="schemaentitylistallresponsepayload"></a>
<a id="schema_entityListAllResponsePayload"></a>
<a id="tocSentitylistallresponsepayload"></a>
<a id="tocsentitylistallresponsepayload"></a>

```json
{
  "entities": [
    {
      "id": {
        "value": "value"
      },
      "name": "name"
    },
    {
      "id": {
        "value": "value"
      },
      "name": "name"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entities|[[entityEntity](#schemaentityentity)]|false|none|[An entity is the virtual representation of a (physical, purely virtual or hybrid) device,<br />is only ever located in the node it was created. <br />API-visible (non-metadata) attributes of an entity are: id, label, visibility<br />when visibility=public, any metadata set for this entity (and thus also for its feeds, controls, etc.) <br />should be visible to the world.]|

<h2 id="tocS_entityListResponse">entityListResponse</h2>

<a id="schemaentitylistresponse"></a>
<a id="schema_entityListResponse"></a>
<a id="tocSentitylistresponse"></a>
<a id="tocsentitylistresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "entity": {
      "id": {
        "value": "value"
      },
      "name": "name"
    }
  }
}

```

message returned by the List service as a stream

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[entityListResponsePayload](#schemaentitylistresponsepayload)|false|none|none|

<h2 id="tocS_entityListResponsePayload">entityListResponsePayload</h2>

<a id="schemaentitylistresponsepayload"></a>
<a id="schema_entityListResponsePayload"></a>
<a id="tocSentitylistresponsepayload"></a>
<a id="tocsentitylistresponsepayload"></a>

```json
{
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entity|[entityEntity](#schemaentityentity)|false|none|An entity is the virtual representation of a (physical, purely virtual or hybrid) device,<br />is only ever located in the node it was created. <br />API-visible (non-metadata) attributes of an entity are: id, label, visibility<br />when visibility=public, any metadata set for this entity (and thus also for its feeds, controls, etc.) <br />should be visible to the world.|

<h2 id="tocS_entityMetaResult">entityMetaResult</h2>

<a id="schemaentitymetaresult"></a>
<a id="schema_entityMetaResult"></a>
<a id="tocSentitymetaresult"></a>
<a id="tocsentitymetaresult"></a>

```json
{
  "comment": "comment",
  "label": "label",
  "location": {
    "lat": 0.8008281904610115,
    "lon": 6.027456183070403
  },
  "properties": [
    {
      "key": "key",
      "values": [
        {
          "bvalue": true,
          "dvalue": 1.4658129805029452,
          "ivalue": "ivalue",
          "svalue": "svalue",
          "type": "type"
        },
        {
          "bvalue": true,
          "dvalue": 1.4658129805029452,
          "ivalue": "ivalue",
          "svalue": "svalue",
          "type": "type"
        }
      ]
    },
    {
      "key": "key",
      "values": [
        {
          "bvalue": true,
          "dvalue": 1.4658129805029452,
          "ivalue": "ivalue",
          "svalue": "svalue",
          "type": "type"
        },
        {
          "bvalue": true,
          "dvalue": 1.4658129805029452,
          "ivalue": "ivalue",
          "svalue": "svalue",
          "type": "type"
        }
      ]
    }
  ],
  "tags": [
    "tags",
    "tags"
  ],
  "values": [
    {
      "label": "label",
      "pointId": {
        "value": "value"
      },
      "storesRecent": true
    },
    {
      "label": "label",
      "pointId": {
        "value": "value"
      },
      "storesRecent": true
    }
  ]
}

```

Metadata result data bag for this point

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|comment|string|false|none|none|
|label|string|false|none|none|
|location|[commonGeoLocation](#schemacommongeolocation)|false|none|Location of e.g. Iotic Things|
|properties|[[commonPropertyList](#schemacommonpropertylist)]|false|none|none|
|tags|[string]|false|none|none|
|values|[[entityPointMeta](#schemaentitypointmeta)]|false|none|[Metadata message for this point]|

<h2 id="tocS_entityMetadataRequest">entityMetadataRequest</h2>

<a id="schemaentitymetadatarequest"></a>
<a id="schema_entityMetadataRequest"></a>
<a id="tocSentitymetadatarequest"></a>
<a id="tocsentitymetadatarequest"></a>

```json
{
  "args": {
    "entityId": {
      "value": "value"
    }
  },
  "format": "string",
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  }
}

```

Requests metadata of this entity

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[entityMetadataRequestArguments](#schemaentitymetadatarequestarguments)|false|none|Only one action argument is necessary.|
|format|string|false|none|format of this metadata request|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|

<h2 id="tocS_entityMetadataRequestArguments">entityMetadataRequestArguments</h2>

<a id="schemaentitymetadatarequestarguments"></a>
<a id="schema_entityMetadataRequestArguments"></a>
<a id="tocSentitymetadatarequestarguments"></a>
<a id="tocsentitymetadatarequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  }
}

```

Only one action argument is necessary.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|

<h2 id="tocS_entityMetadataResponse">entityMetadataResponse</h2>

<a id="schemaentitymetadataresponse"></a>
<a id="schema_entityMetadataResponse"></a>
<a id="tocSentitymetadataresponse"></a>
<a id="tocsentitymetadataresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "entity": {
      "id": {
        "value": "value"
      },
      "name": "name"
    },
    "metadata": "metadata"
  }
}

```

the response for a metadata request on this entity

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[entityMetadataResponsePayload](#schemaentitymetadataresponsepayload)|false|none|none|

<h2 id="tocS_entityMetadataResponsePayload">entityMetadataResponsePayload</h2>

<a id="schemaentitymetadataresponsepayload"></a>
<a id="schema_entityMetadataResponsePayload"></a>
<a id="tocSentitymetadataresponsepayload"></a>
<a id="tocsentitymetadataresponsepayload"></a>

```json
{
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  },
  "metadata": "metadata"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entity|[entityEntity](#schemaentityentity)|false|none|An entity is the virtual representation of a (physical, purely virtual or hybrid) device,<br />is only ever located in the node it was created. <br />API-visible (non-metadata) attributes of an entity are: id, label, visibility<br />when visibility=public, any metadata set for this entity (and thus also for its feeds, controls, etc.) <br />should be visible to the world.|
|metadata|string|false|none|the metadata in teh requested format;|

<h2 id="tocS_entityPointMeta">entityPointMeta</h2>

<a id="schemaentitypointmeta"></a>
<a id="schema_entityPointMeta"></a>
<a id="tocSentitypointmeta"></a>
<a id="tocsentitypointmeta"></a>

```json
{
  "label": "label",
  "pointId": {
    "value": "value"
  },
  "storesRecent": true
}

```

Metadata message for this point

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|label|string|false|none|none|
|pointId|[commonPointID](#schemacommonpointid)|false|none|none|
|pointType|[commonPointType](#schemacommonpointtype)|false|none|A point type|
|storesRecent|boolean(boolean)|false|none|none|

<h2 id="tocS_entityTagsRequest">entityTagsRequest</h2>

<a id="schemaentitytagsrequest"></a>
<a id="schema_entityTagsRequest"></a>
<a id="tocSentitytagsrequest"></a>
<a id="tocsentitytagsrequest"></a>

```json
{
  "args": {
    "entityId": {
      "value": "value"
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "range": {
    "limit": {
      "value": 0
    },
    "offset": {
      "value": 0
    }
  }
}

```

Requests message for tags of this entity

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[entityTagsRequestArguments](#schemaentitytagsrequestarguments)|false|none|none|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|range|[commonRange](#schemacommonrange)|false|none|Range if specified *may* be obliged by the backend|

<h2 id="tocS_entityTagsRequestArguments">entityTagsRequestArguments</h2>

<a id="schemaentitytagsrequestarguments"></a>
<a id="schema_entityTagsRequestArguments"></a>
<a id="tocSentitytagsrequestarguments"></a>
<a id="tocsentitytagsrequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|

<h2 id="tocS_entityTagsResponse">entityTagsResponse</h2>

<a id="schemaentitytagsresponse"></a>
<a id="schema_entityTagsResponse"></a>
<a id="tocSentitytagsresponse"></a>
<a id="tocsentitytagsresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "entity": {
      "id": {
        "value": "value"
      },
      "name": "name"
    },
    "tags": [
      "tags",
      "tags"
    ]
  }
}

```

the response for a tags request on this entity

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[entityTagsResponsePayload](#schemaentitytagsresponsepayload)|false|none|none|

<h2 id="tocS_entityTagsResponsePayload">entityTagsResponsePayload</h2>

<a id="schemaentitytagsresponsepayload"></a>
<a id="schema_entityTagsResponsePayload"></a>
<a id="tocSentitytagsresponsepayload"></a>
<a id="tocsentitytagsresponsepayload"></a>

```json
{
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  },
  "tags": [
    "tags",
    "tags"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entity|[entityEntity](#schemaentityentity)|false|none|An entity is the virtual representation of a (physical, purely virtual or hybrid) device,<br />is only ever located in the node it was created. <br />API-visible (non-metadata) attributes of an entity are: id, label, visibility<br />when visibility=public, any metadata set for this entity (and thus also for its feeds, controls, etc.) <br />should be visible to the world.|
|tags|[string]|false|none|the tags in teh requested format;|

<h2 id="tocS_entityUpdateRequest">entityUpdateRequest</h2>

<a id="schemaentityupdaterequest"></a>
<a id="schema_entityUpdateRequest"></a>
<a id="tocSentityupdaterequest"></a>
<a id="tocsentityupdaterequest"></a>

```json
{
  "args": {
    "entityId": {
      "value": "value"
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "metadata": {
      "format": "string",
      "value": "string"
    },
    "newVisibility": {
      "visibility": "PRIVATE"
    },
    "tags": {
      "added": [
        "string"
      ],
      "deleted": [
        "string"
      ]
    }
  }
}

```

Deprecated note: entityProcessId has been deprecated
Visibility, in V1 is done via Meta-Entity resource.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[entityUpdateRequestArguments](#schemaentityupdaterequestarguments)|false|none|none|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[entityUpdateRequestPayload](#schemaentityupdaterequestpayload)|false|none|One or more fields will be available for update|

<h2 id="tocS_entityUpdateRequestArguments">entityUpdateRequestArguments</h2>

<a id="schemaentityupdaterequestarguments"></a>
<a id="schema_entityUpdateRequestArguments"></a>
<a id="tocSentityupdaterequestarguments"></a>
<a id="tocsentityupdaterequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|

<h2 id="tocS_entityUpdateRequestPayload">entityUpdateRequestPayload</h2>

<a id="schemaentityupdaterequestpayload"></a>
<a id="schema_entityUpdateRequestPayload"></a>
<a id="tocSentityupdaterequestpayload"></a>
<a id="tocsentityupdaterequestpayload"></a>

```json
{
  "metadata": {
    "format": "string",
    "value": "string"
  },
  "newVisibility": {
    "visibility": "PRIVATE"
  },
  "tags": {
    "added": [
      "string"
    ],
    "deleted": [
      "string"
    ]
  }
}

```

One or more fields will be available for update

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|metadata|[commonMetadata](#schemacommonmetadata)|false|none|metadata type - generic databag for setting metadata of resources.|
|newVisibility|[PayloadVisibilityValue](#schemapayloadvisibilityvalue)|false|none|none|
|tags|[commonTags](#schemacommontags)|false|none|list of tags to be added and deleted. if a tag appears in both lists, <br />applications may choose to ignore the tags or throw some error|

<h2 id="tocS_entityUpdated">entityUpdated</h2>

<a id="schemaentityupdated"></a>
<a id="schema_entityUpdated"></a>
<a id="tocSentityupdated"></a>
<a id="tocsentityupdated"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "entity": {
      "id": {
        "value": "value"
      },
      "name": "name"
    }
  }
}

```

Event sent to the requester when the request of update is OK.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[entityUpdatedPayload](#schemaentityupdatedpayload)|false|none|none|

<h2 id="tocS_entityUpdatedPayload">entityUpdatedPayload</h2>

<a id="schemaentityupdatedpayload"></a>
<a id="schema_entityUpdatedPayload"></a>
<a id="tocSentityupdatedpayload"></a>
<a id="tocsentityupdatedpayload"></a>

```json
{
  "entity": {
    "id": {
      "value": "value"
    },
    "name": "name"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entity|[entityEntity](#schemaentityentity)|false|none|An entity is the virtual representation of a (physical, purely virtual or hybrid) device,<br />is only ever located in the node it was created. <br />API-visible (non-metadata) attributes of an entity are: id, label, visibility<br />when visibility=public, any metadata set for this entity (and thus also for its feeds, controls, etc.) <br />should be visible to the world.|

<h2 id="tocS_interestAskRequestArguments">interestAskRequestArguments</h2>

<a id="schemainterestaskrequestarguments"></a>
<a id="schema_interestAskRequestArguments"></a>
<a id="tocSinterestaskrequestarguments"></a>
<a id="tocsinterestaskrequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  },
  "interestId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|
|interestId|[commonInterestID](#schemacommoninterestid)|false|none|none|

<h2 id="tocS_interestAsked">interestAsked</h2>

<a id="schemainterestasked"></a>
<a id="schema_interestAsked"></a>
<a id="tocSinterestasked"></a>
<a id="tocsinterestasked"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  }
}

```

Event sent to requestor of ask request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|

<h2 id="tocS_interestControlPayload">interestControlPayload</h2>

<a id="schemainterestcontrolpayload"></a>
<a id="schema_interestControlPayload"></a>
<a id="tocSinterestcontrolpayload"></a>
<a id="tocsinterestcontrolpayload"></a>

```json
{
  "data": "string",
  "mime": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|string(byte)|false|none|data associated with control request|
|mime|string|false|none|(optional) Mime type of data. ASCII encoded of length 1 <= n <= 64 bytes|

<h2 id="tocS_interestCreateRequestArguments">interestCreateRequestArguments</h2>

<a id="schemainterestcreaterequestarguments"></a>
<a id="schema_interestCreateRequestArguments"></a>
<a id="tocSinterestcreaterequestarguments"></a>
<a id="tocsinterestcreaterequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|

<h2 id="tocS_interestCreateRequestPayload">interestCreateRequestPayload</h2>

<a id="schemainterestcreaterequestpayload"></a>
<a id="schema_interestCreateRequestPayload"></a>
<a id="tocSinterestcreaterequestpayload"></a>
<a id="tocsinterestcreaterequestpayload"></a>

```json
{
  "interest": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    },
    "point": {
      "key": {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        }
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|interest|[interestInterest](#schemainterestinterest)|false|none|An interest is relationship between an entity (node) and a point. For example, creating <br />an interest on (following) a Feed results  in any data shared on said Feed to be forwarded to <br />the associated entity. Interests can be revoked either by the subscriber or provider and there <br />may only be one interest between any unique entity and point combination.|

<h2 id="tocS_interestFetchRequestArguments">interestFetchRequestArguments</h2>

<a id="schemainterestfetchrequestarguments"></a>
<a id="schema_interestFetchRequestArguments"></a>
<a id="tocSinterestfetchrequestarguments"></a>
<a id="tocsinterestfetchrequestarguments"></a>

```json
{
  "interest": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    },
    "point": {
      "key": {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        }
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|interest|[interestInterest](#schemainterestinterest)|false|none|An interest is relationship between an entity (node) and a point. For example, creating <br />an interest on (following) a Feed results  in any data shared on said Feed to be forwarded to <br />the associated entity. Interests can be revoked either by the subscriber or provider and there <br />may only be one interest between any unique entity and point combination.|

<h2 id="tocS_interestFetchResponse">interestFetchResponse</h2>

<a id="schemainterestfetchresponse"></a>
<a id="schema_interestFetchResponse"></a>
<a id="tocSinterestfetchresponse"></a>
<a id="tocsinterestfetchresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "feedData": {
      "data": "string",
      "feedId": "string",
      "mime": "string",
      "time": "2019-08-24T14:15:22Z"
    },
    "interest": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      },
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      }
    },
    "recentDataCounter": 0
  }
}

```

A fetch response message

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[interestFetchResponsePayload](#schemainterestfetchresponsepayload)|false|none|none|

<h2 id="tocS_interestFetchResponsePayload">interestFetchResponsePayload</h2>

<a id="schemainterestfetchresponsepayload"></a>
<a id="schema_interestFetchResponsePayload"></a>
<a id="tocSinterestfetchresponsepayload"></a>
<a id="tocsinterestfetchresponsepayload"></a>

```json
{
  "feedData": {
    "data": "string",
    "feedId": "string",
    "mime": "string",
    "time": "2019-08-24T14:15:22Z"
  },
  "interest": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    },
    "point": {
      "key": {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        }
      }
    }
  },
  "recentDataCounter": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|feedData|[commonFeedDataItem](#schemacommonfeeddataitem)|false|none|none|
|interest|[interestInterest](#schemainterestinterest)|false|none|An interest is relationship between an entity (node) and a point. For example, creating <br />an interest on (following) a Feed results  in any data shared on said Feed to be forwarded to <br />the associated entity. Interests can be revoked either by the subscriber or provider and there <br />may only be one interest between any unique entity and point combination.|
|recentDataCounter|integer(int64)|false|none|optional: current count of recent data sample. it's omitted for non recent data. with value 0, it's the last recent data sample|

<h2 id="tocS_interestInterest">interestInterest</h2>

<a id="schemainterestinterest"></a>
<a id="schema_interestInterest"></a>
<a id="tocSinterestinterest"></a>
<a id="tocsinterestinterest"></a>

```json
{
  "entityId": {
    "value": "value"
  },
  "id": {
    "value": "value"
  },
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  }
}

```

An interest is relationship between an entity (node) and a point. For example, creating
an interest on (following) a Feed results  in any data shared on said Feed to be forwarded to
the associated entity. Interests can be revoked either by the subscriber or provider and there
may only be one interest between any unique entity and point combination.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|
|id|[commonInterestID](#schemacommoninterestid)|false|none|none|
|point|[pointPoint](#schemapointpoint)|false|none|A point (alias for feed or control)|

<h2 id="tocS_interestRecentData">interestRecentData</h2>

<a id="schemainterestrecentdata"></a>
<a id="schema_interestRecentData"></a>
<a id="tocSinterestrecentdata"></a>
<a id="tocsinterestrecentdata"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "point": {
      "key": {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        }
      }
    },
    "samples": [
      {
        "data": "string",
        "feedId": "string",
        "mime": "string",
        "time": "2019-08-24T14:15:22Z"
      }
    ]
  }
}

```

Recent data data bag

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[interestRecentDataPayload](#schemainterestrecentdatapayload)|false|none|none|

<h2 id="tocS_interestRecentDataPayload">interestRecentDataPayload</h2>

<a id="schemainterestrecentdatapayload"></a>
<a id="schema_interestRecentDataPayload"></a>
<a id="tocSinterestrecentdatapayload"></a>
<a id="tocsinterestrecentdatapayload"></a>

```json
{
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  },
  "samples": [
    {
      "data": "string",
      "feedId": "string",
      "mime": "string",
      "time": "2019-08-24T14:15:22Z"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|point|[pointPoint](#schemapointpoint)|false|none|A point (alias for feed or control)|
|samples|[[commonFeedDataItem](#schemacommonfeeddataitem)]|false|none|the list is capped to a max number of recent data which may be smaller than that created by the thing/feed.<br />you can get all recent data by subscribing to teh interest via Fetch|

<h2 id="tocS_interestRecentDataRequestArguments">interestRecentDataRequestArguments</h2>

<a id="schemainterestrecentdatarequestarguments"></a>
<a id="schema_interestRecentDataRequestArguments"></a>
<a id="tocSinterestrecentdatarequestarguments"></a>
<a id="tocsinterestrecentdatarequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  },
  "interestId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|
|interestId|[commonInterestID](#schemacommoninterestid)|false|none|none|

<h2 id="tocS_interestTellRequestArguments">interestTellRequestArguments</h2>

<a id="schemainteresttellrequestarguments"></a>
<a id="schema_interestTellRequestArguments"></a>
<a id="tocSinteresttellrequestarguments"></a>
<a id="tocsinteresttellrequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  },
  "interestId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|
|interestId|[commonInterestID](#schemacommoninterestid)|false|none|none|

<h2 id="tocS_interestTold">interestTold</h2>

<a id="schemainteresttold"></a>
<a id="schema_interestTold"></a>
<a id="tocSinteresttold"></a>
<a id="tocsinteresttold"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  }
}

```

Event sent to requestor of tell request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|

<h2 id="tocS_pingPingResponse">pingPingResponse</h2>

<a id="schemapingpingresponse"></a>
<a id="schema_pingPingResponse"></a>
<a id="tocSpingpingresponse"></a>
<a id="tocspingpingresponse"></a>

```json
{
  "serverTime": "2000-01-23T04:56:07Z",
  "version": {
    "patch": 1,
    "major": 0,
    "minor": 6,
    "build": "build"
  },
  "status": {
    "code": 0,
    "details": [
      {
        "type_url": "type_url",
        "value": "value"
      },
      {
        "type_url": "type_url",
        "value": "value"
      }
    ],
    "message": "message"
  }
}

```

Simple ping response object

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|serverTime|string(date-time)|false|none|server time - loosely useful for latency|
|status|[rpcStatus](#schemarpcstatus)|false|none|The `Status` type defines a logical error model that is suitable for different<br />programming environments, including REST APIs and RPC APIs. It is used by<br />[gRPC](https://github.com/grpc). The error model is designed to be:<br />- Simple to use and understand for most users<br />- Flexible enough to meet unexpected needs<br /><br /># Overview<br /><br />The `Status` message contains three pieces of data: error code, error message,<br />and error details. The error code should be an enum value of<br />[google.rpc.Code][google.rpc.Code], but it may accept additional error codes if needed.  The<br />error message should be a developer-facing English message that helps<br />developers *understand* and *resolve* the error. If a localized user-facing<br />error message is needed, put the localized message in the error details or<br />localize it in the client. The optional error details may contain arbitrary<br />information about the error. There is a predefined set of error detail types<br />in the package `google.rpc` that can be used for common error conditions.<br /><br /># Language mapping<br /><br />The `Status` message is the logical representation of the error model, but it<br />is not necessarily the actual wire format. When the `Status` message is<br />exposed in different client libraries and different wire protocols, it can be<br />mapped differently. For example, it will likely be mapped to some exceptions<br />in Java, but more likely mapped to some error codes in C.<br /><br /># Other uses<br /><br />The error model and the `Status` message can be used in a variety of<br />environments, either with or without APIs, to provide a<br />consistent developer experience across different environments.<br /><br />Example uses of this error model include:<br /><br />- Partial errors. If a service needs to return partial errors to the client,<br />    it may embed the `Status` in the normal response to indicate the partial<br />    errors.<br /><br />- Workflow errors. A typical workflow has multiple steps. Each step may<br />    have a `Status` message for error reporting.<br /><br />- Batch operations. If a client uses batch request and batch response, the<br />    `Status` message should be used directly inside batch response, one for<br />    each error sub-response.<br /><br />- Asynchronous operations. If an API call embeds asynchronous operation<br />    results in its response, the status of those operations should be<br />    represented directly using the `Status` message.<br /><br />- Logging. If some API errors are stored in logs, the message `Status` could<br />    be used directly after any stripping needed for security/privacy reasons.|
|version|[commonVersion](#schemacommonversion)|false|none|Version represents the version of this API|

<h2 id="tocS_pointCompleted">pointCompleted</h2>

<a id="schemapointcompleted"></a>
<a id="schema_pointCompleted"></a>
<a id="tocSpointcompleted"></a>
<a id="tocspointcompleted"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|

<h2 id="tocS_pointCreateControlRequest">pointCreateControlRequest</h2>

<a id="schemapointcreatecontrolrequest"></a>
<a id="schema_pointCreateControlRequest"></a>
<a id="tocSpointcreatecontrolrequest"></a>
<a id="tocspointcreatecontrolrequest"></a>

```json
{
  "args": {
    "entityId": {
      "value": "value"
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "pointId": {
      "value": "value"
    }
  }
}

```

Create control request: a control is a point that send command to a remote device.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[pointCreateControlRequestArguments](#schemapointcreatecontrolrequestarguments)|false|none|none|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[pointCreateControlRequestPayload](#schemapointcreatecontrolrequestpayload)|false|none|none|

<h2 id="tocS_pointCreateControlRequestArguments">pointCreateControlRequestArguments</h2>

<a id="schemapointcreatecontrolrequestarguments"></a>
<a id="schema_pointCreateControlRequestArguments"></a>
<a id="tocSpointcreatecontrolrequestarguments"></a>
<a id="tocspointcreatecontrolrequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|

<h2 id="tocS_pointCreateControlRequestPayload">pointCreateControlRequestPayload</h2>

<a id="schemapointcreatecontrolrequestpayload"></a>
<a id="schema_pointCreateControlRequestPayload"></a>
<a id="tocSpointcreatecontrolrequestpayload"></a>
<a id="tocspointcreatecontrolrequestpayload"></a>

```json
{
  "pointId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|pointId|[commonPointID](#schemacommonpointid)|false|none|none|

<h2 id="tocS_pointCreateFeedRequest">pointCreateFeedRequest</h2>

<a id="schemapointcreatefeedrequest"></a>
<a id="schema_pointCreateFeedRequest"></a>
<a id="tocSpointcreatefeedrequest"></a>
<a id="tocspointcreatefeedrequest"></a>

```json
{
  "args": {
    "entityId": {
      "value": "value"
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "maxSamples": 0,
    "pointId": {
      "value": "value"
    }
  }
}

```

Create feed request: a feed is a point that shares data.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[pointCreateFeedRequestArguments](#schemapointcreatefeedrequestarguments)|false|none|none|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[pointCreateFeedRequestPayload](#schemapointcreatefeedrequestpayload)|false|none|none|

<h2 id="tocS_pointCreateFeedRequestArguments">pointCreateFeedRequestArguments</h2>

<a id="schemapointcreatefeedrequestarguments"></a>
<a id="schema_pointCreateFeedRequestArguments"></a>
<a id="tocSpointcreatefeedrequestarguments"></a>
<a id="tocspointcreatefeedrequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|

<h2 id="tocS_pointCreateFeedRequestPayload">pointCreateFeedRequestPayload</h2>

<a id="schemapointcreatefeedrequestpayload"></a>
<a id="schema_pointCreateFeedRequestPayload"></a>
<a id="tocSpointcreatefeedrequestpayload"></a>
<a id="tocspointcreatefeedrequestpayload"></a>

```json
{
  "maxSamples": 0,
  "pointId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|maxSamples|integer(int32)|false|none|TODO: this is ugly - do it differetnly with a proper SamplesConfig message<br />number of shares to save in recent data store (if available).<br />- No value or a value of zero disables storage.<br />- A negative value can be used to request the maximum sample count.<br />- Too large a value will results in the maximum count being used also.<br />- This option currently only applies to Feeds and will be ignored for Controls.<br />- For existing points this parameter has no effect.<br />- If the container does not support recent storage, this parameter is ignored.|
|pointId|[commonPointID](#schemacommonpointid)|false|none|none|

<h2 id="tocS_pointCreated">pointCreated</h2>

<a id="schemapointcreated"></a>
<a id="schema_pointCreated"></a>
<a id="tocSpointcreated"></a>
<a id="tocspointcreated"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "alreadyCreated": true,
    "point": {
      "key": {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        }
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[pointCreatedPayload](#schemapointcreatedpayload)|false|none|none|

<h2 id="tocS_pointCreatedPayload">pointCreatedPayload</h2>

<a id="schemapointcreatedpayload"></a>
<a id="schema_pointCreatedPayload"></a>
<a id="tocSpointcreatedpayload"></a>
<a id="tocspointcreatedpayload"></a>

```json
{
  "alreadyCreated": true,
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|alreadyCreated|boolean(boolean)|false|none|none|
|point|[pointPoint](#schemapointpoint)|false|none|A point (alias for feed or control)|

<h2 id="tocS_pointDeleteRequest">pointDeleteRequest</h2>

<a id="schemapointdeleterequest"></a>
<a id="schema_pointDeleteRequest"></a>
<a id="tocSpointdeleterequest"></a>
<a id="tocspointdeleterequest"></a>

```json
{
  "args": {
    "pointKey": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[pointDeleteRequestArguments](#schemapointdeleterequestarguments)|false|none|none|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|

<h2 id="tocS_pointDeleteRequestArguments">pointDeleteRequestArguments</h2>

<a id="schemapointdeleterequestarguments"></a>
<a id="schema_pointDeleteRequestArguments"></a>
<a id="tocSpointdeleterequestarguments"></a>
<a id="tocspointdeleterequestarguments"></a>

```json
{
  "pointKey": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|pointKey|[PointKey](#schemapointkey)|false|none|none|

<h2 id="tocS_pointDeleted">pointDeleted</h2>

<a id="schemapointdeleted"></a>
<a id="schema_pointDeleted"></a>
<a id="tocSpointdeleted"></a>
<a id="tocspointdeleted"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "point": {
      "key": {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        }
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[pointDeletedPayload](#schemapointdeletedpayload)|false|none|none|

<h2 id="tocS_pointDeletedPayload">pointDeletedPayload</h2>

<a id="schemapointdeletedpayload"></a>
<a id="schema_pointDeletedPayload"></a>
<a id="tocSpointdeletedpayload"></a>
<a id="tocspointdeletedpayload"></a>

```json
{
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|point|[pointPoint](#schemapointpoint)|false|none|A point (alias for feed or control)|

<h2 id="tocS_pointDescriptionRequest">pointDescriptionRequest</h2>

<a id="schemapointdescriptionrequest"></a>
<a id="schema_pointDescriptionRequest"></a>
<a id="tocSpointdescriptionrequest"></a>
<a id="tocspointdescriptionrequest"></a>

```json
{
  "args": {
    "pointKey": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "lang": "string",
  "scope": "GLOBAL"
}

```

Description of entities: Provides public metadata lookup for individual resources

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[pointDescriptionRequestArguments](#schemapointdescriptionrequestarguments)|false|none|Only one action argument is necessary.|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|lang|string|false|none|Language code for labels and comments (but not values and tags, apart from for value comments).|
|scope|[commonScope](#schemacommonscope)|false|none|- LOCAL: container-local describe<br /> - LOCAL_OWN: container-local search of own entities only. Scoped to the user associated to this request<br /> - AUTO: equivalent to local and if not found, global|

<h2 id="tocS_pointDescriptionRequestArguments">pointDescriptionRequestArguments</h2>

<a id="schemapointdescriptionrequestarguments"></a>
<a id="schema_pointDescriptionRequestArguments"></a>
<a id="tocSpointdescriptionrequestarguments"></a>
<a id="tocspointdescriptionrequestarguments"></a>

```json
{
  "pointKey": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    }
  }
}

```

Only one action argument is necessary.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|pointKey|[PointKey](#schemapointkey)|false|none|none|

<h2 id="tocS_pointDescriptionResponse">pointDescriptionResponse</h2>

<a id="schemapointdescriptionresponse"></a>
<a id="schema_pointDescriptionResponse"></a>
<a id="tocSpointdescriptionresponse"></a>
<a id="tocspointdescriptionresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "point": {
      "key": {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        }
      }
    },
    "result": {
      "comment": "comment",
      "label": "label",
      "storesRecent": true,
      "tags": [
        "tags",
        "tags"
      ],
      "values": [
        {
          "comment": "comment",
          "dataType": "dataType",
          "label": "label",
          "unit": "unit"
        },
        {
          "comment": "comment",
          "dataType": "dataType",
          "label": "label",
          "unit": "unit"
        }
      ]
    }
  }
}

```

the response to a describe request fo this point

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[pointDescriptionResponsePayload](#schemapointdescriptionresponsepayload)|false|none|none|

<h2 id="tocS_pointDescriptionResponsePayload">pointDescriptionResponsePayload</h2>

<a id="schemapointdescriptionresponsepayload"></a>
<a id="schema_pointDescriptionResponsePayload"></a>
<a id="tocSpointdescriptionresponsepayload"></a>
<a id="tocspointdescriptionresponsepayload"></a>

```json
{
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  },
  "result": {
    "comment": "comment",
    "label": "label",
    "storesRecent": true,
    "tags": [
      "tags",
      "tags"
    ],
    "values": [
      {
        "comment": "comment",
        "dataType": "dataType",
        "label": "label",
        "unit": "unit"
      },
      {
        "comment": "comment",
        "dataType": "dataType",
        "label": "label",
        "unit": "unit"
      }
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|point|[pointPoint](#schemapointpoint)|false|none|A point (alias for feed or control)|
|result|[pointMetaResult](#schemapointmetaresult)|false|none|Metadata result databag|

<h2 id="tocS_pointListAllRequest">pointListAllRequest</h2>

<a id="schemapointlistallrequest"></a>
<a id="schema_pointListAllRequest"></a>
<a id="tocSpointlistallrequest"></a>
<a id="tocspointlistallrequest"></a>

```json
{
  "args": {
    "entityId": {
      "value": "value"
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "pointTypeValue": {
    "pointType": "FEED"
  }
}

```

List all points request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[pointListAllRequestArguments](#schemapointlistallrequestarguments)|false|none|none|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|pointTypeValue|[ListAllRequestPointTypeValue](#schemalistallrequestpointtypevalue)|false|none|none|

<h2 id="tocS_pointListAllRequestArguments">pointListAllRequestArguments</h2>

<a id="schemapointlistallrequestarguments"></a>
<a id="schema_pointListAllRequestArguments"></a>
<a id="tocSpointlistallrequestarguments"></a>
<a id="tocspointlistallrequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|

<h2 id="tocS_pointListAllResponse">pointListAllResponse</h2>

<a id="schemapointlistallresponse"></a>
<a id="schema_pointListAllResponse"></a>
<a id="tocSpointlistallresponse"></a>
<a id="tocspointlistallresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "infoList": [
      {
        "interestCount": 0,
        "point": {
          "key": {
            "entityId": {
              "value": "value"
            },
            "id": {
              "value": "value"
            }
          }
        }
      },
      {
        "interestCount": 0,
        "point": {
          "key": {
            "entityId": {
              "value": "value"
            },
            "id": {
              "value": "value"
            }
          }
        }
      }
    ]
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[pointListAllResponsePayload](#schemapointlistallresponsepayload)|false|none|none|

<h2 id="tocS_pointListAllResponsePayload">pointListAllResponsePayload</h2>

<a id="schemapointlistallresponsepayload"></a>
<a id="schema_pointListAllResponsePayload"></a>
<a id="tocSpointlistallresponsepayload"></a>
<a id="tocspointlistallresponsepayload"></a>

```json
{
  "infoList": [
    {
      "interestCount": 0,
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      }
    },
    {
      "interestCount": 0,
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      }
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|infoList|[[pointPointInfo](#schemapointpointinfo)]|false|none|optional: only for list request|

<h2 id="tocS_pointMetaResult">pointMetaResult</h2>

<a id="schemapointmetaresult"></a>
<a id="schema_pointMetaResult"></a>
<a id="tocSpointmetaresult"></a>
<a id="tocspointmetaresult"></a>

```json
{
  "comment": "comment",
  "label": "label",
  "storesRecent": true,
  "tags": [
    "tags",
    "tags"
  ],
  "values": [
    {
      "comment": "comment",
      "dataType": "dataType",
      "label": "label",
      "unit": "unit"
    },
    {
      "comment": "comment",
      "dataType": "dataType",
      "label": "label",
      "unit": "unit"
    }
  ]
}

```

Metadata result databag

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|comment|string|false|none|none|
|label|string|false|none|none|
|pointType|[commonPointType](#schemacommonpointtype)|false|none|A point type|
|storesRecent|boolean(boolean)|false|none|none|
|tags|[string]|false|none|none|
|values|[[pointPointMeta](#schemapointpointmeta)]|false|none|[Point metadata]|

<h2 id="tocS_pointMetadataRequest">pointMetadataRequest</h2>

<a id="schemapointmetadatarequest"></a>
<a id="schema_pointMetadataRequest"></a>
<a id="tocSpointmetadatarequest"></a>
<a id="tocspointmetadatarequest"></a>

```json
{
  "args": {
    "pointKey": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  },
  "format": "string",
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  }
}

```

metadata request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[pointMetadataRequestArguments](#schemapointmetadatarequestarguments)|false|none|none|
|format|string|false|none|this request's format;|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|

<h2 id="tocS_pointMetadataRequestArguments">pointMetadataRequestArguments</h2>

<a id="schemapointmetadatarequestarguments"></a>
<a id="schema_pointMetadataRequestArguments"></a>
<a id="tocSpointmetadatarequestarguments"></a>
<a id="tocspointmetadatarequestarguments"></a>

```json
{
  "pointKey": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|pointKey|[PointKey](#schemapointkey)|false|none|none|

<h2 id="tocS_pointMetadataResponse">pointMetadataResponse</h2>

<a id="schemapointmetadataresponse"></a>
<a id="schema_pointMetadataResponse"></a>
<a id="tocSpointmetadataresponse"></a>
<a id="tocspointmetadataresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "metadata": "metadata",
    "point": {
      "key": {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        }
      }
    }
  }
}

```

the response to a metadata request for this point

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[pointMetadataResponsePayload](#schemapointmetadataresponsepayload)|false|none|none|

<h2 id="tocS_pointMetadataResponsePayload">pointMetadataResponsePayload</h2>

<a id="schemapointmetadataresponsepayload"></a>
<a id="schema_pointMetadataResponsePayload"></a>
<a id="tocSpointmetadataresponsepayload"></a>
<a id="tocspointmetadataresponsepayload"></a>

```json
{
  "metadata": "metadata",
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|metadata|string|false|none|the metadata in the req specified format|
|point|[pointPoint](#schemapointpoint)|false|none|A point (alias for feed or control)|

<h2 id="tocS_pointPoint">pointPoint</h2>

<a id="schemapointpoint"></a>
<a id="schema_pointPoint"></a>
<a id="tocSpointpoint"></a>
<a id="tocspointpoint"></a>

```json
{
  "key": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    }
  }
}

```

A point (alias for feed or control)

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|key|[PointKey](#schemapointkey)|false|none|none|
|type|[commonPointType](#schemacommonpointtype)|false|none|A point type|

<h2 id="tocS_pointPointInfo">pointPointInfo</h2>

<a id="schemapointpointinfo"></a>
<a id="schema_pointPointInfo"></a>
<a id="tocSpointpointinfo"></a>
<a id="tocspointpointinfo"></a>

```json
{
  "interestCount": 0,
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|interestCount|integer(int64)|false|none|number of active interest|
|point|[pointPoint](#schemapointpoint)|false|none|A point (alias for feed or control)|

<h2 id="tocS_pointPointMeta">pointPointMeta</h2>

<a id="schemapointpointmeta"></a>
<a id="schema_pointPointMeta"></a>
<a id="tocSpointpointmeta"></a>
<a id="tocspointpointmeta"></a>

```json
{
  "comment": "comment",
  "dataType": "dataType",
  "label": "label",
  "unit": "unit"
}

```

Point metadata

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|comment|string|false|none|none|
|dataType|string|false|none|none|
|label|string|false|none|none|
|unit|string|false|none|none|

<h2 id="tocS_pointTagsRequest">pointTagsRequest</h2>

<a id="schemapointtagsrequest"></a>
<a id="schema_pointTagsRequest"></a>
<a id="tocSpointtagsrequest"></a>
<a id="tocspointtagsrequest"></a>

```json
{
  "args": {
    "pointKey": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "range": {
    "limit": {
      "value": 0
    },
    "offset": {
      "value": 0
    }
  }
}

```

tags request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[pointTagsRequestArguments](#schemapointtagsrequestarguments)|false|none|none|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|range|[commonRange](#schemacommonrange)|false|none|Range if specified *may* be obliged by the backend|

<h2 id="tocS_pointTagsRequestArguments">pointTagsRequestArguments</h2>

<a id="schemapointtagsrequestarguments"></a>
<a id="schema_pointTagsRequestArguments"></a>
<a id="tocSpointtagsrequestarguments"></a>
<a id="tocspointtagsrequestarguments"></a>

```json
{
  "pointKey": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|pointKey|[PointKey](#schemapointkey)|false|none|none|

<h2 id="tocS_pointTagsResponse">pointTagsResponse</h2>

<a id="schemapointtagsresponse"></a>
<a id="schema_pointTagsResponse"></a>
<a id="tocSpointtagsresponse"></a>
<a id="tocspointtagsresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "point": {
      "key": {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        }
      }
    },
    "tags": [
      "tags",
      "tags"
    ]
  }
}

```

the response to a tags request for this point

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[pointTagsResponsePayload](#schemapointtagsresponsepayload)|false|none|none|

<h2 id="tocS_pointTagsResponsePayload">pointTagsResponsePayload</h2>

<a id="schemapointtagsresponsepayload"></a>
<a id="schema_pointTagsResponsePayload"></a>
<a id="tocSpointtagsresponsepayload"></a>
<a id="tocspointtagsresponsepayload"></a>

```json
{
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  },
  "tags": [
    "tags",
    "tags"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|point|[pointPoint](#schemapointpoint)|false|none|A point (alias for feed or control)|
|tags|[string]|false|none|the tags for this point|

<h2 id="tocS_pointUpdateConfigRequest">pointUpdateConfigRequest</h2>

<a id="schemapointupdateconfigrequest"></a>
<a id="schema_pointUpdateConfigRequest"></a>
<a id="tocSpointupdateconfigrequest"></a>
<a id="tocspointupdateconfigrequest"></a>

```json
{
  "args": {
    "pointKey": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "maxSamples": 0,
    "metadata": {
      "format": "string",
      "value": "string"
    },
    "tags": {
      "added": [
        "string"
      ],
      "deleted": [
        "string"
      ]
    }
  }
}

```

A request to update config of an existing feed or control

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[pointUpdateConfigRequestArguments](#schemapointupdateconfigrequestarguments)|false|none|none|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[pointUpdateConfigRequestPayload](#schemapointupdateconfigrequestpayload)|false|none|One or more fields will be available for update|

<h2 id="tocS_pointUpdateConfigRequestArguments">pointUpdateConfigRequestArguments</h2>

<a id="schemapointupdateconfigrequestarguments"></a>
<a id="schema_pointUpdateConfigRequestArguments"></a>
<a id="tocSpointupdateconfigrequestarguments"></a>
<a id="tocspointupdateconfigrequestarguments"></a>

```json
{
  "pointKey": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|pointKey|[PointKey](#schemapointkey)|false|none|none|

<h2 id="tocS_pointUpdateConfigRequestPayload">pointUpdateConfigRequestPayload</h2>

<a id="schemapointupdateconfigrequestpayload"></a>
<a id="schema_pointUpdateConfigRequestPayload"></a>
<a id="tocSpointupdateconfigrequestpayload"></a>
<a id="tocspointupdateconfigrequestpayload"></a>

```json
{
  "maxSamples": 0,
  "metadata": {
    "format": "string",
    "value": "string"
  },
  "tags": {
    "added": [
      "string"
    ],
    "deleted": [
      "string"
    ]
  }
}

```

One or more fields will be available for update

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|maxSamples|integer(int32)|false|none|max samples|
|metadata|[commonMetadata](#schemacommonmetadata)|false|none|metadata type - generic databag for setting metadata of resources.|
|tags|[commonTags](#schemacommontags)|false|none|list of tags to be added and deleted. if a tag appears in both lists, <br />applications may choose to ignore the tags or throw some error|

<h2 id="tocS_pointUpdateControlRequestArguments">pointUpdateControlRequestArguments</h2>

<a id="schemapointupdatecontrolrequestarguments"></a>
<a id="schema_pointUpdateControlRequestArguments"></a>
<a id="tocSpointupdatecontrolrequestarguments"></a>
<a id="tocspointupdatecontrolrequestarguments"></a>

```json
{
  "pointKey": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|pointKey|[PointKey](#schemapointkey)|false|none|none|

<h2 id="tocS_pointUpdateControlRequestPayload">pointUpdateControlRequestPayload</h2>

<a id="schemapointupdatecontrolrequestpayload"></a>
<a id="schema_pointUpdateControlRequestPayload"></a>
<a id="tocSpointupdatecontrolrequestpayload"></a>
<a id="tocspointupdatecontrolrequestpayload"></a>

```json
{
  "success": true
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|success|boolean(boolean)|false|none|feed data to share|

<h2 id="tocS_pointUpdateFeedRequestArguments">pointUpdateFeedRequestArguments</h2>

<a id="schemapointupdatefeedrequestarguments"></a>
<a id="schema_pointUpdateFeedRequestArguments"></a>
<a id="tocSpointupdatefeedrequestarguments"></a>
<a id="tocspointupdatefeedrequestarguments"></a>

```json
{
  "pointKey": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|pointKey|[PointKey](#schemapointkey)|false|none|none|

<h2 id="tocS_pointUpdateFeedRequestPayload">pointUpdateFeedRequestPayload</h2>

<a id="schemapointupdatefeedrequestpayload"></a>
<a id="schema_pointUpdateFeedRequestPayload"></a>
<a id="tocSpointupdatefeedrequestpayload"></a>
<a id="tocspointupdatefeedrequestpayload"></a>

```json
{
  "data": "string",
  "mime": "string",
  "time": "2019-08-24T14:15:22Z"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|data|string(byte)|false|none|feed data to share|
|mime|string|false|none|Mime type of data. ASCII encoded of length 1 <= n <= 64 bytes|
|time|string(date-time)|false|none|If not provided the current time, as seen by the container, will be used.|

<h2 id="tocS_pointUpdated">pointUpdated</h2>

<a id="schemapointupdated"></a>
<a id="schema_pointUpdated"></a>
<a id="tocSpointupdated"></a>
<a id="tocspointupdated"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "point": {
      "key": {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        }
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[pointUpdatedPayload](#schemapointupdatedpayload)|false|none|none|

<h2 id="tocS_pointUpdatedPayload">pointUpdatedPayload</h2>

<a id="schemapointupdatedpayload"></a>
<a id="schema_pointUpdatedPayload"></a>
<a id="tocSpointupdatedpayload"></a>
<a id="tocspointupdatedpayload"></a>

```json
{
  "point": {
    "key": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|point|[pointPoint](#schemapointpoint)|false|none|A point (alias for feed or control)|

<h2 id="tocS_protobufAny">protobufAny</h2>

<a id="schemaprotobufany"></a>
<a id="schema_protobufAny"></a>
<a id="tocSprotobufany"></a>
<a id="tocsprotobufany"></a>

```json
{
  "type_url": "string",
  "value": {}
}

```

`Any` contains an arbitrary serialized protocol buffer message along with a
URL that describes the type of the serialized message.

Protobuf library provides support to pack/unpack Any values in the form
of utility functions or additional generated methods of the Any type.

Example 1: Pack and unpack a message in C++.

    Foo foo = ...;
    Any any;
    any.PackFrom(foo);
    ...
    if (any.UnpackTo(&foo)) {
      ...
    }

Example 2: Pack and unpack a message in Java.

    Foo foo = ...;
    Any any = Any.pack(foo);
    ...
    if (any.is(Foo.class)) {
      foo = any.unpack(Foo.class);
    }

 Example 3: Pack and unpack a message in Python.

    foo = Foo(...)
    any = Any()
    any.Pack(foo)
    ...
    if any.Is(Foo.DESCRIPTOR):
      any.Unpack(foo)
      ...

 Example 4: Pack and unpack a message in Go

     foo := &pb.Foo{...}
     any, err := ptypes.MarshalAny(foo)
     ...
     foo := &pb.Foo{}
     if err := ptypes.UnmarshalAny(any, foo); err != nil {
       ...
     }

The pack methods provided by protobuf library will by default use
'type.googleapis.com/full.type.name' as the type URL and the unpack
methods only use the fully qualified type name after the last '/'
in the type URL, for example "foo.bar.com/x/y.z" will yield type
name "y.z".

JSON
====
The JSON representation of an `Any` value uses the regular
representation of the deserialized, embedded message, with an
additional field `@type` which contains the type URL. Example:

    package google.profile;
    message Person {
      string first_name = 1;
      string last_name = 2;
    }

    {
      "@type": "type.googleapis.com/google.profile.Person",
      "firstName": <string>,
      "lastName": <string>
    }

If the embedded message type is well-known and has a custom JSON
representation, that representation will be embedded adding a field
`value` which holds the custom JSON in addition to the `@type`
field. Example (for message [google.protobuf.Duration][]):

    {
      "@type": "type.googleapis.com/google.protobuf.Duration",
      "value": "1.212s"
    }

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type_url|string|false|none|A URL/resource name that uniquely identifies the type of the serialized<br />protocol buffer message. This string must contain at least<br />one "/" character. The last segment of the URL's path must represent<br />the fully qualified name of the type (as in<br />`path/google.protobuf.Duration`). The name should be in a canonical form<br />(e.g., leading "." is not accepted).<br /><br />In practice, teams usually precompile into the binary all types that they<br />expect it to use in the context of Any. However, for URLs which use the<br />scheme `http`, `https`, or no scheme, one can optionally set up a type<br />server that maps type URLs to message definitions as follows:<br /><br />* If no scheme is provided, `https` is assumed.<br />* An HTTP GET on the URL must yield a [google.protobuf.Type][]<br />  value in binary format, or produce an error.<br />* Applications are allowed to cache lookup results based on the<br />  URL, or have them precompiled into a binary to avoid any<br />  lookup. Therefore, binary compatibility needs to be preserved<br />  on changes to types. (Use versioned type names to manage<br />  breaking changes.)<br /><br />Note: this functionality is not currently available in the official<br />protobuf release, and it is not used for type URLs beginning with<br />type.googleapis.com.<br /><br />Schemes other than `http`, `https` (or the empty scheme) might be<br />used with implementation specific semantics.|
|value|object|false|none|none|

<h2 id="tocS_qapiinterestCreated">qapiinterestCreated</h2>

<a id="schemaqapiinterestcreated"></a>
<a id="schema_qapiinterestCreated"></a>
<a id="tocSqapiinterestcreated"></a>
<a id="tocsqapiinterestcreated"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "alreadyCreated": true,
    "interest": {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      },
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      }
    }
  }
}

```

An event sent to requestor when created request succeeded

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[qapiinterestCreatedPayload](#schemaqapiinterestcreatedpayload)|false|none|none|

<h2 id="tocS_qapiinterestCreatedPayload">qapiinterestCreatedPayload</h2>

<a id="schemaqapiinterestcreatedpayload"></a>
<a id="schema_qapiinterestCreatedPayload"></a>
<a id="tocSqapiinterestcreatedpayload"></a>
<a id="tocsqapiinterestcreatedpayload"></a>

```json
{
  "alreadyCreated": true,
  "interest": {
    "entityId": {
      "value": "value"
    },
    "id": {
      "value": "value"
    },
    "point": {
      "key": {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        }
      }
    }
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|alreadyCreated|boolean(boolean)|false|none|whether the interest exists already (creating an existing interest is idempotent). Optional, with defaule=false|
|interest|[interestInterest](#schemainterestinterest)|false|none|An interest is relationship between an entity (node) and a point. For example, creating <br />an interest on (following) a Feed results  in any data shared on said Feed to be forwarded to <br />the associated entity. Interests can be revoked either by the subscriber or provider and there <br />may only be one interest between any unique entity and point combination.|

<h2 id="tocS_qapiinterestDeleteRequestArguments">qapiinterestDeleteRequestArguments</h2>

<a id="schemaqapiinterestdeleterequestarguments"></a>
<a id="schema_qapiinterestDeleteRequestArguments"></a>
<a id="tocSqapiinterestdeleterequestarguments"></a>
<a id="tocsqapiinterestdeleterequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  },
  "interestId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|
|interestId|[commonInterestID](#schemacommoninterestid)|false|none|none|

<h2 id="tocS_qapiinterestDeleted">qapiinterestDeleted</h2>

<a id="schemaqapiinterestdeleted"></a>
<a id="schema_qapiinterestDeleted"></a>
<a id="tocSqapiinterestdeleted"></a>
<a id="tocsqapiinterestdeleted"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "interestId": [
      {
        "value": "value"
      }
    ]
  }
}

```

Event sent to requestor of delete resource

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[qapiinterestDeletedPayload](#schemaqapiinterestdeletedpayload)|false|none|none|

<h2 id="tocS_qapiinterestDeletedPayload">qapiinterestDeletedPayload</h2>

<a id="schemaqapiinterestdeletedpayload"></a>
<a id="schema_qapiinterestDeletedPayload"></a>
<a id="tocSqapiinterestdeletedpayload"></a>
<a id="tocsqapiinterestdeletedpayload"></a>

```json
{
  "interestId": [
    {
      "value": "value"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|interestId|[[commonInterestID](#schemacommoninterestid)]|false|none|list of globally unique ids of interests|

<h2 id="tocS_qapiinterestListAllRequest">qapiinterestListAllRequest</h2>

<a id="schemaqapiinterestlistallrequest"></a>
<a id="schema_qapiinterestListAllRequest"></a>
<a id="tocSqapiinterestlistallrequest"></a>
<a id="tocsqapiinterestlistallrequest"></a>

```json
{
  "args": {
    "entityId": {
      "value": "value"
    }
  },
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "range": {
    "limit": {
      "value": 0
    },
    "offset": {
      "value": 0
    }
  }
}

```

A request to list all interests for this entity local id.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|args|[qapiinterestListAllRequestArguments](#schemaqapiinterestlistallrequestarguments)|false|none|none|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|range|[commonRange](#schemacommonrange)|false|none|Range if specified *may* be obliged by the backend|

<h2 id="tocS_qapiinterestListAllRequestArguments">qapiinterestListAllRequestArguments</h2>

<a id="schemaqapiinterestlistallrequestarguments"></a>
<a id="schema_qapiinterestListAllRequestArguments"></a>
<a id="tocSqapiinterestlistallrequestarguments"></a>
<a id="tocsqapiinterestlistallrequestarguments"></a>

```json
{
  "entityId": {
    "value": "value"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entityId|[commonEntityID](#schemacommonentityid)|false|none|none|

<h2 id="tocS_qapiinterestListAllResponse">qapiinterestListAllResponse</h2>

<a id="schemaqapiinterestlistallresponse"></a>
<a id="schema_qapiinterestListAllResponse"></a>
<a id="tocSqapiinterestlistallresponse"></a>
<a id="tocsqapiinterestlistallresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "interests": [
      {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        },
        "point": {
          "key": {
            "entityId": {
              "value": "value"
            },
            "id": {
              "value": "value"
            }
          }
        }
      },
      {
        "entityId": {
          "value": "value"
        },
        "id": {
          "value": "value"
        },
        "point": {
          "key": {
            "entityId": {
              "value": "value"
            },
            "id": {
              "value": "value"
            }
          }
        }
      }
    ]
  }
}

```

List all response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[qapiinterestListAllResponsePayload](#schemaqapiinterestlistallresponsepayload)|false|none|none|

<h2 id="tocS_qapiinterestListAllResponsePayload">qapiinterestListAllResponsePayload</h2>

<a id="schemaqapiinterestlistallresponsepayload"></a>
<a id="schema_qapiinterestListAllResponsePayload"></a>
<a id="tocSqapiinterestlistallresponsepayload"></a>
<a id="tocsqapiinterestlistallresponsepayload"></a>

```json
{
  "interests": [
    {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      },
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      }
    },
    {
      "entityId": {
        "value": "value"
      },
      "id": {
        "value": "value"
      },
      "point": {
        "key": {
          "entityId": {
            "value": "value"
          },
          "id": {
            "value": "value"
          }
        }
      }
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|interests|[[interestInterest](#schemainterestinterest)]|false|none|[An interest is relationship between an entity (node) and a point. For example, creating <br />an interest on (following) a Feed results  in any data shared on said Feed to be forwarded to <br />the associated entity. Interests can be revoked either by the subscriber or provider and there <br />may only be one interest between any unique entity and point combination.]|

<h2 id="tocS_qapisearchResponse">qapisearchResponse</h2>

<a id="schemaqapisearchresponse"></a>
<a id="schema_qapisearchResponse"></a>
<a id="tocSqapisearchresponse"></a>
<a id="tocsqapisearchresponse"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "payload": {
    "entities": [
      {
        "id": {
          "value": "value"
        },
        "label": "label",
        "location": {
          "lat": 6.027456183070403,
          "lon": 1.4658129805029452
        },
        "points": [
          {
            "label": "label",
            "point": {
              "key": {
                "entityId": {
                  "value": "value"
                },
                "id": {
                  "value": "value"
                }
              }
            },
            "storesRecent": true
          },
          {
            "label": "label",
            "point": {
              "key": {
                "entityId": {
                  "value": "value"
                },
                "id": {
                  "value": "value"
                }
              }
            },
            "storesRecent": true
          }
        ]
      },
      {
        "id": {
          "value": "value"
        },
        "label": "label",
        "location": {
          "lat": 6.027456183070403,
          "lon": 1.4658129805029452
        },
        "points": [
          {
            "label": "label",
            "point": {
              "key": {
                "entityId": {
                  "value": "value"
                },
                "id": {
                  "value": "value"
                }
              }
            },
            "storesRecent": true
          },
          {
            "label": "label",
            "point": {
              "key": {
                "entityId": {
                  "value": "value"
                },
                "id": {
                  "value": "value"
                }
              }
            },
            "storesRecent": true
          }
        ]
      }
    ],
    "status": {
      "code": 0,
      "details": [
        {
          "type_url": "type_url",
          "value": "value"
        },
        {
          "type_url": "type_url",
          "value": "value"
        }
      ],
      "message": "message"
    }
  }
}

```

the search response. In the registrar based iotic platform a Respose contains ALL matching entities in the local
subspace and all public in the registrar.
In the decentralised iotics operating env, each node in the network generates a response and the client is expected to
receive a stream of response messages.
`matches` and `owner` attributes have been removed from the original qapi spec in infra/v1 as they're not used.
depending on the desired ResponseType in the request, not all attributes in the entity details are specified (see comments).
Another difference between results from centralised v decentralised backends is the interpretation of range. The single
response provided by the centralised backend has the entities ordered and produced according to the (optional) range
in the request. In a decentralised network, range has limited use and the offset attribute is ignored.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|payload|[searchResponsePayload](#schemasearchresponsepayload)|false|none|none|

<h2 id="tocS_rpcStatus">rpcStatus</h2>

<a id="schemarpcstatus"></a>
<a id="schema_rpcStatus"></a>
<a id="tocSrpcstatus"></a>
<a id="tocsrpcstatus"></a>

```json
{
  "code": 0,
  "details": [
    {
      "type_url": "type_url",
      "value": "value"
    },
    {
      "type_url": "type_url",
      "value": "value"
    }
  ],
  "message": "message"
}

```

The `Status` type defines a logical error model that is suitable for different
programming environments, including REST APIs and RPC APIs. It is used by
[gRPC](https://github.com/grpc). The error model is designed to be:
- Simple to use and understand for most users
- Flexible enough to meet unexpected needs

# Overview

The `Status` message contains three pieces of data: error code, error message,
and error details. The error code should be an enum value of
[google.rpc.Code][google.rpc.Code], but it may accept additional error codes if needed.  The
error message should be a developer-facing English message that helps
developers *understand* and *resolve* the error. If a localized user-facing
error message is needed, put the localized message in the error details or
localize it in the client. The optional error details may contain arbitrary
information about the error. There is a predefined set of error detail types
in the package `google.rpc` that can be used for common error conditions.

# Language mapping

The `Status` message is the logical representation of the error model, but it
is not necessarily the actual wire format. When the `Status` message is
exposed in different client libraries and different wire protocols, it can be
mapped differently. For example, it will likely be mapped to some exceptions
in Java, but more likely mapped to some error codes in C.

# Other uses

The error model and the `Status` message can be used in a variety of
environments, either with or without APIs, to provide a
consistent developer experience across different environments.

Example uses of this error model include:

- Partial errors. If a service needs to return partial errors to the client,
    it may embed the `Status` in the normal response to indicate the partial
    errors.

- Workflow errors. A typical workflow has multiple steps. Each step may
    have a `Status` message for error reporting.

- Batch operations. If a client uses batch request and batch response, the
    `Status` message should be used directly inside batch response, one for
    each error sub-response.

- Asynchronous operations. If an API call embeds asynchronous operation
    results in its response, the status of those operations should be
    represented directly using the `Status` message.

- Logging. If some API errors are stored in logs, the message `Status` could
    be used directly after any stripping needed for security/privacy reasons.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|code|integer(int32)|false|none|The status code, which should be an enum value of [google.rpc.Code][google.rpc.Code].|
|details|[[protobufAny](#schemaprotobufany)]|false|none|A list of messages that carry the error details.  There is a common set of<br />message types for APIs to use.|
|message|string|false|none|A developer-facing error message, which should be in English. Any<br />user-facing error message should be localized and sent in the<br />[google.rpc.Status.details][google.rpc.Status.details] field, or localized by the client.|

<h2 id="tocS_runtimeError">runtimeError</h2>

<a id="schemaruntimeerror"></a>
<a id="schema_runtimeError"></a>
<a id="tocSruntimeerror"></a>
<a id="tocsruntimeerror"></a>

```json
{
  "code": 0,
  "details": [
    {
      "type_url": "string",
      "value": {}
    }
  ],
  "error": "string",
  "message": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|code|integer(int32)|false|none|none|
|details|[[protobufAny](#schemaprotobufany)]|false|none|[`Any` contains an arbitrary serialized protocol buffer message along with a<br />URL that describes the type of the serialized message.<br /><br />Protobuf library provides support to pack/unpack Any values in the form<br />of utility functions or additional generated methods of the Any type.<br /><br />Example 1: Pack and unpack a message in C++.<br /><br />    Foo foo = ...;<br />    Any any;<br />    any.PackFrom(foo);<br />    ...<br />    if (any.UnpackTo(&foo)) {<br />      ...<br />    }<br /><br />Example 2: Pack and unpack a message in Java.<br /><br />    Foo foo = ...;<br />    Any any = Any.pack(foo);<br />    ...<br />    if (any.is(Foo.class)) {<br />      foo = any.unpack(Foo.class);<br />    }<br /><br /> Example 3: Pack and unpack a message in Python.<br /><br />    foo = Foo(...)<br />    any = Any()<br />    any.Pack(foo)<br />    ...<br />    if any.Is(Foo.DESCRIPTOR):<br />      any.Unpack(foo)<br />      ...<br /><br /> Example 4: Pack and unpack a message in Go<br /><br />     foo := &pb.Foo{...}<br />     any, err := ptypes.MarshalAny(foo)<br />     ...<br />     foo := &pb.Foo{}<br />     if err := ptypes.UnmarshalAny(any, foo); err != nil {<br />       ...<br />     }<br /><br />The pack methods provided by protobuf library will by default use<br />'type.googleapis.com/full.type.name' as the type URL and the unpack<br />methods only use the fully qualified type name after the last '/'<br />in the type URL, for example "foo.bar.com/x/y.z" will yield type<br />name "y.z".<br /><br /><br />JSON<br />====<br />The JSON representation of an `Any` value uses the regular<br />representation of the deserialized, embedded message, with an<br />additional field `@type` which contains the type URL. Example:<br /><br />    package google.profile;<br />    message Person {<br />      string first_name = 1;<br />      string last_name = 2;<br />    }<br /><br />    {<br />      "@type": "type.googleapis.com/google.profile.Person",<br />      "firstName": <string>,<br />      "lastName": <string><br />    }<br /><br />If the embedded message type is well-known and has a custom JSON<br />representation, that representation will be embedded adding a field<br />`value` which holds the custom JSON in addition to the `@type`<br />field. Example (for message [google.protobuf.Duration][]):<br /><br />    {<br />      "@type": "type.googleapis.com/google.protobuf.Duration",<br />      "value": "1.212s"<br />    }]|
|error|string|false|none|none|
|message|string|false|none|none|

<h2 id="tocS_runtimeStreamError">runtimeStreamError</h2>

<a id="schemaruntimestreamerror"></a>
<a id="schema_runtimeStreamError"></a>
<a id="tocSruntimestreamerror"></a>
<a id="tocsruntimestreamerror"></a>

```json
{
  "details": [
    {
      "type_url": "string",
      "value": {}
    }
  ],
  "grpc_code": 0,
  "http_code": 0,
  "http_status": "string",
  "message": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|details|[[protobufAny](#schemaprotobufany)]|false|none|[`Any` contains an arbitrary serialized protocol buffer message along with a<br />URL that describes the type of the serialized message.<br /><br />Protobuf library provides support to pack/unpack Any values in the form<br />of utility functions or additional generated methods of the Any type.<br /><br />Example 1: Pack and unpack a message in C++.<br /><br />    Foo foo = ...;<br />    Any any;<br />    any.PackFrom(foo);<br />    ...<br />    if (any.UnpackTo(&foo)) {<br />      ...<br />    }<br /><br />Example 2: Pack and unpack a message in Java.<br /><br />    Foo foo = ...;<br />    Any any = Any.pack(foo);<br />    ...<br />    if (any.is(Foo.class)) {<br />      foo = any.unpack(Foo.class);<br />    }<br /><br /> Example 3: Pack and unpack a message in Python.<br /><br />    foo = Foo(...)<br />    any = Any()<br />    any.Pack(foo)<br />    ...<br />    if any.Is(Foo.DESCRIPTOR):<br />      any.Unpack(foo)<br />      ...<br /><br /> Example 4: Pack and unpack a message in Go<br /><br />     foo := &pb.Foo{...}<br />     any, err := ptypes.MarshalAny(foo)<br />     ...<br />     foo := &pb.Foo{}<br />     if err := ptypes.UnmarshalAny(any, foo); err != nil {<br />       ...<br />     }<br /><br />The pack methods provided by protobuf library will by default use<br />'type.googleapis.com/full.type.name' as the type URL and the unpack<br />methods only use the fully qualified type name after the last '/'<br />in the type URL, for example "foo.bar.com/x/y.z" will yield type<br />name "y.z".<br /><br /><br />JSON<br />====<br />The JSON representation of an `Any` value uses the regular<br />representation of the deserialized, embedded message, with an<br />additional field `@type` which contains the type URL. Example:<br /><br />    package google.profile;<br />    message Person {<br />      string first_name = 1;<br />      string last_name = 2;<br />    }<br /><br />    {<br />      "@type": "type.googleapis.com/google.profile.Person",<br />      "firstName": <string>,<br />      "lastName": <string><br />    }<br /><br />If the embedded message type is well-known and has a custom JSON<br />representation, that representation will be embedded adding a field<br />`value` which holds the custom JSON in addition to the `@type`<br />field. Example (for message [google.protobuf.Duration][]):<br /><br />    {<br />      "@type": "type.googleapis.com/google.protobuf.Duration",<br />      "value": "1.212s"<br />    }]|
|grpc_code|integer(int32)|false|none|none|
|http_code|integer(int32)|false|none|none|
|http_status|string|false|none|none|
|message|string|false|none|none|

<h2 id="tocS_searchRequest">searchRequest</h2>

<a id="schemasearchrequest"></a>
<a id="schema_searchRequest"></a>
<a id="tocSsearchrequest"></a>
<a id="tocssearchrequest"></a>

```json
{
  "headers": {
    "clientAppId": "clientAppId",
    "clientRef": "clientRef",
    "consumerGroup": "consumerGroup",
    "requestTimeout": "2000-01-23T04:56:07Z",
    "transactionRef": [
      "transactionRef",
      "transactionRef"
    ]
  },
  "lang": "string",
  "payload": {
    "expiryTimeout": "2019-08-24T14:15:22Z",
    "location": {
      "location": {
        "lat": 0.8008281904610115,
        "lon": 6.027456183070403
      },
      "radiusKm": 0
    },
    "responseType": "FULL",
    "text": "string",
    "unit": "string"
  },
  "range": {
    "limit": {
      "value": 0
    },
    "offset": {
      "value": 0
    }
  },
  "scope": "GLOBAL"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|headers|[commonHeaders](#schemacommonheaders)|false|none|Common Header definitions<br />Ref: https://github.com/Iotic-Labs/infra/wiki/QAPI-Overview|
|lang|string|false|none|Note: This implies both search and result text language|
|payload|[searchRequestPayload](#schemasearchrequestpayload)|false|none|none|
|range|[commonRange](#schemacommonrange)|false|none|Range if specified *may* be obliged by the backend|
|scope|[commonScope](#schemacommonscope)|false|none|- LOCAL: container-local describe<br /> - LOCAL_OWN: container-local search of own entities only. Scoped to the user associated to this request<br /> - AUTO: equivalent to local and if not found, global|

<h2 id="tocS_searchRequestPayload">searchRequestPayload</h2>

<a id="schemasearchrequestpayload"></a>
<a id="schema_searchRequestPayload"></a>
<a id="tocSsearchrequestpayload"></a>
<a id="tocssearchrequestpayload"></a>

```json
{
  "expiryTimeout": "2019-08-24T14:15:22Z",
  "location": {
    "location": {
      "lat": 0.8008281904610115,
      "lon": 6.027456183070403
    },
    "radiusKm": 0
  },
  "responseType": "FULL",
  "text": "string",
  "unit": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|expiryTimeout|string(date-time)|false|none|UTC time (millis from epoch / unix time) when this search request has to be considered expired.|
|location|[commonGeoCircle](#schemacommongeocircle)|false|none|Approximate location, e.g. for search reduction|
|responseType|[searchResponseType](#schemasearchresponsetype)|false|none|none|
|text|string|false|none|Currently all of these are optional (in that you need a combination of some of these!)|
|unit|string|false|none|none|

<h2 id="tocS_searchResponsePayload">searchResponsePayload</h2>

<a id="schemasearchresponsepayload"></a>
<a id="schema_searchResponsePayload"></a>
<a id="tocSsearchresponsepayload"></a>
<a id="tocssearchresponsepayload"></a>

```json
{
  "entities": [
    {
      "id": {
        "value": "value"
      },
      "label": "label",
      "location": {
        "lat": 6.027456183070403,
        "lon": 1.4658129805029452
      },
      "points": [
        {
          "label": "label",
          "point": {
            "key": {
              "entityId": {
                "value": "value"
              },
              "id": {
                "value": "value"
              }
            }
          },
          "storesRecent": true
        },
        {
          "label": "label",
          "point": {
            "key": {
              "entityId": {
                "value": "value"
              },
              "id": {
                "value": "value"
              }
            }
          },
          "storesRecent": true
        }
      ]
    },
    {
      "id": {
        "value": "value"
      },
      "label": "label",
      "location": {
        "lat": 6.027456183070403,
        "lon": 1.4658129805029452
      },
      "points": [
        {
          "label": "label",
          "point": {
            "key": {
              "entityId": {
                "value": "value"
              },
              "id": {
                "value": "value"
              }
            }
          },
          "storesRecent": true
        },
        {
          "label": "label",
          "point": {
            "key": {
              "entityId": {
                "value": "value"
              },
              "id": {
                "value": "value"
              }
            }
          },
          "storesRecent": true
        }
      ]
    }
  ],
  "status": {
    "code": 0,
    "details": [
      {
        "type_url": "type_url",
        "value": "value"
      },
      {
        "type_url": "type_url",
        "value": "value"
      }
    ],
    "message": "message"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|entities|[[ResponseEntityDetails](#schemaresponseentitydetails)]|false|none|[details of the entity found]|
|responseType|[searchResponseType](#schemasearchresponsetype)|false|none|none|
|status|[rpcStatus](#schemarpcstatus)|false|none|The `Status` type defines a logical error model that is suitable for different<br />programming environments, including REST APIs and RPC APIs. It is used by<br />[gRPC](https://github.com/grpc). The error model is designed to be:<br />- Simple to use and understand for most users<br />- Flexible enough to meet unexpected needs<br /><br /># Overview<br /><br />The `Status` message contains three pieces of data: error code, error message,<br />and error details. The error code should be an enum value of<br />[google.rpc.Code][google.rpc.Code], but it may accept additional error codes if needed.  The<br />error message should be a developer-facing English message that helps<br />developers *understand* and *resolve* the error. If a localized user-facing<br />error message is needed, put the localized message in the error details or<br />localize it in the client. The optional error details may contain arbitrary<br />information about the error. There is a predefined set of error detail types<br />in the package `google.rpc` that can be used for common error conditions.<br /><br /># Language mapping<br /><br />The `Status` message is the logical representation of the error model, but it<br />is not necessarily the actual wire format. When the `Status` message is<br />exposed in different client libraries and different wire protocols, it can be<br />mapped differently. For example, it will likely be mapped to some exceptions<br />in Java, but more likely mapped to some error codes in C.<br /><br /># Other uses<br /><br />The error model and the `Status` message can be used in a variety of<br />environments, either with or without APIs, to provide a<br />consistent developer experience across different environments.<br /><br />Example uses of this error model include:<br /><br />- Partial errors. If a service needs to return partial errors to the client,<br />    it may embed the `Status` in the normal response to indicate the partial<br />    errors.<br /><br />- Workflow errors. A typical workflow has multiple steps. Each step may<br />    have a `Status` message for error reporting.<br /><br />- Batch operations. If a client uses batch request and batch response, the<br />    `Status` message should be used directly inside batch response, one for<br />    each error sub-response.<br /><br />- Asynchronous operations. If an API call embeds asynchronous operation<br />    results in its response, the status of those operations should be<br />    represented directly using the `Status` message.<br /><br />- Logging. If some API errors are stored in logs, the message `Status` could<br />    be used directly after any stripping needed for security/privacy reasons.|

<h2 id="tocS_searchResponseType">searchResponseType</h2>

<a id="schemasearchresponsetype"></a>
<a id="schema_searchResponseType"></a>
<a id="tocSsearchresponsetype"></a>
<a id="tocssearchresponsetype"></a>

```json
"FULL"

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|FULL|
|*anonymous*|REDUCED|
|*anonymous*|LOCATED|
|*anonymous*|MINIMAL|
