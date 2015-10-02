## Overview
This section contains a walkthrough of the parameters supported by the API for filtering and querying items.

## Testing and debugging
You can use our developer console for testing and debugging queries to the API. 

For more information on how to use the developer console, please click here:
https://github.com/BenjaminMedia/bonnier-index-db/wiki/Administration#developer_console

## Parameters

|Name|Description|
|---|---|
|[brand_code](#parameter_brand_code)|Returns result that matches specified brand code|
|[app_code](#parameter_app_code)|Returns result that matches specified app code|
|[filter](#parameter_filter)|Filter results by given field and value|
|[meta](#parameter_meta)|Filter meta items by given value|
|[q](#parameter_q)|Matches everything|
|[sort](#parameter_sort)|Sort by field|
|[order](#parameter_order)|Order results ascending or descending|
|[skip](#parameter_skip)|Skip the entered amount of rows (useful for paging)|
|[limit](#parameter_limit)|Limits the number of rows returned in the result.|
|[dsl](#parameter_dsl)|Advanced Elasticsearch DSL-querying|

-

### <a name="parameter_brand_code"></a> brand_code
Returns result that matches specified brand code. 
String that describes the brand ownership of the content, Must match a value returned by the /api/v1/brandcode service. When creating content you must provide both a brand_code and a app_code, Your api credentials gives you access to specific combinations of app_codes and brand_codes, these can be fetched from the /api/v1/combination api.

For multiple matches, please separate the value with ",".

###### Example
brand_code=kom

brand_code=kom,dif

-

### <a name="parameter_app_code"></a> app_code
Returns result that matches specified app code. 
String that describes the app ownership of the content, Must match a value returned by the /api/v1/appcode service. When creating content you must provide both a app_code and a brand_code, Your api credentials gives you access to specific combinations of app_codes and brand_codes, these can be fetched from the /api/v1/combination api.

For multiple matches, please separate the value with ",".

###### Example
app_code=fordelszonen

app_code=fordelszonen,arkiv

-

### <a name="parameter_filter"></a> filter
Filter results by given value. 

For multiple matches, please separate the value with ",".

###### Example
content_type=page

content_type=page,article

-

### <a name="parameter_meta"></a> meta
Filter meta items by given value. 

For multiple matches, please separate the value with ",".

###### Example
meta=product.color:blue

content_type=product.color:blue,product.color:red

-

### <a name="parameter_q"></a> q
Returns every field that has value provided in q.

###### Example
q=horses

-

### <a name="parameter_sort"></a> sort
Sort by field

###### Example
sort=created_date

-

### <a name="parameter_order"></a> order
Order results ascending or descending

###### Values
asc
desc

###### Default
desc

###### Example
order=asc

-

### <a name="parameter_skip"></a> skip
Skips the entered amount of rows in the result (useful for paging).

If this parameter is missing, empty or null - the service will not skip any rows.

###### Values
integer
null

###### Default
null

###### Example
skip=10

-

### <a name="parameter_limit"></a> limit
Limits the number of rows returned in the result.

If this parameter is missing, empty or null - the service will return all rows in the result.

###### Values
integer
null

###### Default
null

###### Example
limit=10

-

### <a name="parameter_dsl"></a> dsl
Use advanced ElasticSearch queries known as DSL. This is useful for creating advanced queries, weighing fields or sorting on multiple values.

For more information, please refer to the Elasticsearch documentation on DSL here:
https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl.html

###### Example
dsl={ "match" : { "description" : "Hello world" } }