## Overview
The Search API is a basic way of getting data from our internal Elasticsearch service through a RESTFUL api. The search api authenticates the request and provides additional parameters for filtering, querying and sorting data - delivered from the Elasticsearch service.

The data-structure is provided as-is from Elasticsearch with the only exception of errors. Whenever an error occur two fields (error and errorCode) will be returned in the result.

Each request requires a valid access token (referenced as a “secret”) which is a unique identifier generated randomly when creating an applications through the API administration panel (see x.x). 

## Table of contents
- [Home](https://github.com/BenjaminMedia/app-wiki/blob/master/bonnier-index-db.wiki/Home.md)
- [Administration](https://github.com/BenjaminMedia/app-wiki/blob/master/bonnier-index-db.wiki/Administration.md)
- [Services](https://github.com/BenjaminMedia/app-wiki/blob/master/bonnier-index-db.wiki/Services.md)
- [Errors](https://github.com/BenjaminMedia/app-wiki/blob/master/bonnier-index-db.wiki/Errors.md)
- [SDK](https://github.com/BenjaminMedia/app-wiki/blob/master/bonnier-index-db.wiki/SDK.md)

## Getting started
The easiest way to learn, debug and understand the API is by using the developer console available through the administration. The developer console is a tool you can use to query, add and remove data - and is handy to have at hand when creating new integrations with the search API.

Click here for more information on how to use the developer console:
https://github.com/BenjaminMedia/bonnier-index-db/wiki/Administration
