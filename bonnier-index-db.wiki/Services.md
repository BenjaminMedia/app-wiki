# Services

The API follows a RESTful pattern. The following table shows a CRUD example for
content.

|Path|Description|
|---|---|
|[/api/content](https://github.com/BenjaminMedia/bonnier-index-db/wiki/service-content)|Service for storing content in Elasticsearch|
|[/api/contenttype](https://github.com/BenjaminMedia/bonnier-index-db/wiki/service-contenttype)|Retrieve information about contenttypes available for use in the Content-service|
|[/api/auth](https://github.com/BenjaminMedia/bonnier-index-db/wiki/service-auth)|Authentication service|
|[/api/application](https://github.com/BenjaminMedia/bonnier-index-db/wiki/service-application)|Retrieve information about apps|

## Notes

The API uses a RESTFUL api. In order to simulate method types like "PUT" and "DELETE" it's important that you remember to add an extra field named "_method" with the given request-type every time you call the API.