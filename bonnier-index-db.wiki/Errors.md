# Overview
This list contains the custom errors that you can encounter when using the API in a wrong way along with a description on how to fix the error, if available. 

### Custom errors
|Code|Description|Possible fix|
|---|---|---|---|
|1|Missing required header parameter: "Auth-Secret"|Add the header "Auth-secret" that contains the secret for your application to the request.|
|2|The provided secret is not valid|Go to the API administration and check that the secret used in the API matches the secret for your application.|
|3|Missing required param(s): [param], [param]|The field [param] is missing. Please check that they have been added correctly to the query.|
|4|Incorrect [type] value for param [param]|The field [param] you are adding is a wrong type. Please change it so it uses the appropriate [type].|
|5|Missing required argument [argument] in url|You forgot to add an required argument to the url.|
|6|FATAL API Exception: invalid validation type|Validation type not yet implemented in the API. This is an internal error and cannot be fixed.|

### Other errors
The list below contains the a list of the error you might encounter when using the API. These errors are taken directly from Elasticsearch and only contains the most common errors. 

Please refer to the Elasticsearch documentation if you experience any error that is not defined in the list below or if the error-description provided by the API isn’t helpful enough:

https://www.elastic.co/guide/en/elasticsearch 

|Code|Description|
|---|---|---|---|
|400|Bad request|
|403|Forbidden|
|404|Not found|
|412|Precondition failed|
|500|Internal server error|
|503|Service unavailable|