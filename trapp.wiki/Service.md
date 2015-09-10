# Service

#### Service Calls
Service for creating and retrieving translations.

|Action|Path|Example|Description|
|---|---|---|---|
|GET|[/api/v1/translations](#/get/api/translations)|/api/v1/translations|Returns a list of latest translations.|
|POST|[/api/v1/translations](#/post/api/translations)|/api/v1/translations|Create new translation and returns the id for the new item.|
|GET|[/api/v1/translations/[id]](#/get/api/translations/id)|/api/v1/translations/100|Returns translation with matching id|
|DELETE|[/api/v1/translations/[id]](#/delete/api/translations/id)|/api/v1/translations/100|Delete translation with the matching id|
|PUT|[/api/v1/translations/[id]](#/put/api/translations/id)|/api/v1/translations/100|Update translation with the matching id|

#### Helpers
|Action|Path|Example|Description|
|---|---|---|---|
|GET|[/api/v1/languages](#/get/api/languages)|/api/v1/languages|Returns a list of available languages|
|GET|[/api/v1/states](#/get/api/states)|/api/v1/translations|Returns a list of available states|

## Parameters
This is a list of the parameters supported by the API for filtering and querying items.

For a more detailed description please see: https://github.com/BenjaminMedia/app-wiki/blob/master/trapp.wiki/Parameters.md

|Name|Description|
|---|---|
|[sort](#parameter_sort)|Sort by field|
|[order](#parameter_order)|Order results ascending or descending|
|[locale](#parameter_locale)|Filter the results to only returns items with matching locale(s).|
|[app_id](#parameter_app_id)|Filter the results to only returns items with matching application id.|
|[state](#parameter_state)|Filter results by matching state|
|[q](#parameter_q)|Filters results where meta-data contains the specified value|
|[skip](#parameter_skip)|Skips the entered amount of rows in the result (useful for paging).|
|[limit](#parameter_limit)|Limits the number of rows returned in the result. code|


## Fields

In this section you can see what fields are supported. 

For a more detailed description please see: https://github.com/BenjaminMedia/app-wiki/blob/master/trapp.wiki/Fields.md

|Name|Type|Required|
|---|---|---|
|locale|string|true|
|translate_into|array|true|
|deadline|datetime|true|
|fields|object|true|
|title|string|true|
|state|string|false|
|comment|string|false|
|do_callback|boolean|false|
|update\_endpoint_uri|string|false|

## <a name="/get/api/translations"></a> GET /api/v1/translations
Returns a list of latest translations.

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" https://trapp.whitealbum.dk/api/v1/translations
```
### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));
        
$response = json_decode(curl_exec($ch));

```

#### Response

```
{
   "max":10,
   "skip":null,
   "limit":null,
   "rows":[
      {
         "_id":"55b8f5b2214f48da0900421f",
         "application_id":1,
         "publish_date":{
            "date":"2015-07-05 21:29:34.000000",
            "timezone_type":3,
            "timezone":"UTC"
         },
         "update_endpoint_uri":"http://runolfsdottir.com/",
         "language_id":"55b8f5b2214f48da090041b2",
         "original_entity_id":null,
         "updated_at":"2015-07-29 15:48:02",
         "created_at":"2015-07-29 15:48:02",
         "application":{
            "id":1,
            "display_name":"Translation",
            "username":"Translation",
            "site_code":"trapp",
            "app_code":"trans",
            "last_activity":"2015-07-29 15:43:18",
            "created_at":"2015-07-17 11:47:14",
            "updated_at":"2015-07-29 15:43:18",
            "roles":[
               {
                  "role":"application_index",
                  "app_id":1,
                  "created_at":"2015-07-17 12:40:52",
                  "updated_at":"2015-07-17 12:40:52"
               },
               {
               	... // Removed for simplicity
               }
            ]
         },
         "revisions":[
            {
               "_id":"55b8f5b2214f48da09004220",
               "revision_count":0,
               "comment":"Autem odit laudantium corrupti ut. Aut aut dolor nam illum fuga. Dolorum et fugit aut. Nemo voluptas tenetur dolorem sed.",
               "created_at":"2015-07-19 22:51:55",
               "state_id":"55b8f5b2214f48da090041b8",
               "user_id":"55b8f5b1214f48da090041af",
               "entity_id":"55b8f5b2214f48da0900421f",
               "updated_at":"2015-07-29 15:48:02",
               "field_ids":[
                  "55b8f5b2214f48da09004221"
               ],
               "fields":[
                  {
                     "_id":"55b8f5b2214f48da09004221",
                     "label":"Miss",
                     "value":"Harum pariatur possimus ut itaque illum animi. Qui distinctio id deleniti provident quo. Et vel dolor sed et aspernatur reprehenderit et. Quia tenetur veritatis voluptates omnis.",
                     "display_format":"text",
                     "updated_at":"2015-07-29 15:48:02",
                     "created_at":"2015-07-29 15:48:02",
                     "revision_ids":[
                        "55b8f5b2214f48da09004220"
                     ]
                  },
                  {
                  	... // Removed for simplicity
                  }
               ],
               "state":{
                  "_id":"55b8f5b2214f48da090041b8",
                  "name":"On Hold",
                  "description":"",
                  "state_order":0
               },
               "user":{
                  "_id":"55b8f5b1214f48da090041af",
                  "name":"Miss Shanie Ward",
                  "email":"paula.ullrich@gmail.com",
                  "updated_at":"2015-07-29 15:48:01",
                  "created_at":"2015-07-29 15:48:01"
               }
            },
            {
            	... // Removed for simplicity
            }
         ],
         "original":null,
         "language":{
            "_id":"55b8f5b2214f48da090041b2",
            "name":"Danish",
            "locale":"da_dk"
         },
         {
         	... // Removed for simplicity
         }
      }
   ]
}
```

## <a name="/post/api/translations"></a> POST /api/v1/translations

Creates a new translation of the given type and returns the id for the newly created item.

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" -X POST -d "locale=da-dk&title=My title&image=http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png&content_type=article&publish_at=25-04-2015 15:15&created_at=26-04-2015 15:20&updated_at=27-04-2015 15:30&path=/path&active=true&content_url=http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2" http://trapp.whitealbum.dk/api/v1/translations
```
### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations/5DD845435D7B8BF6E9CDD6094BC79CF3');

$data = array('_method' => 'POST', 'locale' => 'da-dk', 'title' => 'My new title', 'image' => 'http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png', 'content_type' => 'article', 'publish_at' => '25-04-2015 15:15', 'created_at' => '26-04-2015 15:20', 'updated_at' => '27-04-2015 15:30', 'path' => '/path', 'active' => true, 'content_url' => 'http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));

$response = json_decode(curl_exec($ch));
```

###### Response

```json
RESPONSE
```

## <a name="/get/api/translations/id"></a> GET /api/v1/translations/[id]

Returns translation with matching id

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" https://trapp.whitealbum.dk/api/v1/translations/55b8f5b2214f48da0900421f
```

### PHP

###### Request

```php
$ch = curl_init('https://traoo.whitealbum.dk/api/v1/translations/472411B3EEE17052A861D1C34DF9C646');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));
        
$response = json_decode(curl_exec($ch));
```

#### Response

```json
{
   "_id":"55b8f5b2214f48da0900421f",
   "application_id":1,
   "publish_date":{
      "date":"2015-07-05 21:29:34.000000",
      "timezone_type":3,
      "timezone":"UTC"
   },
   "update_endpoint_uri":"http://runolfsdottir.com/",
   "language_id":"55b8f5b2214f48da090041b2",
   "original_entity_id":null,
   "updated_at":"2015-07-29 15:48:02",
   "created_at":"2015-07-29 15:48:02",
   "application":{
      "id":1,
      "display_name":"Translation",
      "username":"Translation",
      "site_code":"trapp",
      "app_code":"trans",
      "last_activity":"2015-07-29 15:43:18",
      "created_at":"2015-07-17 11:47:14",
      "updated_at":"2015-07-29 15:43:18",
      "roles":[
         {
            "role":"application_index",
            "app_id":1,
            "created_at":"2015-07-17 12:40:52",
            "updated_at":"2015-07-17 12:40:52"
         },
         {
           	... // Removed for simplicity
         }
      ]
   },
   "revisions":[
      {
         "_id":"55b8f5b2214f48da09004220",
         "revision_count":0,
         "comment":"Autem odit laudantium corrupti ut. Aut aut dolor nam illum fuga. Dolorum et fugit aut. Nemo voluptas tenetur dolorem sed.",
         "created_at":"2015-07-19 22:51:55",
         "state_id":"55b8f5b2214f48da090041b8",
         "user_id":"55b8f5b1214f48da090041af",
         "entity_id":"55b8f5b2214f48da0900421f",
         "updated_at":"2015-07-29 15:48:02",
         "field_ids":[
            "55b8f5b2214f48da09004221"
         ],
         "fields":[
            {
               "_id":"55b8f5b2214f48da09004221",
               "label":"Miss",
               "value":"Harum pariatur possimus ut itaque illum animi. Qui distinctio id deleniti provident quo. Et vel dolor sed et aspernatur reprehenderit et. Quia tenetur veritatis voluptates omnis.",
               "display_format":"text",
               "updated_at":"2015-07-29 15:48:02",
               "created_at":"2015-07-29 15:48:02",
               "revision_ids":[
                  "55b8f5b2214f48da09004220"
               ]
            }
         ],
         "state":{
            "_id":"55b8f5b2214f48da090041b8",
            "name":"On Hold",
            "description":"",
            "state_order":0
         },
         "user":{
            "_id":"55b8f5b1214f48da090041af",
            "name":"Miss Shanie Ward",
            "email":"paula.ullrich@gmail.com",
            "updated_at":"2015-07-29 15:48:01",
            "created_at":"2015-07-29 15:48:01"
         }
      },
      {
   			... // Removed for simplicity
 	  }
   ],
   "original":null,
   "language":{
      "_id":"55b8f5b2214f48da090041b2",
      "name":"Danish",
      "locale":"da_dk"
   }
}
```

## <a name="/put/api/translations/id"></a> PUT /api/v1/translations/[id]
Update item of type with the given id 

### CURL

###### Request
```
curl -H "Authorization: Basic [TOKEN]" -X POST -d "_method=PUT&title=My new title&description=My new description" https://trapp.whitealbum.dk/api/v1/translations/C36AF818BE94E41C1F2C52133BF85F33
```

### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations/5DD845435D7B8BF6E9CDD6094BC79CF3');

$data = array('_method' => 'PUT', 'title' => 'My new title', 'description' => 'My new description');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));

$response = json_decode(curl_exec($ch));
```

#### Response
```json
{
   "_id":"55b8f5b2214f48da0900421f",
   "application_id":1,
   "publish_date":{
      "date":"2015-07-05 21:29:34.000000",
      "timezone_type":3,
      "timezone":"UTC"
   },
   "update_endpoint_uri":"http://runolfsdottir.com/",
   "language_id":"55b8f5b2214f48da090041b2",
   "original_entity_id":null,
   "updated_at":"2015-07-29 15:48:02",
   "created_at":"2015-07-29 15:48:02",
   "application":{
      "id":1,
      "display_name":"Translation",
      "username":"Translation",
      "site_code":"trapp",
      "app_code":"trans",
      "last_activity":"2015-07-29 15:43:18",
      "created_at":"2015-07-17 11:47:14",
      "updated_at":"2015-07-29 15:43:18",
      "roles":[
         {
            "role":"application_index",
            "app_id":1,
            "created_at":"2015-07-17 12:40:52",
            "updated_at":"2015-07-17 12:40:52"
         },
         {
         	... // Removed for simplicity
         }
      ]
   },
   "revisions":[
      {
         "_id":"55b8f5b2214f48da09004220",
         "revision_count":0,
         "comment":"Autem odit laudantium corrupti ut. Aut aut dolor nam illum fuga. Dolorum et fugit aut. Nemo voluptas tenetur dolorem sed.",
         "created_at":"2015-07-19 22:51:55",
         "state_id":"55b8f5b2214f48da090041b8",
         "user_id":"55b8f5b1214f48da090041af",
         "entity_id":"55b8f5b2214f48da0900421f",
         "updated_at":"2015-07-29 15:48:02",
         "field_ids":[
            "55b8f5b2214f48da09004221"
         ],
         "fields":[
            {
               "_id":"55b8f5b2214f48da09004221",
               "label":"Miss",
               "value":"Harum pariatur possimus ut itaque illum animi. Qui distinctio id deleniti provident quo. Et vel dolor sed et aspernatur reprehenderit et. Quia tenetur veritatis voluptates omnis.",
               "display_format":"text",
               "updated_at":"2015-07-29 15:48:02",
               "created_at":"2015-07-29 15:48:02",
               "revision_ids":[
                  "55b8f5b2214f48da09004220"
               ]
            }
         ],
         "state":{
            "_id":"55b8f5b2214f48da090041b8",
            "name":"On Hold",
            "description":"",
            "state_order":0
         },
         "user":{
            "_id":"55b8f5b1214f48da090041af",
            "name":"Miss Shanie Ward",
            "email":"paula.ullrich@gmail.com",
            "updated_at":"2015-07-29 15:48:01",
            "created_at":"2015-07-29 15:48:01"
         }
      },
      {
      	... // Removed for simplicity
      }
   "original":null,
   "language":{
      "_id":"55b8f5b2214f48da090041b2",
      "name":"Danish",
      "locale":"da_dk"
   }
}
```

## <a name="/delete/api/translations/id"></a> DELETE /api/v1/translations/[id]
Delete translation with the matching id

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" -X POST -d "&_method=delete" https://trapp.whitealbum.dk/api/v1/translations/C36AF818BE94E41C1F2C52133BF85F33
```

### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations/0F18B76A2294449455595381FC49D092');

$data = array('_method' => 'DELETE');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));

$response = json_decode(curl_exec($ch));
```

#### Response

```json
{
	"id": "C36AF818BE94E41C1F2C52133BF85F33",
	"deleted": true
}
```

## <a name="/get/api/states"></a> GET /api/v1/states
Get a list of states a translation can be in.

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" -X POST -d "&_method=delete" https://trapp.whitealbum.dk/api/v1/translations/C36AF818BE94E41C1F2C52133BF85F33
```

### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations/0F18B76A2294449455595381FC49D092');

$data = array('_method' => 'DELETE');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));

$response = json_decode(curl_exec($ch));
```

#### Response

```json
{
"total": 4,
"rows": [
	"state-waiting",
	"state-missing",
	"state-progress",
	"state-translated"
	]
}
```

## <a name="/get/api/languages"></a> GET /api/v1/languages
Get a list of states a translation can be in.

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" -X POST -d "&_method=delete" https://trapp.whitealbum.dk/api/v1/translations/C36AF818BE94E41C1F2C52133BF85F33
```

### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations/0F18B76A2294449455595381FC49D092');

$data = array('_method' => 'DELETE');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));

$response = json_decode(curl_exec($ch));
```

#### Response

```json
{
"total": 4,
"rows": [
		{
		"_id": "55f0343345726eb0500041b1",
		"name": "Danish",
		"locale": "da_dk",
		"country": "Denmark"
		},
		{
		"_id": "55f0343345726eb0500041b2",
		"name": "English",
		"locale": "en_gb",
		"country": "United Kingdom"
		},
		{
		"_id": "55f0343345726eb0500041b3",
		"name": "Finnish",
		"locale": "fi_fi",
		"country": "Finland"
		},
		{
		"_id": "55f0343345726eb0500041b4",
		"name": "Swedish",
		"locale": "sv_se",
		"country": "Sweden"
		},
		{
		"_id": "55f0343345726eb0500041b5",
		"name": "Norwegian",
		"locale": "nb_no",
		"country": "Norway"
		},
		{
		"_id": "55f0343345726eb0500041b6",
		"name": "Dutch",
		"locale": "nl_nl",
		"country": "Netherlands"
		}
	]
}
```
	