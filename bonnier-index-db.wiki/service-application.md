# api/applications

Service for retrieving information about apps created on the platform.

|Action|Path|Example|Description|
|---|---|---|---|
|GET|[/api/applications/](#/get/api/applications)|/api/applications|Returns a list of all applications.|
|GET|[/api/applications/[id]](#/get/api/applications/id)|/api/applications/100|Return application with matching id.|

## <a name="/get/api/applications"></a> GET /api/applications

Returns a list of all applications.

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" https://indexdb.whitealbum.dk/api/application
```

###### Response

```json
{  
   "max":1,
   "rows":[  
      {  
         "id":1,
         "display_name":"Illustreret videnskab",
         "name":"IllustreretVidenskab",
         "site_code":"ilvid",
         "app_code":"cd_ark",
         "locale":"",
         "last_activity":"2015-07-13 09:59:03",
         "created_at":"2015-07-10 13:51:02",
         "updated_at":"2015-07-13 09:59:03",
         "roles":[  
            "application_index",
            "application_show",
            "content_destroy",
            "content_index",
            "content_show",
            "content_store",
            "content_update",
            "contenttype_index",
            "contenttype_show",
            "translate_create"
         ]
      }
   ]
}
```

### PHP

###### Request

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/application');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
        
$response = json_decode(curl_exec($ch));
```

###### Response

```php
object(stdClass)#17 (2) {
  ["max"]=>
  int(1)
  ["rows"]=>
  array(1) {
    [0]=>
    object(stdClass)#18 (10) {
      ["id"]=>
      int(1)
      ["display_name"]=>
      string(21) "Illustreret videnskab"
      ["name"]=>
      string(20) "IllustreretVidenskab"
      ["site_code"]=>
      string(5) "ilvid"
      ["app_code"]=>
      string(6) "cd_ark"
      ["locale"]=>
      string(0) ""
      ["last_activity"]=>
      string(19) "2015-07-13 10:07:34"
      ["created_at"]=>
      string(19) "2015-07-10 13:51:02"
      ["updated_at"]=>
      string(19) "2015-07-13 10:07:34"
      ["roles"]=>
      array(10) {
        [0]=>
        string(17) "application_index"
        [1]=>
        string(16) "application_show"
        [2]=>
        string(15) "content_destroy"
        [3]=>
        string(13) "content_index"
        [4]=>
        string(12) "content_show"
        [5]=>
        string(13) "content_store"
        [6]=>
        string(14) "content_update"
        [7]=>
        string(17) "contenttype_index"
        [8]=>
        string(16) "contenttype_show"
        [9]=>
        string(16) "translate_create"
      }
    }
  }
}
```

## <a name="/get/api/applications/id"></a> GET /api/applications/[id]

Return application with matching id.

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" https://indexdb.whitealbum.dk/api/application/100
```

###### Response

```json
{  
   "id":1,
   "display_name":"Illustreret videnskab",
   "name":"IllustreretVidenskab",
   "site_code":"ilvid",
   "app_code":"cd_ark",
   "locale":"",
   "last_activity":"2015-07-13 10:01:09",
   "created_at":"2015-07-10 13:51:02",
   "updated_at":"2015-07-13 10:01:09",
   "roles":[  
      "application_index",
      "application_show",
      "content_destroy",
      "content_index",
      "content_show",
      "content_store",
      "content_update",
      "contenttype_index",
      "contenttype_show",
      "translate_create"
   ]
}
```

### PHP

###### Request

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/application/100');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
        
$response = json_decode(curl_exec($ch));
```

###### Response

```php
object(stdClass)#17 (10) {
  ["id"]=>
  int(1)
  ["display_name"]=>
  string(21) "Illustreret videnskab"
  ["name"]=>
  string(20) "IllustreretVidenskab"
  ["site_code"]=>
  string(5) "ilvid"
  ["app_code"]=>
  string(6) "cd_ark"
  ["locale"]=>
  string(0) ""
  ["last_activity"]=>
  string(19) "2015-07-13 10:08:37"
  ["created_at"]=>
  string(19) "2015-07-10 13:51:02"
  ["updated_at"]=>
  string(19) "2015-07-13 10:08:37"
  ["roles"]=>
  array(10) {
    [0]=>
    string(17) "application_index"
    [1]=>
    string(16) "application_show"
    [2]=>
    string(15) "content_destroy"
    [3]=>
    string(13) "content_index"
    [4]=>
    string(12) "content_show"
    [5]=>
    string(13) "content_store"
    [6]=>
    string(14) "content_update"
    [7]=>
    string(17) "contenttype_index"
    [8]=>
    string(16) "contenttype_show"
    [9]=>
    string(16) "translate_create"
  }
}
```