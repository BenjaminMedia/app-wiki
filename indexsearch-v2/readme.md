##IndexSearch V.2 Documentation

Version 2 of the IndexSearch has taken a completely different approach in how we provide you with the extensive search functionality. 

Instead of having a simplified API, that abstracts logic away from the behind driving motor (ElasticSearch), we now give you more access and control by allowing you to parse ElasticSearch queries directly through our API. 

This provies you with an increase in flexibility but comes at the cost of extended complexity; since you now have to understand how to query ElasticSearch. However this is an abstraction that we think is acceptable due to ElasticSearch having a considerably more documentated and community driven understanding of their API, then we possibly can replicate through a wrapper.

##Creating content

* **URL**

  http://staging-indexdb.whitealbum.dk/api/v2/teaser

* **Method:**

   `POST`

   **Required:**
 
 	`app_code = [string]`
 	
 	`brand_code = [string]`
 	
 	`locale = [string|'da_dk'|'sv_se'|'nb_no'|'fi_fi'|'en_gb']`
 	
 	`title = [string]`
 	
 	`title_teaser = [string]`
 	
 	`description = [string]`
 	
 	`description_teaser = [string]`
 	
 	`image = [string|url]`
   
   `content_type = [string|'article'|'car'|'review']`
   
   `url = [string|url]`
   
   `active = [boolean]`

   **Optional:**
 
   `categories = [array[strings]]`
   
   `tags = [array[strings]]`
   
   `body = [string]`
   
   `meta = [object]`

* **Example JSON**

  ```javascript
  {
    	"locale": "da-DK",
    	"app_code": "fordelszonen",
    	"brand_code": "kom",
    	"content_type": "article",
    	"active" : true,
    	"title": "en awesome title",
    	"title_teaser": "en seo friendly teaser title",
    	"description": "en awesome beskrivelse",
    	"description_teaser": "en seo friendly teaser description"
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

  * **Code:** 200 <br />
    **Content:**
    Return the posted content + an id.
    
	    ```
	    { 
	    	"id" : AVJ9J5_V3p6shXKj93sr
	    	"locale": "da-DK",
	    	"app_code": "fordelszonen",
	    	"brand_code": "kom",
	    	"content_type": "article",
	    	...
	    }
	    ```
 
* **Error Response:**

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** 
    
	    ```
	    {
		    "status": 401,
		    "error": "You dont have the required permissions to <some action>"
	    }
	    ```

  OR

  * **Code:** 406 NOT ACCEPTABLE <br />
    **Content:**
        
	    ```
	    {
		    "status": 406,
		    "error":"JSON input error: quoted object property name expected"
	    }
	    ```
	    OR
	            
	    ```
	    {
		  "messages": {
		    "<some_field>": [
		      "<some_error> on <some_field>"
		    ]
		  },
		  "input": {
		  		...(the input data)...
		  }
		}
	    ```

* **Sample Call:**

	The sample code here is made using a [Guzzle](https://github.com/guzzle/guzzle "Guzzle") http-client, we strongly suggest using this client.
	
	``` php
	$clientSetup = [
	    'base_uri' => 'https://staging-indexdb.whitealbum.dk/api/v2/', // requested url
	    'curl' => [
	        CURLOPT_SSL_VERIFYHOST => 0, // needed to ignore ssl verification
	        CURLOPT_SSL_VERIFYPEER => 0 // needed to ignore ssl verification
	    ],
	    'auth' => [
	        '<user>', // your api user name
	        '<key>' // your api key
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
		// Fetch error code of input
	    $errorCode = json_decode($e->getCode());
	    // Fetch json_encoded message, so decode it
	    $errorMsg = json_decode($e->getResponse()->getBody()->getContents(), true);
	}
	
	$response = $client->request('post', 'teaser', ['json' => $createContent]);
	
	// Create should return 201 when successful
	if ($response->getStatusCode() === 201) {
		 // Returns input content but now with an id  
	    $returnedContent = json_decode($response->getBody()->getContents(), true); 
	    
	    // IMPORTANT
	    // Save this in your database as you will need it for updating|deleting content
	    $id = $returnedContent['id'];
	}    
	
	```
* **Notes:**

Notice that on creation we return the same content including an id. It is each individual (you) apps responsibility to keep track and store this id. The ID will not change and will be used for all future reference of that content.
  
##The Meta object

The meta object is a special part of the content that allows you to define your own key-names for content. Also you are allowed to put as many key:value combinations in it as you like. But you should only add the values that you actually need and not just throw your whole data model in there.

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

Updating is exactly the same as creating except we expect an `id` to be appended to the end of the url

* **URL**

  http://staging-indexdb.whitealbum.dk/api/v2/teaser/<insert-id>

* **Method:**

   `POST`

   **Required:** 
 	
 	`locale = [string|'da_dk'|'sv_se'|'nb_no'|'fi_fi'|'en_gb']`

   `content_type = [string|'article'|'car'|'review']`
   
##Bulking content
Bulking is a functinality that allows you to create|update multiple sets of content in a single api call. It is considerably faster then creating a single record and it should always be used over single record creation.

Note: bulking uses exactly the same parameters as updating|creating content, with the exception that it expects an array of objects rather than a single object.

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
    { // this content will be updated
    "id" : "AVJplG9TpBYEBTqOPVcE" 
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

	We suggest you dont bulk more than 32 MB worth of data at a time as this may impact results and perfomance; also you should set a high timeout value on your request when bulking, since creating/updating a lot of data is slow by nature. 
	
##Query example
Querying for data is considerably different from IS V1. In V2 you are now able to parse an ElasticSearch query to our API and have it ported directly into ElasticSearch. This will be the primary way of querying for data.

This also means that you can use all the existing examples and documentation provided by ElasticSearch here [ElasticSearch Query] (https://www.elastic.co/guide/en/elasticsearch/reference/2.1/query-dsl.html).

For starters we suggest looking at the example below, and you can always contact us with questions or to help build any query functionality.

* **URL**

	http://staging-indexdb.whitealbum.dk/api/v2/teaser/_bulk

* **Method:** `POST`

* **Data Params**

  	**Required:**
 
	`locale = [string|'da_dk'|'sv_se'|'nb_no'|'fi_fi']|'en_gb'`
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
	
* **Error Response:**

	Requesting with an incorrect query will return an error code 400. This error is generated by ElasticSearch and will return some information that might nessecarily not be useful for you, but potentially could help you in your search for the error.

  * **Code:** 400 Bad Request <br />
    **Content:** 
    
	``` javascript 
	{
  		"status": 400,
		  "messages": {
		    "root_cause": [
		      {
		        "type": "query_parsing_exception",
		        "reason": "No query registered for [fs]",
		        "index": "content_da_dk",
		        "line": 1,
		        "col": 20
		      }
		    ],
		    "type": "search_phase_execution_exception",
		    "reason": "all shards failed",
		    "phase": "query",
		    "grouped": true,
		    "failed_shards": [
		      {
		        "shard": 0,
		        "index": "content_da_dk",
		        "node": "JUWvVMQNRDqd42_Svxxe7Q",
		        "reason": {
		          "type": "query_parsing_exception",
		          "reason": "No query registered for [fs]",
		          "index": "content_da_dk",
		          "line": 1,
		          "col": 20
		        }
		      }
		    ]
		  }
		}
	}
	```

* **Notes:**
