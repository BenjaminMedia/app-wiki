# api/v1/appcode

Service for retrieving all available app codes that can be used for filtering content by using the app_code parameter. You must use that value of the app codes when using the app_code filter. Multilple values can be separated by ,

|Action|Path|Example|Description|
|---|---|---|---|
|GET|[/api/v1/appcode/](#/get/api/contenttype)|/api/v1/appcode|Returns a list of all app codes.|

## <a name="/get/api/appcode"></a> GET /api/v1/appcode

Returns a list of all app codes.

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" https://indexdb.whitealbum.dk/api/appcode
```

###### Response

```json
{
	max: 3,
	rows: [
		{
			name: "Fordelszonen",
			value: "fordelszonen"
		},
		{
			name: "Arkiv",
			value: "arkiv"
		},
		{
			name: "Route planner",
			value: "route_planner"
		}
	]
}
```


### PHP

###### Request

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/appcode');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Auth-Secret: [SECRET]'));
        
$response = json_decode(curl_exec($ch));
```

###### Response

```php
array (size=2)
  'max' => int 3
  'rows' => 
    array (size=3)
      0 => 
        array (size=2)
          'name' => string 'Fordelszonen' (length=12)
          'value' => string 'fordelszonen' (length=12)
      1 => 
        array (size=2)
          'name' => string 'Arkiv' (length=5)
          'value' => string 'arkiv' (length=5)
      2 => 
        array (size=2)
          'name' => string 'Route planner' (length=13)
          'value' => string 'route_planner' (length=13)
```

