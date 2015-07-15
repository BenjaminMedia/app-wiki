# Services

The API follows a RESTful pattern. The following table shows a CRUD example for
content.

|Path|Description|
|---|---|
|[/api/content](https://github.com/BenjaminMedia/app-wiki/blob/master/bonnier-index-db.wiki/service-content.md)|Service for storing content in Elasticsearch|
|[/api/contenttype](https://github.com/BenjaminMedia/app-wiki/blob/master/bonnier-index-db.wiki/service-contenttype.md)|Retrieve information about contenttypes available for use in the Content-service|
|[/api/auth](https://github.com/BenjaminMedia/app-wiki/blob/master/bonnier-index-db.wiki/service-auth.md)|Authentication service|
|[/api/application](https://github.com/BenjaminMedia/app-wiki/blob/master/bonnier-index-db.wiki/service-application.md)|Retrieve information about apps|

## Notes

The API uses a RESTFUL api. In order to simulate method types like "PUT" and "DELETE" it's important that you remember to add an extra field named "_method" with the given request-type every time you call the API.
