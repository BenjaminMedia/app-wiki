## Overview
This section contains a walkthrough of the parameters supported by the API for filtering and querying items.

## Parameters

|Name|Description|
|---|---|
|[sort](#parameter_sort)|Sort by field|
|[order](#parameter_order)|Order results ascending or descending|
|[locale](#parameter_locale)|Filter the results to only returns items with matching locale(s).|
|[app_id](#parameter_app_id)|Filter the results to only returns items with matching application id.|
|[state](#parameter_state)|Filter results by matching state|
|[q](#parameter_q)|Filters results where meta-data contains the specified value|
|[skip](#parameter_skip)|Skips the entered amount of rows in the result (useful for paging).|
|[limit](#parameter_limit)|Limits the number of rows returned in the result.|
|[original](#original)|Filter results by matching id of original translation|
|[filter_original](#filter_original)|Filter the results to only return original translations without revisions|

-

### <a name="parameter_sort"></a> sort
Sort by field

###### Default
desc
###### Values
asc
desc

###### Example
order=desc
order=asc

-

### <a name="parameter_order"></a> order
Order results ascending or descending

###### Default
desc

###### Values
asc
desc

###### Example
order=desc
order=asc

-

### <a name="parameter_locale"></a> locale
Filter the results to only returns items with matching locale

Value must contain valid and supported locale.

For multiple matches, please separate the value with ",".

###### Values
string

###### Example
locale=da_DK

locale=da\_DK,en_GB

-

### <a name="parameter_app_id"></a> q
Filter results by matching application id.

###### Values
int
null

###### Example
app_id=1

-

### <a name="parameter_state"></a> q
Filter results by matching state

Value must contain valid and supported state.

For multiple matches, please separate the value with ",".

###### Values
string
null

###### Example
state=translated,waiting

state=translated

-

### <a name="parameter_q"></a> state_id
Filters results where meta-data contains the specified value

###### Values
string

###### Example
q=myQuery

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
30

###### Example
limit=10

### <a name="original"></a> original
Filter results by matching id of original translation

###### Values
string
null

###### Default
null

###### Example
orignal=55b8f5b2214f48da0900421f


### <a name="filter_original"></a> filter_original
Filter the results to not return revisions but only original translations

###### Values
boolean
null

###### Default
false

###### Example
filter_original=true

