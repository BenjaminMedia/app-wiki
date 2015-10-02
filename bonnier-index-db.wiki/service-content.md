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

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" https://indexdb.whitealbum.dk/api/v1/content
```

###### Response

```
{  
   "total":91,
   "skip":0,
   "limit":0,
   "searchTime":1,
   "rows":[  
      {  
         "id":"472411B3EEE17052A861D1C34DF9C646",
         "type":"content",
         "app_id":1,
         "locale":"da-dk",
         "title":"min titel",
         "image":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg",
         "description":"hello",
         "content_type":"article",
         "content_url":"http:\/\/www.dr.dk\/hej",
         "active":true,
         "created_at":"2015-02-10T00:00:00+00:00",
         "updated_at":"2015-02-10T00:00:00+00:00",
         "relative_content_url":"\/hej",
         "images":{  
            "small":{  
               "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=150&h=150",
               "width":150,
               "height":150
            },
            "medium":{  
               "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=300&h=300",
               "width":300,
               "height":300
            },
            "large":{  
               "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=1024&h=1024",
               "width":1024,
               "height":1024
            },
            "original":{  
               "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg",
               "width":833,
               "height":576
            }
         },
         "publish_at":"2015-02-10T00:00:00+00:00"
      },
      {  
         "id":"7581E513EF8B9AA14EA3145CEED6A91F",
         "type":"content",
         "app_id":1,
         "locale":"da-dk",
         "title":"test",
         "description":"hej",
         "active":true,
         "created_at":"1990-04-06T01:10:00+00:00",
         "updated_at":"1990-04-06T03:40:00+00:00",
         "content_type":"article",
         "content_url":"http:\/\/www.google.dk\/test",
         "image":"http:\/\/bonnier.imgix.net\/greasedeathmetal-sT2lsC5k73jPB1zmDFZPgg.jpg",
         "relative_content_url":"\/test",
         "images":{  
            "small":{  
               "url":"http:\/\/bonnier.imgix.net\/greasedeathmetal-sT2lsC5k73jPB1zmDFZPgg.jpg?w=150&h=150",
               "width":150,
               "height":150
            },
            "medium":{  
               "url":"http:\/\/bonnier.imgix.net\/greasedeathmetal-sT2lsC5k73jPB1zmDFZPgg.jpg?w=300&h=300",
               "width":300,
               "height":300
            },
            "large":{  
               "url":"http:\/\/bonnier.imgix.net\/greasedeathmetal-sT2lsC5k73jPB1zmDFZPgg.jpg?w=1024&h=1024",
               "width":1024,
               "height":1024
            },
            "original":{  
               "url":"http:\/\/bonnier.imgix.net\/greasedeathmetal-sT2lsC5k73jPB1zmDFZPgg.jpg",
               "width":1200,
               "height":749
            }
         },
         "publish_at":"1990-04-06T01:10:00+00:00"
      }
   ]
}
```

### PHP

###### Request

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/v1/content');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
        
$response = json_decode(curl_exec($ch));
```

###### Response

```php
object(stdClass)#17 (5) {
  ["total"]=>
  int(91)
  ["skip"]=>
  int(0)
  ["limit"]=>
  string(1) "2"
  ["searchTime"]=>
  int(1)
  ["rows"]=>
  array(2) {
    [0]=>
    object(stdClass)#18 (15) {
      ["id"]=>
      string(32) "472411B3EEE17052A861D1C34DF9C646"
      ["type"]=>
      string(7) "content"
      ["app_id"]=>
      int(1)
      ["locale"]=>
      string(5) "da-dk"
      ["title"]=>
      string(9) "min titel"
      ["image"]=>
      string(68) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg"
      ["description"]=>
      string(5) "hello"
      ["content_type"]=>
      string(7) "article"
      ["content_url"]=>
      string(20) "http://www.dr.dk/hej"
      ["active"]=>
      bool(true)
      ["created_at"]=>
      string(25) "2015-02-10T00:00:00+00:00"
      ["updated_at"]=>
      string(25) "2015-02-10T00:00:00+00:00"
      ["relative_content_url"]=>
      string(4) "/hej"
      ["images"]=>
      object(stdClass)#19 (4) {
        ["small"]=>
        object(stdClass)#20 (3) {
          ["url"]=>
          string(80) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=150&h=150"
          ["width"]=>
          int(150)
          ["height"]=>
          int(150)
        }
        ["medium"]=>
        object(stdClass)#21 (3) {
          ["url"]=>
          string(80) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=300&h=300"
          ["width"]=>
          int(300)
          ["height"]=>
          int(300)
        }
        ["large"]=>
        object(stdClass)#22 (3) {
          ["url"]=>
          string(82) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=1024&h=1024"
          ["width"]=>
          int(1024)
          ["height"]=>
          int(1024)
        }
        ["original"]=>
        object(stdClass)#23 (3) {
          ["url"]=>
          string(68) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg"
          ["width"]=>
          int(833)
          ["height"]=>
          int(576)
        }
      }
      ["publish_at"]=>
      string(25) "2015-02-10T00:00:00+00:00"
    }
    [1]=>
    object(stdClass)#24 (15) {
      ["id"]=>
      string(32) "7581E513EF8B9AA14EA3145CEED6A91F"
      ["type"]=>
      string(7) "content"
      ["app_id"]=>
      int(1)
      ["locale"]=>
      string(5) "da-dk"
      ["title"]=>
      string(4) "test"
      ["description"]=>
      string(3) "hej"
      ["active"]=>
      bool(true)
      ["created_at"]=>
      string(25) "1990-04-06T01:10:00+00:00"
      ["updated_at"]=>
      string(25) "1990-04-06T03:40:00+00:00"
      ["content_type"]=>
      string(7) "article"
      ["content_url"]=>
      string(25) "http://www.google.dk/test"
      ["image"]=>
      string(68) "http://bonnier.imgix.net/greasedeathmetal-sT2lsC5k73jPB1zmDFZPgg.jpg"
      ["relative_content_url"]=>
      string(5) "/test"
      ["images"]=>
      object(stdClass)#25 (4) {
        ["small"]=>
        object(stdClass)#26 (3) {
          ["url"]=>
          string(80) "http://bonnier.imgix.net/greasedeathmetal-sT2lsC5k73jPB1zmDFZPgg.jpg?w=150&h=150"
          ["width"]=>
          int(150)
          ["height"]=>
          int(150)
        }
        ["medium"]=>
        object(stdClass)#27 (3) {
          ["url"]=>
          string(80) "http://bonnier.imgix.net/greasedeathmetal-sT2lsC5k73jPB1zmDFZPgg.jpg?w=300&h=300"
          ["width"]=>
          int(300)
          ["height"]=>
          int(300)
        }
        ["large"]=>
        object(stdClass)#28 (3) {
          ["url"]=>
          string(82) "http://bonnier.imgix.net/greasedeathmetal-sT2lsC5k73jPB1zmDFZPgg.jpg?w=1024&h=1024"
          ["width"]=>
          int(1024)
          ["height"]=>
          int(1024)
        }
        ["original"]=>
        object(stdClass)#29 (3) {
          ["url"]=>
          string(68) "http://bonnier.imgix.net/greasedeathmetal-sT2lsC5k73jPB1zmDFZPgg.jpg"
          ["width"]=>
          int(1200)
          ["height"]=>
          int(749)
        }
      }
      ["publish_at"]=>
      string(25) "1990-04-06T01:10:00+00:00"
    }
  }
}
```

## <a name="/post/api/content"></a> POST /api/v1/content

Creates a new item of the given type and returns the id for the newly created item.

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" -X POST -d "locale=da-dk&title=My title&image=http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png&content_type=article&publish_at=25-04-2015 15:15&created_at=26-04-2015 15:20&updated_at=27-04-2015 15:30&active=true&content_url=http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2" http://indexdb.whitealbum.dk/api/v1/content
```

###### Response

```json
{  
   "id":"E96C33F8D181A3A414802DE852510403",
   "type":"content",
   "app_id":1,
   "locale":"da-dk",
   "title":"My title",
   "image":"http:\/\/bonnier.imgix.net\/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png",
   "content_type":"article",
   "created_at":"2015-04-26T15:20:00+00:00",
   "updated_at":"2015-04-27T15:30:00+00:00",
   "active":true,
   "content_url":"http:\/\/mmm.dk\/konkurrencer\/vind-en-ted-bamse-to-billetter-til-ted-2",
   "relative_content_url":"\/konkurrencer\/vind-en-ted-bamse-to-billetter-til-ted-2",
   "parent_id":null,
   "images":{  
      "small":{  
         "url":"http:\/\/bonnier.imgix.net\/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=150&h=150",
         "width":150,
         "height":150
      },
      "medium":{  
         "url":"http:\/\/bonnier.imgix.net\/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=300&h=300",
         "width":300,
         "height":300
      },
      "large":{  
         "url":"http:\/\/bonnier.imgix.net\/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=1024&h=1024",
         "width":1024,
         "height":1024
      },
      "original":{  
         "url":"http:\/\/bonnier.imgix.net\/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png",
         "width":1722,
         "height":1291
      }
   },
   "publish_at":"2015-04-25T15:15:00+00:00"
}
```

### PHP

###### Request

```php
$data = array('title' => 'My title', 'locale' => 'da-dk', 'content_url' => 'http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2', 'image' => 'http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png', 'content_type' => 'article', '', 'publish_at' => '25-04-2015 15:15', 'created_at' => '26-04-2015 15:20', 'updated_at' => '27-04-2015 15:30', 'active' => TRUE);

$ch = curl_init('http://indexdb.whitealbum.dk/api/v1/content');
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));

$response = json_decode(curl_exec($ch));
```

###### Response

```php
object(stdClass)#17 (15) {
  ["id"]=>
  string(32) "AB4EEB4B3EE0DBD99F9F34C28E568FD6"
  ["type"]=>
  string(7) "content"
  ["app_id"]=>
  int(1)
  ["title"]=>
  string(8) "My title"
  ["locale"]=>
  string(5) "da-dk"
  ["content_url"]=>
  string(67) "http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2"
  ["image"]=>
  string(58) "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png"
  ["content_type"]=>
  string(7) "article"
  ["created_at"]=>
  string(25) "2015-04-26T15:20:00+00:00"
  ["updated_at"]=>
  string(25) "2015-04-27T15:30:00+00:00"
  ["active"]=>
  bool(true)
  ["relative_content_url"]=>
  string(54) "/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2"
  ["parent_id"]=>
  NULL
  ["images"]=>
  object(stdClass)#18 (4) {
    ["small"]=>
    object(stdClass)#19 (3) {
      ["url"]=>
      string(70) "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=150&h=150"
      ["width"]=>
      int(150)
      ["height"]=>
      int(150)
    }
    ["medium"]=>
    object(stdClass)#20 (3) {
      ["url"]=>
      string(70) "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=300&h=300"
      ["width"]=>
      int(300)
      ["height"]=>
      int(300)
    }
    ["large"]=>
    object(stdClass)#21 (3) {
      ["url"]=>
      string(72) "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png?w=1024&h=1024"
      ["width"]=>
      int(1024)
      ["height"]=>
      int(1024)
    }
    ["original"]=>
    object(stdClass)#22 (3) {
      ["url"]=>
      string(58) "http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png"
      ["width"]=>
      int(1722)
      ["height"]=>
      int(1291)
    }
  }
  ["publish_at"]=>
  string(25) "2015-04-25T15:15:00+00:00"
}
```

## <a name="/get/api/content/id"></a> GET /api/v1/content/[id]

Returns type with matching id

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" https://indexdb.whitealbum.dk/api/v1/content/472411B3EEE17052A861D1C34DF9C646
```

###### Response

```json
{  
   "id":"472411B3EEE17052A861D1C34DF9C646",
   "type":"content",
   "app_id":1,
   "locale":"da-dk",
   "title":"min titel",
   "image":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg",
   "description":"hello",
   "content_type":"article",
   "content_url":"http:\/\/www.dr.dk\/hej",
   "active":true,
   "created_at":"2015-02-10T00:00:00+00:00",
   "updated_at":"2015-02-10T00:00:00+00:00",
   "relative_content_url":"\/hej",
   "images":{  
      "small":{  
         "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=150&h=150",
         "width":150,
         "height":150
      },
      "medium":{  
         "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=300&h=300",
         "width":300,
         "height":300
      },
      "large":{  
         "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=1024&h=1024",
         "width":1024,
         "height":1024
      },
      "original":{  
         "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg",
         "width":833,
         "height":576
      }
   },
   "publish_at":"2015-02-10T00:00:00+00:00"
}
```

### PHP

###### Request

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/v1/content/472411B3EEE17052A861D1C34DF9C646');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
        
$response = json_decode(curl_exec($ch));
```

###### Response

```php
object(stdClass)#17 (15) {
  ["id"]=>
  string(32) "472411B3EEE17052A861D1C34DF9C646"
  ["type"]=>
  string(7) "content"
  ["app_id"]=>
  int(1)
  ["locale"]=>
  string(5) "da-dk"
  ["title"]=>
  string(9) "min titel"
  ["image"]=>
  string(68) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg"
  ["description"]=>
  string(5) "hello"
  ["content_type"]=>
  string(7) "article"
  ["content_url"]=>
  string(20) "http://www.dr.dk/hej"
  ["active"]=>
  bool(true)
  ["created_at"]=>
  string(25) "2015-02-10T00:00:00+00:00"
  ["updated_at"]=>
  string(25) "2015-02-10T00:00:00+00:00"
  ["relative_content_url"]=>
  string(4) "/hej"
  ["images"]=>
  object(stdClass)#18 (4) {
    ["small"]=>
    object(stdClass)#19 (3) {
      ["url"]=>
      string(80) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=150&h=150"
      ["width"]=>
      int(150)
      ["height"]=>
      int(150)
    }
    ["medium"]=>
    object(stdClass)#20 (3) {
      ["url"]=>
      string(80) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=300&h=300"
      ["width"]=>
      int(300)
      ["height"]=>
      int(300)
    }
    ["large"]=>
    object(stdClass)#21 (3) {
      ["url"]=>
      string(82) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=1024&h=1024"
      ["width"]=>
      int(1024)
      ["height"]=>
      int(1024)
    }
    ["original"]=>
    object(stdClass)#22 (3) {
      ["url"]=>
      string(68) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg"
      ["width"]=>
      int(833)
      ["height"]=>
      int(576)
    }
  }
  ["publish_at"]=>
  string(25) "2015-02-10T00:00:00+00:00"
}
```

## <a name="/put/api/content/id"></a> PUT /api/v1/content/[id]
Update item of type with the given id 

### CURL

###### Request
```
curl -H "Auth-Secret: [SECRET]" -X POST -d "_method=PUT&title=My new title&description=My new description" https://indexdb.whitealbum.dk/api/v1/content/C36AF818BE94E41C1F2C52133BF85F33
```

###### Response
```json
{  
   "id":"472411B3EEE17052A861D1C34DF9C646",
   "type":"content",
   "app_id":1,
   "locale":"da-dk",
   "title":"min titel",
   "image":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg",
   "description":"hello",
   "content_type":"article",
   "content_url":"http:\/\/www.dr.dk\/hej",
   "active":true,
   "created_at":"2015-02-10T00:00:00+00:00",
   "updated_at":"2015-02-10T00:00:00+00:00",
   "relative_content_url":"\/hej",
   "images":{  
      "small":{  
         "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=150&h=150",
         "width":150,
         "height":150
      },
      "medium":{  
         "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=300&h=300",
         "width":300,
         "height":300
      },
      "large":{  
         "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=1024&h=1024",
         "width":1024,
         "height":1024
      },
      "original":{  
         "url":"http:\/\/bonnier.imgix.net\/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg",
         "width":833,
         "height":576
      }
   },
   "publish_at":"2015-02-10T00:00:00+00:00"
}
```

### PHP

###### Request

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/v1/content/5DD845435D7B8BF6E9CDD6094BC79CF3');

$data = array('_method' => 'PUT', 'title' => 'My new title', 'description' => 'My new description');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));

$response = json_decode(curl_exec($ch));
```

###### Response

```php
object(stdClass)#17 (15) {
  ["id"]=>
  string(32) "472411B3EEE17052A861D1C34DF9C646"
  ["type"]=>
  string(7) "content"
  ["app_id"]=>
  int(1)
  ["locale"]=>
  string(5) "da-dk"
  ["title"]=>
  string(9) "min titel"
  ["image"]=>
  string(68) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg"
  ["description"]=>
  string(5) "hello"
  ["content_type"]=>
  string(7) "article"
  ["content_url"]=>
  string(20) "http://www.dr.dk/hej"
  ["active"]=>
  bool(true)
  ["created_at"]=>
  string(25) "2015-02-10T00:00:00+00:00"
  ["updated_at"]=>
  string(25) "2015-02-10T00:00:00+00:00"
  ["relative_content_url"]=>
  string(4) "/hej"
  ["images"]=>
  object(stdClass)#18 (4) {
    ["small"]=>
    object(stdClass)#19 (3) {
      ["url"]=>
      string(80) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=150&h=150"
      ["width"]=>
      int(150)
      ["height"]=>
      int(150)
    }
    ["medium"]=>
    object(stdClass)#20 (3) {
      ["url"]=>
      string(80) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=300&h=300"
      ["width"]=>
      int(300)
      ["height"]=>
      int(300)
    }
    ["large"]=>
    object(stdClass)#21 (3) {
      ["url"]=>
      string(82) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg?w=1024&h=1024"
      ["width"]=>
      int(1024)
      ["height"]=>
      int(1024)
    }
    ["original"]=>
    object(stdClass)#22 (3) {
      ["url"]=>
      string(68) "http://bonnier.imgix.net/nej-til-blowjobs-4HQX7r9NziCc3jrULQtx6w.jpg"
      ["width"]=>
      int(833)
      ["height"]=>
      int(576)
    }
  }
  ["publish_at"]=>
  string(25) "2015-02-10T00:00:00+00:00"
}
```

## <a name="/delete/api/content/id"></a> DELETE /api/v1/content/[id]
Delete content with the matching id

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" -X POST -d "&_method=delete" https://indexdb.whitealbum.dk/api/v1/content/C36AF818BE94E41C1F2C52133BF85F33
```

###### Response

```json
{  
   "id":"0F18B76A2294449455595381FC49D092",
   "deleted":true
}
```

### PHP

###### Request

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/v1/content/0F18B76A2294449455595381FC49D092');

$data = array('_method' => 'DELETE');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));

$response = json_decode(curl_exec($ch));
```

###### Response

```php
object(stdClass)#17 (2) {
  ["id"]=>
  string(32) "0F18B76A2294449455595381FC49D092"
  ["deleted"]=>
  bool(true)
}
```
