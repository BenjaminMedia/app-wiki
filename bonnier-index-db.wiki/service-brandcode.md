# api/v1/brandcode

Service for retrieving all available brand codes that can be used for filtering content by using the brand_code parameter. You must use that value of the brand codes when using the brand_code filter. Multilple values can be separated by ,

|Action|Path|Example|Description|
|---|---|---|---|
|GET|[/api/v1/brandcode/](#/get/api/contenttype)|/api/v1/brandcode|Returns a list of all brand codes.|

## <a name="/get/api/brandcode"></a> GET /api/v1/brandcode

Returns a list of all brand codes.

### CURL

###### Request

```
curl -H "Auth-Secret: [SECRET]" https://indexdb.whitealbum.dk/api/brandcode
```

###### Response

```json
{
	max: 3,
	rows: [
		{
			name: "komputer",
			value: "kom"
		},
		{
			name: "digitalfoto",
			value: "dif"
		},
		{
			name: "illustreret videnskab",
			value: "ill"
		}
	]
}
```

### PHP

###### Request

```php
$ch = curl_init('https://indexdb.whitealbum.dk/api/brandcode');

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
          'name' => string 'komputer' (length=8)
          'value' => string 'kom' (length=3)
      1 => 
        array (size=2)
          'name' => string 'digitalfoto' (length=11)
          'value' => string 'dif' (length=3)
      2 => 
        array (size=2)
          'name' => string 'illustreret videnskab' (length=21)
          'value' => string 'ill' (length=3)
```

