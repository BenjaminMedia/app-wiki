# Overview
The API multiple types of items. Each type can have a different set of fields. In this section you can see what types that are supported and what fields that the content-type has.

### Type: content
|Name|Type|Required|
|---|---|---|
|[locale](#content_locale)|string|true|
|[title](#content_title)|string|true|
|[description](#content_description)|text|false|
|[content_type](#content_content_type)|string|true|
|[image](#content_image)|string|false|
|[publish_at](#content_publish_at)|datetime|false|
|[created_at](#content_created_at)|datetime|true|
|[updated_at](#content_updated_at)|datetime|true|
|[content_url](#content_content_url)|string|true|
|[relative\_content\_url](#content_relative_content_url)|string|false|
|[active](#content_active)|boolean|true|
|[parent_id](#content_parent_id)|guid|false|
|[meta](#content_meta)|object|false|

### <a name="content_locale"></a> locale
Locale code for the content.

###### Type
string

###### Example
da_dk
en\_gb

###### Requred
True

-

### <a name="content_title"></a> title
The content title

###### Type
string

###### Example
Hello world!

###### Requred
True

-

### <a name="content_description"></a> description
Description/teaser for the content

###### Type
string

###### Example
Hello world!

###### Requred
False

-

### <a name="content_content_type"></a> content_type
Type of the content

###### Type
string

###### Example
article
page

###### Requred
True

-

### <a name="content_image"></a> image
Imgix url to an original full-size image.

###### Type
string

###### Example
http://bonnier.imgix.net/cdn-connect/8a9649466f7e4bf4b4bf41ab48404021.jpg

###### Requred
True

-

### <a name="content_publish_at"></a> publish_at
Date and time when article is supposed to be active/published from. This field is different from created_at. A lot of content can be prepared beforehand - created for example month ago but published on a specific date from which it should be available.

*Note: the API will automatically try to parse the datetime value if the provided value is not a correct datetime format.*

###### Type
datetime (WC3)

###### Example
2005-08-15T15:52:01+00:00

###### Requred
False

-

### <a name="content_created_at"></a> created_at
When was the content created.

*Note: the API will automatically try to parse the datetime value if the provided value is not a correct datetime format.*

###### Type
datetime (WC3)

###### Example
2005-08-15T15:52:01+00:00

###### Requred
True

-

### <a name="content_updated_at"></a> updated_at
When was the content updated.

*Note: the API will automatically try to parse the datetime value if the provided value is not a correct datetime format.*

###### Type
datetime (WC3)

###### Example
2005-08-15T15:52:01+00:00

###### Requred
True

-

### <a name="content_content_url"></a> content_url
Full absolute url for the content

###### Type
string

###### Example
http://www.example.com/my/custom/path

###### Requred
True

-

### <a name="content_relative_content_url"></a> relative\_content_url
Relative url for the content. 

If this field is not provided, it will be generated automaticially using the content_url parameter.

###### Type
string

###### Example
/my/custom/path

###### Requred
False

-

### <a name="content_active"></a> active
Boolean specifying whether this content is active and should be visible to the user.

###### Type
boolean

###### Example
1
0
true
false

###### Requred
True

-

### <a name="content_app_id"></a> app_id
Unique identifier for the content created by the API. Used to determinate which app that created the content.

###### Type
string

###### Example
5DD845435D7B8BF6E9CDD6094BC79CF3

###### Requred
True

-

### <a name="content_parent_id"></a> parent_id
Defines if the content has a relation to another ElasticSearch document.

###### Type
guid

###### Example
5DD845435D7B8BF6E9CDD6094BC79CF3

###### Requred
False

-

### <a name="content_meta"></a> meta
Json object with meta-data. Can contain nested objects.

###### Type
object

###### Example
{ "color": ["red", "blue", "green"] }

###### Requred
False