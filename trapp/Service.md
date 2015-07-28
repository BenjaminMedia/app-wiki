# Service

Service for creating and retrieving translations.

|Action|Path|Example|Description|
|---|---|---|---|
|GET|[/api/v1/entity](#/get/api/entity)|/api/v1/entity|Returns a list of latest translations.|
|POST|[/api/v1/entity](#/post/api/entity)|/api/v1/entity|Create new translation and returns the id for the new item.|
|GET|[/api/v1/entity/[id]](#/get/api/entity/id)|/api/v1/entity/100|Returns translation with matching id|
|DELETE|[/api/v1/entity/[id]](#/delete/api/entity/id)|/api/v1/entity/100|Delete translation with the matching id|
|PUT|[/api/v1/entity/[id]](#/put/api/entity/id)|/api/v1/entity/100|Update translation with the matching id|

## Parameters

https://github.com/BenjaminMedia/app-wiki/blob/master/bonnier-index-db.wiki/service-content-parameters.md

## Fields

https://github.com/BenjaminMedia/app-wiki/blob/master/bonnier-index-db.wiki/service-content-fields.md

## <a name="/get/api/entity"></a> GET /api/v1/entity
Returns a list of latest translations.

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" https://staging-indexdb.whitealbum.dk/api/content
```

###### Response

```
response
```

### PHP

###### Request

```php
$ch = curl_init('https://staging-indexdb.whitealbum.dk/api/content');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
        
$response = json_decode(curl_exec($ch));
```

###### Response

```php
RESPONSE
```

## <a name="/post/api/entity"></a> POST /api/v1/entity

Creates a new translation of the given type and returns the id for the newly created item.

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" -X POST -d "locale=da-dk&title=My title&image=http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png&content_type=article&publish_at=25-04-2015 15:15&created_at=26-04-2015 15:20&updated_at=27-04-2015 15:30&path=/path&active=true&content_url=http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2" http://staging-indexdb.whitealbum.dk/api/content
```

###### Response

```json
RESPONSE
```

## <a name="/get/api/entity/id"></a> GET /api/v1/entity/[id]

Returns translation with matching id

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" https://staging-indexdb.whitealbum.dk/api/content/472411B3EEE17052A861D1C34DF9C646
```

###### Response

```json
RESPONSE
```

### PHP

###### Request

```php
$ch = curl_init('https://staging-indexdb.whitealbum.dk/api/content/472411B3EEE17052A861D1C34DF9C646');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
        
$response = json_decode(curl_exec($ch));
```

###### Response

```php
RESPONSE
```

## <a name="/put/api/entity/id"></a> PUT /api/v1/entity/[id]
Update item of type with the given id 

### CURL

###### Request
```
curl -H "Auth-Secret: [SECRET]" -X POST -d "_method=PUT&title=My new title&description=My new description" https://staging-indexdb.whitealbum.dk/api/content/C36AF818BE94E41C1F2C52133BF85F33
```

###### Response
```json
RESPONSE
```

### PHP

###### Request

```php
$ch = curl_init('https://staging-indexdb.whitealbum.dk/api/content/5DD845435D7B8BF6E9CDD6094BC79CF3');

$data = array('_method' => 'PUT', 'title' => 'My new title', 'description' => 'My new description');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));

$response = json_decode(curl_exec($ch));
```

###### Response

```php
RESPONSE
```

## <a name="/delete/api/entity/id"></a> DELETE /api/v1/entity/[id]
Delete translation with the matching id

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" -X POST -d "&_method=delete" https://staging-indexdb.whitealbum.dk/api/content/C36AF818BE94E41C1F2C52133BF85F33
```

###### Response

```json
RESPONSE
```

### PHP

###### Request

```php
$ch = curl_init('https://staging-indexdb.whitealbum.dk/api/content/0F18B76A2294449455595381FC49D092');

$data = array('_method' => 'DELETE');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));

$response = json_decode(curl_exec($ch));
```

###### Response

```php
RESPONSE
```
