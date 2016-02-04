##IndexSearch V.2 Documentation

Version 2 of the IndexSearch has taken a completely different approach in how we provide you with the extensive search functionality. 

Instead of having a simplified API, that abstracts logic away from the behind driving motor (ElasticSearch), we now give you more access and control by allowing you to parse ElasticSearch queries directly through our API. 

This provies you with an increase in flexibility but comes at the cost of extended complexity; since you now have to understand how to query ElasticSearch. However this is an abstraction that we think is acceptable due to ElasticSearch having a considerably more documentated and community driven understanding of their API than we could possibly replicate in a wrapper.


# Table of Contents
  * [Creating Content](#create-content)
  * [The Meta Object](#meta-object)
  * [Update Single Content](#update-single)
  * [Bulk Content](#bulk-content)
  * [Query Examples] (#query-examples)
  	* [Additional Query Examples] (#additional-query-examples)
  		* [Pagination] (#query-example-pagination)
  		* [Sorting] (#query-example-sorting)
  		* [Boosting] (#query-example-boosting)
  		* [Aggregation] (#query-example-aggregation)
  		* [Search Request Fields] (#query-example-fields)
  		* [And, Or, Not] (#query-example-fields)

  
##Creating content <a id="create-content"></a>

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
   
   `content_type = [string|'article'|'car']`
   
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
	   "locale":"da-DK",
	   "app_code":"fordelszonen",
	   "brand_code":"kom",
	   "content_type":"article",
	   "active":true,
	   "title":"en awesome title",
	   "title_teaser":"en seo friendly teaser title",
	   "description":"en awesome beskrivelse",
	   "description_teaser":"en seo friendly teaser description",
	   "url":"http://bla.com/haha",
	   "image":"http://bla.com/haha.png",
	   "categories":[
	      "Software",
	      "Computer",
	      "Objektiver"
	   ],
	   "tags":[
	      "Kvalitet",
	      "Seje",
	      "Billige"
	   ],
	   "meta":{
	      "test":[
	         "software med mere",
	         "styresystemer",
	         "seje objektiver"
	      ],
	      "test_integer":1,
	      "test_boolean":true,
	      "test_long":2.1,
	      "test_float":2.1,
	      "test_double":2.1,
	      "test_byte":1,
	      "test_date":"2016-02-24",
	      "test_object":{
	         "hest":"test"
	      },
	      "test1_object":[
	         {
	            "hest":"test"
	         },
	         {
	            "hest":"test1"
	         }
	      ],
	      "test_ip":"127.0.0.1",
	      "test2_object":{
	         "text":"test text",
	         "test_geo_point":{
	            "lat":41.12,
	            "lon":-71.34
	         }
	      },
	      "test_geo_point":"41.12,-71.34"
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
  
##The Meta object <a id="meta-object"></a>

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

##Updating single piece of content <a id="update-single"></a>

Updating is exactly the same as creating except we expect an `id` to be appended to the end of the url

* **URL**

  http://staging-indexdb.whitealbum.dk/api/v2/teaser/<insert-id>

* **Method:**

   `PUT`

   **Required:** 
 	
 	`locale = [string|'da_dk'|'sv_se'|'nb_no'|'fi_fi'|'en_gb']`

   `content_type = [string|'article'|'car'|'review']`
   
##Bulking content <a id="bulk-content"></a>
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
	   {
	      "locale":"da-DK",
	      "app_code":"fordelszonen",
	      "brand_code":"kom",
	      "content_type":"article",
	      "active":true,
	      "title":"en awesome test titeesel",
	      "description":"en endnu mere awesome beskrivelse",
	      "url":"http://bla.com/haha",
	      "image":"http://bla.com/haha.png",
	      "categories":[
	         "Software",
	         "Computer",
	         "Objektiver"
	      ],
	      "tags":[
	         "Kvalitet",
	         "Seje",
	         "Billige"
	      ],
	      "meta":{
	         "test":[
	            "software med mere",
	            "styresystemer",
	            "seje objektiver"
	         ],
	         "test_integer":1,
	         "test_boolean":true,
	         "test_long":2.1,
	         "test_float":2.1,
	         "test_double":2.1,
	         "test_byte":1,
	         "test_date":"2016-02-24",
	         "test_object":{
	            "hest":"test"
	         },
	         "test1_object":[
	            {
	               "hest":"test"
	            },
	            {
	               "hest":"test1"
	            }
	         ],
	         "test_ip":"127.0.0.1",
	         "test2_object":{
	            "text":"test text",
	            "test_geo_point":{
	               "lat":41.12,
	               "lon":-71.34
	            }
	         },
	         "test_geo_point":"41.12,-71.34"
	      }
	   },
	   {
	      "id":"BGJplG9TpBYEBTqOPVcE",
	      "locale":"da-DK",
	      "app_code":"fordelszonen",
	      "brand_code":"kom",
	      "content_type":"article",
	      "active":true,
	      "title":"en awesome test titeesel",
	      "description":"en endnu mere awesome beskrivelse",
	      "url":"http://bla.com/haha",
	      "image":"http://bla.com/haha.png",
	      "categories":[
	         "Software",
	         "Computer",
	         "Objektiver"
	      ],
	      "tags":[
	         "Kvalitet",
	         "Seje",
	         "Billige"
	      ],
	      "meta":{
	         "test":[
	            "software med mere",
	            "styresystemer",
	            "seje objektiver"
	         ],
	         "test_integer":1,
	         "test_boolean":true,
	         "test_long":2.1,
	         "test_float":2.1,
	         "test_double":2.1,
	         "test_byte":1,
	         "test_date":"2016-02-24",
	         "test_object":{
	            "hest":"test"
	         },
	         "test1_object":[
	            {
	               "hest":"test"
	            },
	            {
	               "hest":"test1"
	            }
	         ],
	         "test_ip":"127.0.0.1",
	         "test2_object":{
	            "text":"test text",
	            "test_geo_point":{
	               "lat":41.12,
	               "lon":-71.34
	            }
	         },
	         "test_geo_point":"41.12,-71.34"
	      }
	   }
	]
	```

* **Success Response:**
  

  * **Code:** 200 <br />
    **Content:** 
    
    ``` javacript 
    [
    	{"id" : "AVJplG9TpBYEBTqOPVcE", "status": 201},
    	{"id" : "BGJplG9TpBYEBTqOPVcE", "status": 200}
    ]
    ``` 
	Status `201` means content was created, `200` means it updated existing content
	
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

	We suggest you don't bulk more than 32 MB worth of data at a time as this may impact results and perfomance; also you should set a high timeout value on your request when bulking, since creating/updating a lot of data is slow by nature. 
	
##Query example <a id="query-example"></a>
Querying for data is considerably different from IS V1. In V2 you are now able to parse an ElasticSearch query to our API and have it ported directly into ElasticSearch. This will be the primary way of querying for data.

This also means that you can use all the existing examples and documentation provided by ElasticSearch here [ElasticSearch Query] (https://www.elastic.co/guide/en/elasticsearch/reference/2.1/query-dsl.html).

For starters we suggest looking at the example below, and you can always contact us with questions or to help build any query functionality.

* **URL**

	http://staging-indexdb.whitealbum.dk/api/v2/teaser/_search

* **Method:** `POST`

* **Data Params**

  	**Required:**
 
	`locale = [string|'da_dk'|'sv_se'|'nb_no'|'fi_fi'|'en_gb'`]
	
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
	            "must":{
	               "multi_match":{
	                  "query":"moti",
	                  "fields":[
	                     "title.*",
	                     "description.*",
	                     "categories.*",
	                     "tags.*"
	                  ],
	                  "type":"most_fields"
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
	               }
	            ]
	         }
	      }
	   }
	}
	```


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    
	``` javascript 
	{
	   "total":3,
	   "max_score":0,
	   "hits":[
	      {
	         "app_code":"kom",
	         "brand_code":"fordelszonen",
	         "title":"Simple Motions 2"
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
	   "status":400,
	   "messages":{
	      "root_cause":[
	         {
	            "type":"query_parsing_exception",
	            "reason":"No query registered for [fs]",
	            "index":"content_da_dk",
	            "line":1,
	            "col":20
	         }
	      ],
	      "type":"search_phase_execution_exception",
	      "reason":"all shards failed",
	      "phase":"query",
	      "grouped":true,
	      "failed_shards":[
	         {
	            "shard":0,
	            "index":"content_da_dk",
	            "node":"JUWvVMQNRDqd42_Svxxe7Q",
	            "reason":{
	               "type":"query_parsing_exception",
	               "reason":"No query registered for [fs]",
	               "index":"content_da_dk",
	               "line":1,
	               "col":20
	            }
	         }
	      ]
	   }
	}
	```
* **Notes:**

Please be adviced that when searching for data with an impartial string you can only get results when searching within the `title.*`, `description.*`, `tags.*` and `categories.*`. Doing full-text search in other then the mentioned fields will require an exact match of the exact string parsed. Meaning "Sea" will not match "I am searching", but will match "I am under the sea". 

For title, description, tags and categories, it is also required that when doing fulltext search you append the field with `.*` to let the API know you are doing a fulltext search rather then an exact value query. This functionality is limited to the before specified fields only. 

### Additional Query Examples: <a id="additional-query-example"></a>
Below is a couple of examples on queries that will often be used.

####Pagination: <a id="query-example-pagination"></a>
Below query will fetch 50 items, starting from number 100, when specified app and brand code values.

```
{
   "locale":"da_dk",
   "body":{
      "size":50,
      "from":100,
      "query":{
         "bool":{
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
               }
            ]
         }
      }
   }
}
```

####[Sorting](https://www.elastic.co/guide/en/elasticsearch/reference/1.4/search-request-sort.html): <a id="query-example-sorting"></a>
Below query will fetch 50 items, starting from number 100, when specified app and brand code values.

```
{
   "locale":"da_dk",
   "body":{
	   "sort":[
	      {
	         "title": { "order":"asc" }
	      }
	   ],
      "size":50,
      "from":100,
      "query":{
         "bool":{
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
               }
            ]
         }
      }
   }
}
``` 

####[Boosting](https://www.elastic.co/guide/en/elasticsearch/reference/2.1/query-dsl-query-string-query.html#_boosting): <a id="query-example-boosting"></a>
Below query will search the content for moti and boost the "ranking" of those results which has moti in their title by 3 (notice: `"title.*^3"`), description by 2 ("description.*^2") and the rest by one.

Meaning a if all of them contains the "moti" query, the title will give "3 points", description "2 points" and the rest "1 point". The data is then returned based on the average scoring of each document.

The default boost value is 1, but can be any positive floating point number. Boosts between 0 and 1 reduce relevance.

```
{
   "locale":"da_dk",
   "body":{
      "size":5,
      "query":{
         "bool":{
            "must":{
               "multi_match":{
                  "query":"moti",
                  "fields":[
                     "title.*^3",
                     "description.*^2",
                     "categories.*",
                     "tags.*"
                  ],
                  "type":"most_fields"
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
               }
            ]
         }
      }
   }
}
``` 
####[Aggregations](https://www.elastic.co/guide/en/elasticsearch/reference/2.1/search-aggregations.html): <a id="query-example-aggregations"></a>
Aggregations is one of the features that ElasticSearch allows us to do very nicely.

Lets imagine we are creating an application that shows a list of cars. We want to be able to filter this list of cars by brand, model and series. If we pick a value in the brand dropdown, say brand A, then we want the other filters to adjust accordingly, so that the other dropdowns do not show values in which no car with brand A exists.

This can be done with the following query

```
{
   "locale":"da_dk",
   "body":{
      "query":{
         "bool":{
            "filter":[
               {
                  "term":{
                     "brand_code":"car"
                  }
               },
               {
                  "term":{
                     "app_code":"carapp"
                  }
               }
            ]
         }
      },
      "aggregations":{
         "brands":{
            "terms":{
               "field":"meta.brand"
            }
         },
         "models":{
            "terms":{
               "field":"meta.model"
            }
         },
         "series":{
            "terms":{
               "field":"meta.series"
            }
         }
      }
   }
}
``` 

Returns the following response

```
{
  "total": 1,
  "max_score": 9.260918,
  "hits": [
  		...
  ],
  "aggregations": {
    "brands": [
      {
        "key": "BMW",
        "doc_count": 7
      },
      {
        "key": "Ferrari",
        "doc_count": 15
      },
      {
        "key": "Audi",
        "doc_count": 23
      }
    ],
    "models": [
      {
        "key": "A3",
        "doc_count": 7
      },
      {
        "key": "X6",
        "doc_count": 9
      }
    ],
    "series": [
      {
        "key": "Series 2",
        "doc_count": 1
      }
    ]
  }
}
```

####[Search Request Fields](https://www.elastic.co/guide/en/elasticsearch/reference/2.1/search-request-fields.html): <a id="query-example-fields"></a>
If you know you are only going to be using certain fields for the document you can ask to only have those returned. This can be done with the following query:

```
{
   "locale":"da_dk",
   "body":{
      "fields" : ["title", "description", "image", "url"],
      "query":{
         "bool":{
            "filter":[
               {
                  "term":{
                     "brand_code":"car"
                  }
               },
               {
                  "term":{
                     "app_code":"carapp"
                  }
               }
            ]
         }
      }
   }
}
``` 

Returns the following response

```
{
  "total": 2,
  "max_score": 0,
  "hits": [
    {
      "description": "Some description",
      "image": "http://image.com/image.jpg",
      "title": "Some Title",
      "url": "http://some.url/here",
      "id": "AVKDCR3M3p6shXKj93vw",
      "score": 0
    },
    {
      "description": "Some description",
      "image": "http://image.com/image.jpg",
      "title": "Some Title",
      "url": "http://some.url/here",
      "id": "FAKDCR3M3p6shXKj93vw",
      "score": 0
    }
  ]
}
``` 

####[Searching with And & Or](https://www.elastic.co/guide/en/elasticsearch/reference/current/compound-queries.html): <a id="query-example-and-or"></a>
Given we want to find 'Cameras' and 'Printers' with the brand 'Canon' or 'Sony'.

A query could be built like below that will query bool (true or false) on all documents and based on whether they have tags [Canon or Sony] AND categories [Camera or Printers].

```
{
   "locale":"da_dk",
   "body":{
      "size":"10",
      "from":0,
      "query":{
         "bool":{
            "must":{
               "and":[
                  {
                     "or":[
                        {
                           "match":{
                              "tags":"Canon"
                           }
                        },
                        {
                           "match":{
                              "tags":"Sony"
                           }
                        }
                     ]
                  },
                  {
                     "or":[
                        {
                           "match":{
                              "categories":"Kamera"
                           }
                        },
                        {
                           "match":{
                              "categories":"Printere"
                           }
                        }
                     ]
                  }
               ]
            },
            "filter":[
               {
                  "term":{
                     "app_code":"productsearch"
                  }
               }
            ]
         }
      }
   }
}
``` 

Returns the following response

```
{
  "total": 2,
  "max_score": 0,
  "hits": [
    {
      "description": "Some description",
      "image": "http://image.com/image.jpg",
      "title": "Some Title",
      "url": "http://some.url/here",
      "id": "AVKDCR3M3p6shXKj93vw",
      "score": 0
    },
    {
      "description": "Some description",
      "image": "http://image.com/image.jpg",
      "title": "Some Title",
      "url": "http://some.url/here",
      "id": "FAKDCR3M3p6shXKj93vw",
      "score": 0
    }
  ]
}
``` 


