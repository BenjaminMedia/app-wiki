# Services

The API follows a RESTful pattern. The following table shows a CRUD example for
content.

|Path|Description|
|---|---|
|[/api/v1/content](service-content.md)|Service for storing content in Elasticsearch|
|[/api/v1/contenttype](service-contenttype.md)|Retrieve information about contenttypes available for use in the Content-service|
|[/api/v1/auth](service-auth.md)|Authentication service|
|[/api/v1/application](service-application.md)|Retrieve information about apps|
|[/api/v1/brandcode](service-brandcode.md)|Retrieve all available brand codes|
|[/api/v1/appcode](service-appcode.md)|Retrieve all available brand codes|
|[/api/v1/combination](service-combination.md)|Retrieve all available app brand code combinations that you are allowed to create content with|

## Notes

The API uses a RESTFUL api. In order to simulate method types like "PUT" and "DELETE" it's important that you remember to add an extra field named "_method" with the given request-type every time you call the API.
