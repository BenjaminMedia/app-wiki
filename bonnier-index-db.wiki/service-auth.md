# api/auth

Basic service for checking authentication and access upon a given application-role.

|Action|Path|Example|Description|
|---|---|---|---|
|GET|[/api/auth/[role]](#/get/api/auth/role)|/api/auth/translate_create|Checks if token has access to given role, creates the role if it doesn't exist.|

## <a name="/get/api/auth/role"></a> GET /api/auth/[role]
Checks if token has access to given role, creates the role if it doesn't exist.

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" http://bonnierindexdb.pecee.dk/api/auth/translate_create
```

###### Response

```json
{  
   "role":"translate_create",
   "created_at":"2015-07-13 09:26:37",
   "updated_at":"2015-07-13 09:26:37"
}
```

### PHP

###### Request

```php
$ch = curl_init('http://bonnierindexdb.pecee.dk/api/auth/translate_create');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
        
$response = json_decode(curl_exec($ch));
```

###### Response

```php
object(stdClass)#17 (4) {
  ["role"]=>
  string(16) "translate_create"
  ["created_at"]=>
  string(19) "2015-07-13 09:26:37"
  ["updated_at"]=>
  string(19) "2015-07-13 09:26:37"
  ["access"]=>
  bool(true)
}
```