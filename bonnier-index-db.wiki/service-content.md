# api/v1/content

Service for creating and retrieving content.

|Action|Path|Example|Description|
|---|---|---|---|
|GET|[/api/v1/content](#/get/api/content)|/api/v1/content|Returns a list of latest items.|
|POST|[/api/v1/content](#/post/api/content)|/api/v1/content|Create new item of type “content” and returns the id for the new item.|
|GET|[/api/v1/content/[id]](#/get/api/content/id)|/api/v1/content/100|Returns matching id content with the matching id|
|PUT|[/api/v1/content/[id]](#/put/api/content/id)|/api/v1/content/100|Update content with the matching id|
|DELETE|[/api/v1/content/[id]](#/delete/api/content/id)|/api/v1/content/100|Delete content with the matching id|

## Parameters

[View parameters](service-content-parameters.md)

## Fields

[View fields](service-content-fields.md)

## <a name="/get/api/v1/content"></a> GET /api/v1/content
Returns a list of latest items.

### Request

###### Curl

```
curl -H "Auth-Secret: [SECRET]" https://indexdb.whitealbum.dk/api/v1/content
```

###### PHP

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/v1/content');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
        
$response = json_decode(curl_exec($ch));
```

### Response

```
{
  "total": 2,
  "skip": "0",
  "limit": "0",
  "searchTime": 1,
  "rows": [
    {
      "id": "AD5FA9C3F420D517CF398517F93B1787",
      "type": "content",
      "app_id": 4,
      "active": true,
      "content_type": "article",
      "content_url": "http://woman.dk/dette-nummer/woman-nr-102",
      "created_at": "2007-10-25T00:00:00+00:00",
      "image": "http://bonnier.imgix.net/cdn-connect/5fe9c540189e46fca5f0a15c7182d612.jpg",
      "locale": "da_DK",
      "title": "Woman nr. 102",
      "updated_at": "2015-07-24T09:35:39+00:00",
      "relative_content_url": "/dette-nummer/woman-nr-102",
      "parent_id": null,
      "images": {
        "small": {
          "url": "http://bonnier.imgix.net/cdn-connect/5fe9c540189e46fca5f0a15c7182d612.jpg?w=150&h=150",
          "width": 150,
          "height": 150
        },
        "medium": {
          "url": "http://bonnier.imgix.net/cdn-connect/5fe9c540189e46fca5f0a15c7182d612.jpg?w=300&h=300",
          "width": 300,
          "height": 300
        },
        "large": {
          "url": "http://bonnier.imgix.net/cdn-connect/5fe9c540189e46fca5f0a15c7182d612.jpg?w=1024&h=1024",
          "width": 1024,
          "height": 1024
        },
        "original": {
          "url": "http://bonnier.imgix.net/cdn-connect/5fe9c540189e46fca5f0a15c7182d612.jpg",
          "width": 100,
          "height": 133
        }
      },
      "publish_at": "2007-10-25T00:00:00+00:00"
    },
    {
      "id": "79B1289C18FB1DA2270D78419255286B",
      "type": "content",
      "app_id": 4,
      "active": true,
      "content_type": "article",
      "content_url": "http://woman.dk/mode/rens-dit-eget-toj-derhjemme",
      "created_at": "2005-11-02T14:58:15+00:00",
      "image": "http://bonnier.imgix.net/cdn-connect/0b6c3dbd3763459983f93ccbdadfd6c3.jpg",
      "locale": "da_DK",
      "title": "Rens dit eget tøj derhjemme",
      "updated_at": "2015-07-24T09:35:40+00:00",
      "relative_content_url": "/mode/rens-dit-eget-toj-derhjemme",
      "parent_id": null,
      "images": {
        "small": {
          "url": "http://bonnier.imgix.net/cdn-connect/0b6c3dbd3763459983f93ccbdadfd6c3.jpg?w=150&h=150",
          "width": 150,
          "height": 150
        },
        "medium": {
          "url": "http://bonnier.imgix.net/cdn-connect/0b6c3dbd3763459983f93ccbdadfd6c3.jpg?w=300&h=300",
          "width": 300,
          "height": 300
        },
        "large": {
          "url": "http://bonnier.imgix.net/cdn-connect/0b6c3dbd3763459983f93ccbdadfd6c3.jpg?w=1024&h=1024",
          "width": 1024,
          "height": 1024
        },
        "original": {
          "url": "http://bonnier.imgix.net/cdn-connect/0b6c3dbd3763459983f93ccbdadfd6c3.jpg",
          "width": 191,
          "height": 107
        }
      },
      "publish_at": "2005-11-02T14:58:15+00:00"
    }
  ]
}
```

## <a name="/post/api/content"></a> POST /api/v1/content

Creates a new item of the given type and returns the id for the newly created item.

### Request

###### Curl

```
curl -H "Auth-Secret: [SECRET]" -X POST -d "locale=da-dk&title=My title&image=http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png&content_type=article&publish_at=25-04-2015 15:15&created_at=26-04-2015 15:20&updated_at=27-04-2015 15:30&active=true&content_url=http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2" http://indexdb.whitealbum.dk/api/v1/content
```

###### PHP
```php
$data = array('title' => 'My title', 'locale' => 'da-dk', 'content_url' => 'http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2', 'image' => 'http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png', 'content_type' => 'article', '', 'publish_at' => '25-04-2015 15:15', 'created_at' => '26-04-2015 15:20', 'updated_at' => '27-04-2015 15:30', 'active' => TRUE);

$ch = curl_init('http://indexdb.whitealbum.dk/api/v1/content');
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));

$response = json_decode(curl_exec($ch));
```


### Response

```json
{
  "id": "CED6A573C006F5EAC3125B14FF0F37A3",
  "type": "content",
  "app_id": 1,
  "locale": "da_dk",
  "title": "My Title",
  "content_type": "article",
  "created_at": "2015-04-26T15:20:00+00:00",
  "updated_at": "2015-04-26T15:20:00+00:00",
  "active": true,
  "content_url": "http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2",
  "relative_content_url": "/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2",
  "parent_id": null,
  "images": {
    "small": {
      "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=150&h=150",
      "width": 150,
      "height": 150
    },
    "medium": {
      "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=300&h=300",
      "width": 300,
      "height": 300
    },
    "large": {
      "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=1024&h=1024",
      "width": 1024,
      "height": 1024
    },
    "original": {
      "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png",
      "width": 1722,
      "height": 1291
    }
  },
  "publish_at": "2015-04-25T15:15:00+00:00",
  "indexsearch_created_at": "2015-10-02T12:44:44+00:00",
  "indexsearch_updated_at": "2015-10-02T12:44:44+00:00"
}
```

## <a name="/get/api/content/id"></a> GET /api/v1/content/[id]

Returns type with matching id

### Request

###### Curl

```
curl -H "Auth-Secret: [SECRET]" https://indexdb.whitealbum.dk/api/v1/content/CED6A573C006F5EAC3125B14FF0F37A3
```
###### PHP

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/v1/content/C36AF818BE94E41C1F2C52133BF85F33');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
        
$response = json_decode(curl_exec($ch));
```

### Response

```json
{
    "id": "CED6A573C006F5EAC3125B14FF0F37A3",
    "type": "content",
    "app_id": 1,
    "locale": "da_dk",
    "title": "My Title",
    "content_type": "article",
    "created_at": "2015-04-26T15:20:00+00:00",
    "updated_at": "2015-04-26T15:20:00+00:00",
    "active": true,
    "content_url": "http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2",
    "relative_content_url": "/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2",
    "parent_id": null,
    "images": {
        "small": {
            "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=150&h=150",
            "width": 150,
            "height": 150
        },
        "medium": {
            "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=300&h=300",
            "width": 300,
            "height": 300
        },
        "large": {
            "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=1024&h=1024",
            "width": 1024,
            "height": 1024
        },
        "original": {
            "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png",
            "width": 1722,
            "height": 1291
        }
    },
    "publish_at": "2015-04-25T15:15:00+00:00",
    "indexsearch_created_at": "2015-10-02T12:44:44+00:00",
    "indexsearch_updated_at": "2015-10-02T12:44:44+00:00"
}
```

## <a name="/put/api/content/id"></a> PUT /api/v1/content/[id]
Update item of type with the given id 

### Request

###### Curl
```
curl -H "Auth-Secret: [SECRET]" -X POST -d "_method=PUT&title=My new title&description=My new description" https://indexdb.whitealbum.dk/api/v1/content/C36AF818BE94E41C1F2C52133BF85F33
```
###### PHP

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/v1/content/C36AF818BE94E41C1F2C52133BF85F33');

$data = array('_method' => 'PUT', 'title' => 'My new title', 'description' => 'My new description');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));

$response = json_decode(curl_exec($ch));
```

### Response
```json
{
    "id": "C36AF818BE94E41C1F2C52133BF85F33",
    "type": "content",
    "app_id": 1,
    "locale": "da_dk",
    "title": "My Title",
    "content_type": "article",
    "created_at": "2015-04-26T15:20:00+00:00",
    "updated_at": "2015-04-26T15:20:00+00:00",
    "active": true,
    "content_url": "http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2",
    "relative_content_url": "/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2",
    "parent_id": null,
    "images": {
        "small": {
            "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=150&h=150",
            "width": 150,
            "height": 150
        },
        "medium": {
            "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=300&h=300",
            "width": 300,
            "height": 300
        },
        "large": {
            "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=1024&h=1024",
            "width": 1024,
            "height": 1024
        },
        "original": {
            "url": "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png",
            "width": 1722,
            "height": 1291
        }
    },
    "publish_at": "2015-04-25T15:15:00+00:00",
    "indexsearch_created_at": "2015-10-02T12:44:44+00:00",
    "indexsearch_updated_at": "2015-10-02T12:53:39+00:00"
}
```

## <a name="/delete/api/content/id"></a> DELETE /api/v1/content/[id]
Delete content with the matching id

### Request

###### Curl

```
curl -H "Auth-Secret: [SECRET]" -X POST -d "&_method=delete" https://indexdb.whitealbum.dk/api/v1/content/C36AF818BE94E41C1F2C52133BF85F33
```
###### PHP

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/v1/content/C36AF818BE94E41C1F2C52133BF85F33');

$data = array('_method' => 'DELETE');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));

$response = json_decode(curl_exec($ch));
```

### Response

```json
{  
   "id":"C36AF818BE94E41C1F2C52133BF85F33",
   "deleted":true
}
```