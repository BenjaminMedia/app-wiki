## Overview
This section contains a walkthrough of the parameters supported by the API for filtering and querying items.

## Testing and debugging
You can use our developer console for testing and debugging queries to the API. 

For more information on how to use the developer console, please click here:
https://github.com/BenjaminMedia/bonnier-index-db/wiki/Administration#developer_console

## Parameters

|Name|Description|
|---|---|
|[site_code](#parameter_site_code)|Returns result that matches specified site code|
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

### <a name="parameter_site_code"></a> site_code
Returns result that matches specified site code. 

For multiple matches, please seperate the value with ",".

###### Example
site_code=cd_ark

site_code=ifo,ilvid

-

### <a name="parameter_app_code"></a> app_code
Returns result that matches specified app code. 

For multiple matches, please seperate the value with ",".

###### Example
app_code=ifo

app_code=ifo,ilvid

-

### <a name="parameter_filter"></a> filter
Filter results by given value. 

For multiple matches, please seperate the value with ",".

###### Example
content_type=page

content_type=page,article

-

### <a name="parameter_meta"></a> meta
Filter meta items by given value. 

For multiple matches, please seperate the value with ",".

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
order=asc

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