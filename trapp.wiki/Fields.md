# Overview
In this section you can see what fields are supported and read more about them.

|Name|Type|Required|
|---|---|---|
|[locale](#locale)|string|true|
|[translate_into](#translate_into)|array|true|
|[deadline](#deadline)|datetime|true|
|[fields](#fields)|object|true|
|[comment](#comment)|string|false|
|[state](#state)|string|false|
|[title](#title)|string|true|

-

### <a name="locale"></a> locale
Locale code for the content.

###### Type
string

###### Example
da_dk
en\_gb

###### Required
True

-

### <a name="translate_into"></a> translate_into
Locale codes you want the content to be translated to

###### Type
array

###### Example
da_dk 
en\_gb

###### Required
True

-

### <a name="deadline"></a> deadline
Datetime that specifies the last due date for the translation.

###### Type
datetime (WC3)

###### Example
2005-08-15T15:52:01+00:00

###### Required
True

-

### <a name="fields"></a> fields
Fields that you want translated.

The object contains 3 required fields: 

- **label**: the name of the item. This value will be the one displayed for the translators.
- **value**: the text that you want translated - should be in the same language as the locale field provided.
- **displayformat**: wysiwyg for WYSIWYG editor, otherwise this can be ignored.

Any additional parameters provided will also be stored and will be displayed in the API.

###### Type
object

###### Example
{ "label": "Test", "value": "My text in the original language", "displayFormat": "wysiwyg" }

###### Required
True

-

### <a name="comment"></a> comment
Comment to the translator.

###### Type
string

###### Example
Please remember to translate the image-text.

###### Required
False

-

### <a name="state"></a> state
ID for the state which the content is currently in.

###### Type
string

###### Example
asda28391238asdasdasd

###### Required
False

-

### <a name="title"></a> title
Title in the original language of the content, will be displayed on lists

###### Type
string

###### Example
Science fiction bliver til virkelighed

###### Required
True
