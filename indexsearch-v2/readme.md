##IndexSearch V.2 Documentation

Version 2 of the IndexSearch has taken a completely different approach in how we provide you with the extensive search functionality. 

Instead of wrapping everything in a simple API, that abstracts logic away from the behind driving motor (ElasticSearch), we now give you more access and control. Increased flexibility that comes at the cost of extended complexity; since you now have to understand how to query ElasticSearch. An abstraction we think is acceptable since ElasticSearch is considerably more documentated and community driven then any abstractional API we can deliver.

##Creating content

* **URL**

  http://staging-indexdb.whitealbum.dk/api/v2/teaser

* **Method:**

   `POST`

   **Required:**
 
 	`app_code = [string]`
 	
 	`brand_code = [string]`
 	
 	`locale = [string|'da_dk'|'sv_se'|'nb_no'|'fi_fi']`
 	
 	`title = [string]`
 	
 	`description = [string]`
 	
 	`image = [string|url]`
   
   `content_type = [string|'article'|'car'|'review']`
   
   `url = [string|url]`
   
   `active = [boolean]`

   **Optional:**
 
   `categories = [array[strings]]`
   
   `tags = [array[string]]`
   
   `body = [string]`
   
   `meta = [object]`

* **Example Data**

  ```javascript
  {
    	"locale": "da-DK",
    	"app_code": "fordelszonen",
    	"brand_code": "kom",
    	"content_type": "article",
    	"active" : true,
    	"title": "en awesome test titeesel",
    	"description": "en endnu mere awesome beskrivelse",
    	"url": "http://bla.com/haha",
    	"image": "http://bla.com/haha.png",
    	"categories": [
    		'Software', 'Computer', 'Objektiver'
    	],
    	"tags": [
    		'Kvalitet', 'Seje', 'Billige'
    	],
    	"meta" : {
    	    "test": [
    	    	"software med mere", 
    	    	"styresystemer", 
    	    	"seje objektiver"
    	    ],
    	    "test_integer" : 1,
    	    "test_boolean" : true,
    	    "test_long" : 2.1,
    	    "test_float" : 2.1,
    	    "test_double" : 2.1,
    	    "test_byte" : 1,
    	    "test_date" : "2016-02-24",
    	    "test_object" : {"hest": "test"},
    	    "test1_object" : [{"hest": "test"}, {"hest": "test1"}],
    	    "test_ip" : "127.0.0.1",
    	    "test2_object" : {
    	        "text" : "test text",
    	        "test_geo_point" : {
    	            "lat": 41.12,
    	            "lon": -71.34
    	        }
    	    },
    	    "test_geo_point" :  "41.12,-71.34"
    	    
    	}
    }
    ```

* **Success Response:**
  
  <_What should the status code be on success and is there any returned data? This is useful when people need to to know what their callbacks should expect!_>

  * **Code:** 200 <br />
    **Content:** `{ id : 12 }`
 
* **Error Response:**

  <_Most endpoints will have many ways they can fail. From unauthorized access, to wrongful parameters etc. All of those should be liste d here. It might seem repetitive, but it helps prevent assumptions from being made where they should be._>

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** `{ error : "Log in" }`

  OR

  * **Code:** 422 UNPROCESSABLE ENTRY <br />
    **Content:** `{ error : "Email Invalid" }`

* **Sample Call:**

``` php

$clientSetup = [
    'base_uri' => 'https://staging-indexdb.whitealbum.dk/api/v2/', // the enviroment yo are calling either staging or production
    'curl' => [
        CURLOPT_SSL_VERIFYHOST => 0, // needed to ignore ssl verification
        CURLOPT_SSL_VERIFYPEER => 0 // needed to ignore ssl verification
    ],
    'auth' => [
        'user', // insert your api user name
        'key' // insert your api key
    ],
];

$client new \GuzzleHttp\Client($clientSetup);

$createContent = [
    'locale' => 'da_dk',
    'app_code' => 'fordelszonen',
    'brand_code' => 'kom',
    'active' => true,
    'content_type' => 'article',
    'title' => 'En flot test hest',
    'description' => 'En flot description',
    'url' => 'http://google.dk/test',
    'image' => 'http://google.dk/image',
    'categories' => [
    		'Software', 'Computer', 'Objektiver'
    ],
    'tags' => [
    		'Kvalitet', 'Seje', 'Billige'
    ],
    'meta' => [ 	
    	'test' => [
	    	'software med mere', 
	    	'styresystemer', 
	    	'seje objektiver'
	    ],
		'test_integer' => 1,
	    'test_boolean' => true,
	    'test_long' => 2.1,
	    'test_float' => 2.1,
	    'test_double' => 2.1,
	    'test_byte' => 1,
	    'test_date' => '2016-02-24',
	    'test_object' => ['hest'=> 'test'],
	    'test1_object' => [['hest'=> 'test'], ['hest'=> 'test1']],
	    'test_ip' => '127.0.0.1',
	    'test2_object' => [
	        'text' => 'test text',
	        'test_geo_point' => [
	            'lat'=> 41.12,
	            'lon'=> -71.34
	        ]
	    ],
	    'test_geo_point' =>  '41.12,-71.34'
	]
];

try {
    $request = $client->request('post', 'teaser');
    
} catch (\GuzzleHttp\Exception\RequestException $e) {

    $errorCode = json_decode($e->getCode()); // for example you will get 406 when providing invalid input
    $errorMsg = json_decode($e->getMessage(), true); // the error message will always be json_encoded therefore you should decode it
}

$response = $client->request('post', 'teaser', ['json' => $createContent]);

if ($response->getStatusCode() === 201) { // should always return 201 on create 
    $returnedContent = json_decode($response->getBody()->getContents(), true); // We should get the content the same content as posted, but now with a id present
    
       $id = $returnedContent['id']; // you should save this in your database as it is needed for updating|deleting the content
}    

```

  <_Just a sample call to your endpoint in a runnable format ($.ajax call or a curl request) - this makes life easier and more predictable._> 

* **Notes:**

  <_This is where all uncertainties, commentary, discussion etc. can go. I recommend timestamping and identifying oneself when leaving comments here._> 
  
###  
  
  
##The Meta object
The meta object is a special part of the content that allows you to define your own keys|names for content. Also you are allowed to put as many key:value combinations in it as you like. But you should only add the values that you actually need and not just throw your whole data model in there.

Data in meta is by default stored and indexed as whole strings, therefore when searching on meta values you will only be able to match on complete values, ie: not partials.

If however you need to match on more advanced types of data, you can use the naming of your keys to control what format your data should be stored in. For example:

``` javascript
{
	"test_integer" : 1, 
	"test_boolean" : true,
	"test_long" : 2.1,
	"test_float" : 2.1,
	"test_double" : 2.1,
	"test_byte" : 1,
	"test_date" : "2016-02-24",
	"test_object" : {"hest": "test"}
	
}

```
By appending ```_integer``` to your meta key name, you tell the api that your want the data in the field to be stored as an integer. Likewise this syntax can be used for other types of data as seen in the example above. 

note ```_object``` is special and can be combined with the other types as seen in the example below
 
``` javascript
{
	"test2_object" : {
        "text" : "test text",
        "test_geo_point" : {
            "lat": 41.12,
            "lon": -71.34
        }
    }
}
```

##Updating single piece of content

Updating is exactly the same as creating except we expect an ``` id ``` to be appended to the end of the url

* **URL**

  http://staging-indexdb.whitealbum.dk/api/v2/teaser/[insert id]

* **Method:**

   `POST`

   **Required:** 
 	
 	`locale = [string|'da_dk'|'sv_se'|'nb_no'|'fi_fi']`

   `content_type = [string|'article'|'car'|'review']`
   
##Bulking content
Bulking is a functinality that allows you to create|update multiple sets of content in one api call. Bulking is considerably faster that creating a single record and should always be used over single record creation.

Note bulking uses exactly the same parameters as updating|creating content, with the exception that it expects an array of objects rather than a single object.

* **URL**

http://staging-indexdb.whitealbum.dk/api/v2/teaser/_bulk

* **Method:**

  `POST`

	**Required:**
 
   same as `create|update`

* **Data Params**

```javascript
[
  { // this content wil be created
	"locale": "da-DK",
	"app_code": "fordelszonen",
	"brand_code": "kom",
	"content_type": "article",
	"active" : true,
	"title": "en awesome test titeesel",
	"description": "en endnu mere awesome beskrivelse",
	"url": "http://bla.com/haha",
	"image": "http://bla.com/haha.png",
	"categories": [
		'Software', 'Computer', 'Objektiver'
	],
	"tags": [
		'Kvalitet', 'Seje', 'Billige'
	],
	"meta" : {
	    "test": [
	    	"software med mere", 
	    	"styresystemer", 
	    	"seje objektiver"
	    ],
	    "test_integer" : 1,
	    "test_boolean" : true,
	    "test_long" : 2.1,
	    "test_float" : 2.1,
	    "test_double" : 2.1,
	    "test_byte" : 1,
	    "test_date" : "2016-02-24",
	    "test_object" : {"hest": "test"},
	    "test1_object" : [{"hest": "test"}, {"hest": "test1"}],
	    "test_ip" : "127.0.0.1",
	    "test2_object" : {
	        "text" : "test text",
	        "test_geo_point" : {
	            "lat": 41.12,
	            "lon": -71.34
	        }
	    },
	    "test_geo_point" :  "41.12,-71.34"    
	}
  },
    {
    "id" : "AVJplG9TpBYEBTqOPVcE" // this content will be updated
	"locale": "da-DK",
	"app_code": "fordelszonen",
	"brand_code": "kom",
	"content_type": "article",
	"active" : true,
	"title": "en awesome test titeesel",
	"description": "en endnu mere awesome beskrivelse",
	"url": "http://bla.com/haha",
	"image": "http://bla.com/haha.png",
	"categories": [
		'Software', 'Computer', 'Objektiver'
	],
	"tags": [
		'Kvalitet', 'Seje', 'Billige'
	],
	"meta" : {
	    "test": [
	    	"software med mere", 
	    	"styresystemer", 
	    	"seje objektiver"
	    ],
	    "test_integer" : 1,
	    "test_boolean" : true,
	    "test_long" : 2.1,
	    "test_float" : 2.1,
	    "test_double" : 2.1,
	    "test_byte" : 1,
	    "test_date" : "2016-02-24",
	    "test_object" : {"hest": "test"},
	    "test1_object" : [{"hest": "test"}, {"hest": "test1"}],
	    "test_ip" : "127.0.0.1",
	    "test2_object" : {
	        "text" : "test text",
	        "test_geo_point" : {
	            "lat": 41.12,
	            "lon": -71.34
	        }
	    },
	    "test_geo_point" :  "41.12,-71.34"    
	}
  }
]
```

* **Success Response:**
  

  * **Code:** 200 <br />
    **Content:** 
    
    ``` javacript 
    [
    	{"id" : "BGJplG9TpBYEBTqOPVcE", "status": 200},
    	{"id" : "AVJplG9TpBYEBTqOPVcE", "status": 201}
    ]
    ``` 
	Status `200` means content was created, `201 means it updated existing content
* **Error Response:**

  <_Most endpoints will have many ways they can fail. From unauthorized access, to wrongful parameters etc. All of those should be liste d here. It might seem repetitive, but it helps prevent assumptions from being made where they should be._>

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** `{ error : "Log in" }`

  OR

  * **Code:** 406 INVALID INPUT <br />
    **Content:** `{ "messages" : [error messages], "input": [your input] }`
    
  OR
    
  * **Code:** 200 <br />
    **Content:** 
    
    ``` javacript 
    [
    	{"id" : "BGJplG9TpBYEBTqOPVcE", "status": 200},
    	{"id" : "AVJplG9TpBYEBTqOPVcE", "status": 400, error: "some error message"}
    ]
    ``` 

* **Notes:**

	We suggest you dont bulk more that 32 MB's worth of data as this may impact results and perfomance, also you should set a high timeout value on your request when bulking. 
	
##Query example

* **URL**

	http://staging-indexdb.whitealbum.dk/api/v2/teaser/_bulk

* **Method:** `POST`

* **Data Params**

   **Required:**
 
	`locale = [string|'da_dk'|'sv_se'|'nb_no'|'fi_fi']`
	`body = [object]`

   **body params:**
   
   The body contains standard elasticsearch query
 	[Query documentation](https://www.elastic.co/guide/en/elasticsearch/reference/2.1/query-dsl-bool-query.html)
 	
 	**example query:**
 	
 	``` javascript
 
 {
   "locale":"da_dk",
   "body":{
      "size":5,
      "query":{
         "bool":{
            "must": {
                "multi_match": {
                "query":    "moti",
                "fields": [ "title.*" ],
                "type":     "most_fields"
                }
            },
            "filter":[
                {
                   "term":{
                      "brand_code":"kom"
                   }
                },
                {
                   "term":{
                      "app_code":"fordelszonen"
                   }
                },
            ]
         }
      }
  } 
 ```


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    
	``` javascript 
	{
	  "total": 3,
	  "max_score": 0,
	  "hits": [
	  	{
	  		"app_code" : "kom",
	  		"brand_code" : "fordelszonen",
	  		"title": "Simple Motions 2"
	  		...
	  	}
	  ]
	}
	```

* **Notes:**
