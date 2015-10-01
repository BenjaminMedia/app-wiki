# api/v1/combination

Service for retrieving app brand code combinations that your credentials are allowed to create content with.

|Action|Path|Example|Description|
|---|---|---|---|
|GET|[/api/v1/combination/](#/get/api/contenttype)|/api/v1/combination|Returns a list of allowed combinations.|

## <a name="/get/api/combination"></a> GET /api/v1/combination

Returns a list of allowed combinations.

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" https://indexdb.whitealbum.dk/api/combination
```

###### Response

```json
{
	max: 3,
	rows: [
		{
			brand_code: {
				name: "digitalfoto",
				value: "dif"
			},
			app_code: {
				name: "Fordelszonen",
				value: "fordelszonen"
			}
		},
		{
			brand_code: {
				name: "illustreret videnskab",
				value: "ill"
			},
			app_code: {
				name: "Arkiv",
				value: "arkiv"
			}
		},
		{
			brand_code: {
				name: "komputer",
				value: "kom"
			},
			app_code: {
				name: "Fordelszonen",
				value: "fordelszonen"
			}
		}
	]
	
}
```

### PHP

###### Request

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/combination');

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
          'brand_code' => 
            array (size=2)
              ...
          'app_code' => 
            array (size=2)
              ...
      1 => 
        array (size=2)
          'brand_code' => 
            array (size=2)
              ...
          'app_code' => 
            array (size=2)
              ...
      2 => 
        array (size=2)
          'brand_code' => 
            array (size=2)
              ...
          'app_code' => 
            array (size=2)
              ...
```

