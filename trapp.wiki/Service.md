# Service

#### Service Calls
Service for creating and retrieving translations.

|Action|Path|Example|Description|
|---|---|---|---|
|GET|[/api/v1/translations](#/get/api/translations)|/api/v1/translations|Returns a list of latest translations.|
|POST|[/api/v1/translations](#/post/api/translations)|/api/v1/translations|Create new translation and returns the id for the new item.|
|GET|[/api/v1/translations/[id]](#/get/api/translations/id)|/api/v1/translations/100|Returns translation with matching id|
|DELETE|[/api/v1/translations/[id]](#/delete/api/translations/id)|/api/v1/translations/100|Delete translation with the matching id|
|PUT|[/api/v1/translations/[id]](#/put/api/translations/id)|/api/v1/translations/100|Update translation with the matching id|

#### Helpers
|Action|Path|Example|Description|
|---|---|---|---|
|GET|[/api/v1/languages](#/get/api/languages)|/api/v1/languages|Returns a list of available languages|
|GET|[/api/v1/states](#/get/api/states)|/api/v1/translations|Returns a list of available states|

## Parameters
This is a list of the parameters supported by the API for filtering and querying items.

For a more detailed description please see: https://github.com/BenjaminMedia/app-wiki/blob/master/trapp.wiki/Parameters.md

|Name|Description|
|---|---|
|[sort](#parameter_sort)|Sort by field|
|[order](#parameter_order)|Order results ascending or descending|
|[locale](#parameter_locale)|Filter the results to only returns items with matching locale(s).|
|[app_id](#parameter_app_id)|Filter the results to only returns items with matching application id.|
|[state](#parameter_state)|Filter results by matching state|
|[q](#parameter_q)|Filters results where meta-data contains the specified value|
|[skip](#parameter_skip)|Skips the entered amount of rows in the result (useful for paging).|
|[limit](#parameter_limit)|Limits the number of rows returned in the result. code|


## Fields

In this section you can see what fields are supported. 

For a more detailed description please see: https://github.com/BenjaminMedia/app-wiki/blob/master/trapp.wiki/Fields.md

|Name|Type|Required|Description|
|---|---|---|---|
|locale|string|true||
|translate_into|array|true||
|deadline|datetime|true||
|fields|object|true||
|title|string|true||
|state|string|false||
|comment|string|false||
|do_callback|boolean|false|When posting an update to a tranlsation; if an update_endpoint_uri has been provided in content creation then the update will always post the updated version of the content to the provided uri. If you do not want any callbacks to be made then you should set the do_callback to false when posting an update.|
|[update\_endpoint_uri](#update_callback)|string|false|Provide a comlete uri to where you want updates to be pushed to, note that the uri is the same for all translated versions of one entity. Meaning if we hav an original article in danish that is being translated into swedish and norwegian. Then all these versions will send updates to the same uri.|

## <a name="/get/api/translations"></a> GET /api/v1/translations
Returns a list of latest translations.

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" https://trapp.whitealbum.dk/api/v1/translations
```
### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));
        
$response = json_decode(curl_exec($ch));

```

#### Response

```json
{  
   "total":240,
   "skip":0,
   "limit":1,
   "rows":[  
      {  
         "language_id":"55eae93ac01443a67a8b456c",
         "deadline":"2015-10-08 00:00:00",
         "original_entity_id":"5614d9d5c0144367308b4567",
         "application_id":4,
         "title":"Har du (ogs\u00e5) v\u00e6ret elskerinde? ",
         "update_endpoint_uri":"http:\/\/localhost:3000\/api\/v1\/translations",
         "updated_at":"2015-10-07 08:38:43",
         "created_at":"2015-10-07 08:37:43",
         "application":{  
            "id":4,
            "display_name":"Woman Website",
            "username":"WomanWebsite",
            "site_code":"wom",
            "app_code":"wom_website",
            "locale":"",
            "last_activity":"2015-08-27 07:34:32",
            "created_at":"2015-07-23 10:00:55",
            "updated_at":"2015-09-02 06:17:00",
            "roles":[  
               {  
                  "role":"content_destroy",
                  "app_id":4,
                  "created_at":"2015-09-02 06:17:00",
                  "updated_at":"2015-09-02 06:17:00"
               },
               {  
                  "role":"content_index",
                  "app_id":4,
                  "created_at":"2015-09-02 06:17:00",
                  "updated_at":"2015-09-02 06:17:00"
               },
               {  
                  "role":"content_show",
                  "app_id":4,
                  "created_at":"2015-09-02 06:17:00",
                  "updated_at":"2015-09-02 06:17:00"
               },
               {  
                  "role":"content_store",
                  "app_id":4,
                  "created_at":"2015-09-02 06:17:00",
                  "updated_at":"2015-09-02 06:17:00"
               },
               {  
                  "role":"content_update",
                  "app_id":4,
                  "created_at":"2015-09-02 06:17:00",
                  "updated_at":"2015-09-02 06:17:00"
               },
               {  
                  "role":"contenttype_index",
                  "app_id":4,
                  "created_at":"2015-09-02 06:17:00",
                  "updated_at":"2015-09-02 06:17:00"
               },
               {  
                  "role":"contenttype_show",
                  "app_id":4,
                  "created_at":"2015-09-02 06:17:00",
                  "updated_at":"2015-09-02 06:17:00"
               }
            ]
         },
         "current_state":"state-missing",
         "fields":[  
            {  
               "label":"Image source",
               "value":"http:\/\/bonnier.imgix.net\/istock_000066575771_medium-KeyYtTCnCiF-eZXYeXsESg.jpg",
               "display_format":"image",
               "group":"group_1071454",
               "shared_key":"4d3050b476bca0f683d8254b8170b3bc"
            },
            {  
               "label":"Body",
               "value":"<h3>Jeg har mistet tilliden til m\u00e6nd<\/h3>\r\n<p>F\u00f8rste gang Lina\u00a0var sammen med en optaget mand, var hun sikker pa\u030a, han ville ga\u030a fra k\u00e6resten. Men efter tre l\u00e6ngevarende forhold til optagede m\u00e6nd har hun efterha\u030anden l\u00e6rt, at det altid er elskerinden, der ender med at blive droppet.<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan startede det?<\/strong> \u201cJeg m\u00f8dte en mand gennem arbejdet. Han var s\u00f8d, men efter et par gange n\u00e6vnte han, at han havde en k\u00e6reste. Sa\u030a bakkede jeg lidt ud. En dag ringede han fra sit job, og vi begyndte at snakke hver dag. Jeg sagde: \u201cVi skal ikke lave noget, du har en k\u00e6reste.\u201d<\/p>\r\n<p><strong>Hvad skete der sa\u030a?<\/strong> \u201cVi jokede med, at han ikke turde tage mig med ned i k\u00e6lderen pa\u030a sit arbejde. Men en dag endte vi dernede og kyssede for f\u00f8rste gang. Der gik to ma\u030aneder, f\u00f8r vi kyssede, og fem ma\u030aneder, f\u00f8r vi gik i seng med hinanden. Forholdet varede halvandet a\u030ar.\u201d<\/p>\r\n<p><strong>Hvad lavede I sammen?<\/strong> \u201cHan ringede til mig, og vi sa\u030a hinanden hver dag. Det f\u00f8ltes som et rigtigt forhold. Det var vildt sp\u00e6ndende, fordi det var forbudt. Men lige sa\u030a meget som jeg gl\u00e6dede mig til at se ham, lige sa\u030a meget hadede jeg det, na\u030ar han tog af sted igen. Jeg vidste jo godt, at han skulle hjem pa\u030a sofaen og se film med k\u00e6resten, og det var det, jeg gerne ville.\u201d<\/p>",
               "display_format":"text",
               "shared_key":"4a044fa6f2291b690d5c23778198a637"
            },
            {  
               "label":"Body",
               "value":"<p><strong>Hvad ha\u030abede du, der ville komme ud af det?<\/strong><\/p>\r\n<p>\u201cJeg ha\u030abede selvf\u00f8lgelig, han ville ga\u030a fra sin k\u00e6reste. Jeg var vildt forelsket, og det tror jeg ogsa\u030a, han var. Han sagde aldrig direkte, at han ville ga\u030a fra hende, men han sagde, at han elskede mig, og at det ikke gik godt derhjemme. Det er en klassiker, har jeg senere fundet ud af. Det irriterede mig, men jeg var vanvittigt forelsket og t\u00e6nkte: \u2018Selvf\u00f8lgelig ga\u030ar han fra sin k\u00e6reste\u2019.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan sluttede det?<\/strong><\/p>\r\n<p>\u201cHan kom til at tale over sig en dag derhjemme. Sa\u030a ringede han til mig og sagde: \u2018Kit, det er slut. Vi kan ikke se hinanden mere\u2019. Jeg blev selvf\u00f8lgelig enormt ked af det og savnede ham helt vildt. Jeg lavede de sidste krampetr\u00e6kninger og ringede til ham hele tiden og sagde: \u2018Jeg vil sa\u030a gerne se dig\u2019. Vi m\u00f8dtes nogle gange derefter, men sa\u030a fik jeg et nyt job og m\u00f8dte en mand der, som jeg blev rigtigt glad for. Han var gift. Sa\u030a de overlappede hinanden, og det var sa\u030adan, jeg kom ud af det.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan havde du det efter de f\u00f8rste to gange?<\/strong><\/p>\r\n<p>\u201cDa svor jeg, at jeg aldrig ville g\u00f8re det igen. Det er ikke fedt. Jeg gider ikke, at en mand skal fa\u030a mig til at sla\u030a mig selv i hovedet og t\u00e6nke: \u2018Hvor er jeg ogsa\u030a dum\u2019.\u201d<\/p>",
               "display_format":"text",
               "shared_key":"01336c6dfd20b7d645688a11df2a831b"
            },
            {  
               "label":"Body",
               "value":"<p><strong>Hvorfor gjorde du det igen?<\/strong><\/p>\r\n<p>\u201cJeg har v\u00e6ret forelsket i alle tre m\u00e6nd, og de har givet udtryk for, at de ville ga\u030a fra deres k\u00e6rester. Ellers havde jeg aldrig indledt noget! Jeg har et princip om, at jeg ikke l\u00e6gger an pa\u030a en optaget mand, men na\u030ar jeg ved, der ikke kan ske noget mellem os, slapper jeg af, og sa\u030a opsta\u030ar kemien. Det er altid startet med venskab, der bliver til forelskelse, men jeg pr\u00f8ver samtidig at sige: \u2018Det ga\u030ar ikke. Du har en k\u00e6reste\u2019. Men m\u00e6ndene er blevet ved med at kontakte mig i ma\u030anedsvis, og sa\u030a har jeg t\u00e6nkt: \u2018Det ma\u030a v\u00e6re, fordi han vil mig\u2019, og givet efter. Nu ved jeg, at de aldrig ga\u030ar fra deres k\u00e6rester.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan f\u00f8ltes det at v\u00e6re elskerinden?<\/strong><\/p>\r\n<p>\u201cDet var frustrerende, for jeg var ked af det og savnede en masse ting. Hver gang jeg skulle til familief\u00f8dselsdag eller holde jul, var jeg alene. Det irriterede mig gr\u00e6nsel\u00f8st at t\u00e6nke pa\u030a, at han var ude for at finde en fin gave til sin k\u00e6reste, na\u030ar jeg ikke fik noget. At v\u00e6re elskerinde er ikke ligesom pa\u030a film, hvor man bliver overd\u00e6nget med blomster og gaver. Det er der ikke noget af. Og samtidig gav jeg ogsa\u030a afkald pa\u030a at finde en anden.\u201d<\/p>",
               "display_format":"text",
               "shared_key":"8420b84b005d8cf6d4419990e0e453f6"
            },
            {  
               "label":"Body",
               "value":"<p><strong>Hvorfor gik du ikke fra dem?\u00a0<\/strong><\/p>\r\n<p>glad og forelsket. Det var f\u00f8rst, na\u030ar der gik et par dage imellem, at jeg blev irriteret. Jeg har altid troet, at det var mig, der bestemte, men det var det ikke. Na\u030ar jeg fortalte mine veninder om det, sagde de: \u2018Kan du ikke se, han bare leger med dig?\u2019 Og det kunne jeg jo godt! Hvis han sa\u030a ikke lige ringede, t\u00e6nkte jeg, at han ma\u030a v\u00e6re sammen med k\u00e6resten. Men hvis jeg sa\u030a ham ofte, na\u030aede jeg ikke at t\u00e6nke de tanker.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan har m\u00e6ndene haft det?<\/strong><\/p>\r\n<p>\u201cDen f\u00f8rste, jeg var sammen med, var samvittighedstynget. Den anden havde v\u00e6ret utro f\u00f8r, sa\u030a jeg tror ikke, han lagde sa\u030a meget i det. Den sidste havde ingen skrupler overhovedet, og jeg fandt ogsa\u030a ud af, at jeg ikke var den eneste, han sa\u030as med.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan har det pa\u030avirket dit forhold til m\u00e6nd?<\/strong><\/p>\r\n<p>\u201cDet er ikke nemt for mig at stole pa\u030a m\u00e6nd. Jeg har v\u00e6ret sammen med tre, der havde k\u00e6rester, og jeg har fa\u030aet mange tilbud derudover. Hver gang giver det lidt n\u00e6ring til den spire, der har ligget derinde siden f\u00f8rste gang, som siger: \u2018Kan jeg stole pa\u030a en mand? Findes der en mand derude, som aldrig ville v\u00e6re sin k\u00e6reste utro?\u2019. Det er skideha\u030ardt.\u201d<\/p>",
               "display_format":"text",
               "shared_key":"3b5000a48e7f14a8caa3d5eccb37d06e"
            },
            {  
               "label":"Body",
               "value":"<p><strong>Har du haft da\u030arlig samvittighed?<\/strong><\/p>\r\n<p>\u201cJa. Jeg ha\u030abbede hver eneste dag, det ville blive opdaget. Ikke kun for at jeg kunne fa\u030a ham, men for at retf\u00e6rdigheden skulle ske fyldest. Hvis det var min k\u00e6reste, ville jeg gerne vide det, sa\u030a jeg selv kunne v\u00e6lge, om jeg ville blive sammen med ham. Det samme valg synes jeg, andre kvinder skal have. Men jeg ville aldrig kunne tilgive det. Jeg ved jo, hvad der sker hos den anden kvinde, og hvor mange f\u00f8lelser der er involveret.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvad kommer der ud af at v\u00e6re sammen med en optaget mand?<\/strong><\/p>\r\n<p>\u201cIkke noget godt. Elskerinden fa\u030ar ikke det forhold, hun gerne vil have. Hans k\u00e6reste har ikke den k\u00e6reste, hun gerne vil have, og hvis manden har bare en smule samvittighed, ga\u030ar han jo ogsa\u030a og grubler og har det da\u030arligt.\u201d<\/p>\r\n<p><strong>Kunne du finde pa\u030a at g\u00f8re det igen?<\/strong><\/p>\r\n<p>\u201cDet ha\u030aber jeg virkelig ikke. Jeg har fa\u030aet min egen k\u00e6reste nu og l\u00e6rt, at det godt kan betale sig, for s\u00e5 f\u00e5r jeg alle de ting, som jeg nu ved, jeg ville have. Det er ikke kun sex, men ogs\u00e5 hygge i sofaen, n\u00e6rhed og f\u00f8lelsen af at v\u00e6re elsket.\"\u00a0<\/p>",
               "display_format":"text",
               "shared_key":"a00bdb1ca81a649cdd5cb6e09e2bec14"
            },
            {  
               "label":"Body",
               "value":"<h3>Livas r\u00e5d: Forelsket i en optaget mand?\u00a0<\/h3>\r\n<p><strong>V\u00e6r ikke venner<\/strong>\u00a0<\/p>\r\n<p>Du narrer dig selv, hvis du tror, du kan v\u00e6re venner med en mand, du er forelsket i. F\u00f8rst na\u030ar du cutter kontakten helt, kan du l\u00f8srive dig.<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Brug veninderne<\/strong><\/p>\r\n<p>Dine veninder synes, du har fortjent bedre, sa\u030a lad dem st\u00f8tte dig. Bind dig til aftaler med dem, sa\u030a du ikke bliver fristet til at m\u00f8des med ham.<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Bliv bevidst<\/strong><\/p>\r\n<p>Er det behovet for bekr\u00e6ftelse eller beg\u00e6r, der fa\u030ar dig til at ga\u030a i f\u00e6lden? Find ud af det, sa\u030a du lettere kan sta\u030a imod og eventuelt fa\u030a dine behov d\u00e6kket et andet sted.<\/p>\r\n<p>\u00a0<\/p>\r\n<p><em>Bragt f\u00f8rste gang i Woman nr. 160.\u00a0<\/em><\/p>",
               "display_format":"text",
               "shared_key":"cb100ffd3807c95b93b3c8c0f726fadb"
            }
         ],
         "state":"state-missing",
         "id":"5614d9d7c0144367308b458b",
         "revisions":[  
            {  
               "_id":"5614d9d7c0144367308b458c",
               "comment":"Hello from WA",
               "revision_count":0,
               "entity_id":"5614d9d7c0144367308b458b",
               "state":"state-waiting",
               "user_id":null,
               "updated_at":"2015-10-07 08:37:43",
               "created_at":"2015-10-07 08:37:43",
               "fields":[  
                  {  
                     "_id":"5614d9d7c0144367308b458d",
                     "label":"Image source",
                     "value":"http:\/\/bonnier.imgix.net\/istock_000066575771_medium-KeyYtTCnCiF-eZXYeXsESg.jpg",
                     "display_format":"image",
                     "group":"group_1071454",
                     "shared_key":"4d3050b476bca0f683d8254b8170b3bc"
                  },
                  {  
                     "_id":"5614d9d7c0144367308b458e",
                     "label":"Body",
                     "value":"<h3>Jeg har mistet tilliden til m&aelig;nd<\/h3>\r\n<p>F&oslash;rste gang Lina&nbsp;var sammen med en optaget mand, var hun sikker pa\u030a, han ville ga\u030a fra k&aelig;resten. Men efter tre l&aelig;ngevarende forhold til optagede m&aelig;nd har hun efterha\u030anden l&aelig;rt, at det altid er elskerinden, der ender med at blive droppet.<\/p>\r\n<p>&nbsp;<\/p>\r\n<p><strong>Hvordan startede det?<\/strong> &ldquo;Jeg m&oslash;dte en mand gennem arbejdet. Han var s&oslash;d, men efter et par gange n&aelig;vnte han, at han havde en k&aelig;reste. Sa\u030a bakkede jeg lidt ud. En dag ringede han fra sit job, og vi begyndte at snakke hver dag. Jeg sagde: &ldquo;Vi skal ikke lave noget, du har en k&aelig;reste.&rdquo;<\/p>\r\n<p><strong>Hvad skete der sa\u030a?<\/strong> &ldquo;Vi jokede med, at han ikke turde tage mig med ned i k&aelig;lderen pa\u030a sit arbejde. Men en dag endte vi dernede og kyssede for f&oslash;rste gang. Der gik to ma\u030aneder, f&oslash;r vi kyssede, og fem ma\u030aneder, f&oslash;r vi gik i seng med hinanden. Forholdet varede halvandet a\u030ar.&rdquo;<\/p>\r\n<p><strong>Hvad lavede I sammen?<\/strong> &ldquo;Han ringede til mig, og vi sa\u030a hinanden hver dag. Det f&oslash;ltes som et rigtigt forhold. Det var vildt sp&aelig;ndende, fordi det var forbudt. Men lige sa\u030a meget som jeg gl&aelig;dede mig til at se ham, lige sa\u030a meget hadede jeg det, na\u030ar han tog af sted igen. Jeg vidste jo godt, at han skulle hjem pa\u030a sofaen og se film med k&aelig;resten, og det var det, jeg gerne ville.&rdquo;<\/p>",
                     "display_format":"text",
                     "shared_key":"4a044fa6f2291b690d5c23778198a637"
                  },
                  {  
                     "_id":"5614d9d7c0144367308b458f",
                     "label":"Body",
                     "value":"<p><strong>Hvad ha\u030abede du, der ville komme ud af det?<\/strong><\/p>\r\n<p>&ldquo;Jeg ha\u030abede selvf&oslash;lgelig, han ville ga\u030a fra sin k&aelig;reste. Jeg var vildt forelsket, og det tror jeg ogsa\u030a, han var. Han sagde aldrig direkte, at han ville ga\u030a fra hende, men han sagde, at han elskede mig, og at det ikke gik godt derhjemme. Det er en klassiker, har jeg senere fundet ud af. Det irriterede mig, men jeg var vanvittigt forelsket og t&aelig;nkte: &lsquo;Selvf&oslash;lgelig ga\u030ar han fra sin k&aelig;reste&rsquo;.&rdquo;<\/p>\r\n<p>&nbsp;<\/p>\r\n<p><strong>Hvordan sluttede det?<\/strong><\/p>\r\n<p>&ldquo;Han kom til at tale over sig en dag derhjemme. Sa\u030a ringede han til mig og sagde: &lsquo;Kit, det er slut. Vi kan ikke se hinanden mere&rsquo;. Jeg blev selvf&oslash;lgelig enormt ked af det og savnede ham helt vildt. Jeg lavede de sidste krampetr&aelig;kninger og ringede til ham hele tiden og sagde: &lsquo;Jeg vil sa\u030a gerne se dig&rsquo;. Vi m&oslash;dtes nogle gange derefter, men sa\u030a fik jeg et nyt job og m&oslash;dte en mand der, som jeg blev rigtigt glad for. Han var gift. Sa\u030a de overlappede hinanden, og det var sa\u030adan, jeg kom ud af det.&rdquo;<\/p>\r\n<p>&nbsp;<\/p>\r\n<p><strong>Hvordan havde du det efter de f&oslash;rste to gange?<\/strong><\/p>\r\n<p>&ldquo;Da svor jeg, at jeg aldrig ville g&oslash;re det igen. Det er ikke fedt. Jeg gider ikke, at en mand skal fa\u030a mig til at sla\u030a mig selv i hovedet og t&aelig;nke: &lsquo;Hvor er jeg ogsa\u030a dum&rsquo;.&rdquo;<\/p>",
                     "display_format":"text",
                     "shared_key":"01336c6dfd20b7d645688a11df2a831b"
                  },
                  {  
                     "_id":"5614d9d7c0144367308b4590",
                     "label":"Body",
                     "value":"<p><strong>Hvorfor gjorde du det igen?<\/strong><\/p>\r\n<p>&ldquo;Jeg har v&aelig;ret forelsket i alle tre m&aelig;nd, og de har givet udtryk for, at de ville ga\u030a fra deres k&aelig;rester. Ellers havde jeg aldrig indledt noget! Jeg har et princip om, at jeg ikke l&aelig;gger an pa\u030a en optaget mand, men na\u030ar jeg ved, der ikke kan ske noget mellem os, slapper jeg af, og sa\u030a opsta\u030ar kemien. Det er altid startet med venskab, der bliver til forelskelse, men jeg pr&oslash;ver samtidig at sige: &lsquo;Det ga\u030ar ikke. Du har en k&aelig;reste&rsquo;. Men m&aelig;ndene er blevet ved med at kontakte mig i ma\u030anedsvis, og sa\u030a har jeg t&aelig;nkt: &lsquo;Det ma\u030a v&aelig;re, fordi han vil mig&rsquo;, og givet efter. Nu ved jeg, at de aldrig ga\u030ar fra deres k&aelig;rester.&rdquo;<\/p>\r\n<p>&nbsp;<\/p>\r\n<p><strong>Hvordan f&oslash;ltes det at v&aelig;re elskerinden?<\/strong><\/p>\r\n<p>&ldquo;Det var frustrerende, for jeg var ked af det og savnede en masse ting. Hver gang jeg skulle til familief&oslash;dselsdag eller holde jul, var jeg alene. Det irriterede mig gr&aelig;nsel&oslash;st at t&aelig;nke pa\u030a, at han var ude for at finde en fin gave til sin k&aelig;reste, na\u030ar jeg ikke fik noget. At v&aelig;re elskerinde er ikke ligesom pa\u030a film, hvor man bliver overd&aelig;nget med blomster og gaver. Det er der ikke noget af. Og samtidig gav jeg ogsa\u030a afkald pa\u030a at finde en anden.&rdquo;<\/p>",
                     "display_format":"text",
                     "shared_key":"8420b84b005d8cf6d4419990e0e453f6"
                  },
                  {  
                     "_id":"5614d9d7c0144367308b4591",
                     "label":"Body",
                     "value":"<p><strong>Hvorfor gik du ikke fra dem?&nbsp;<\/strong><\/p>\r\n<p>glad og forelsket. Det var f&oslash;rst, na\u030ar der gik et par dage imellem, at jeg blev irriteret. Jeg har altid troet, at det var mig, der bestemte, men det var det ikke. Na\u030ar jeg fortalte mine veninder om det, sagde de: &lsquo;Kan du ikke se, han bare leger med dig?&rsquo; Og det kunne jeg jo godt! Hvis han sa\u030a ikke lige ringede, t&aelig;nkte jeg, at han ma\u030a v&aelig;re sammen med k&aelig;resten. Men hvis jeg sa\u030a ham ofte, na\u030aede jeg ikke at t&aelig;nke de tanker.&rdquo;<\/p>\r\n<p>&nbsp;<\/p>\r\n<p><strong>Hvordan har m&aelig;ndene haft det?<\/strong><\/p>\r\n<p>&ldquo;Den f&oslash;rste, jeg var sammen med, var samvittighedstynget. Den anden havde v&aelig;ret utro f&oslash;r, sa\u030a jeg tror ikke, han lagde sa\u030a meget i det. Den sidste havde ingen skrupler overhovedet, og jeg fandt ogsa\u030a ud af, at jeg ikke var den eneste, han sa\u030as med.&rdquo;<\/p>\r\n<p>&nbsp;<\/p>\r\n<p><strong>Hvordan har det pa\u030avirket dit forhold til m&aelig;nd?<\/strong><\/p>\r\n<p>&ldquo;Det er ikke nemt for mig at stole pa\u030a m&aelig;nd. Jeg har v&aelig;ret sammen med tre, der havde k&aelig;rester, og jeg har fa\u030aet mange tilbud derudover. Hver gang giver det lidt n&aelig;ring til den spire, der har ligget derinde siden f&oslash;rste gang, som siger: &lsquo;Kan jeg stole pa\u030a en mand? Findes der en mand derude, som aldrig ville v&aelig;re sin k&aelig;reste utro?&rsquo;. Det er skideha\u030ardt.&rdquo;<\/p>",
                     "display_format":"text",
                     "shared_key":"3b5000a48e7f14a8caa3d5eccb37d06e"
                  },
                  {  
                     "_id":"5614d9d7c0144367308b4592",
                     "label":"Body",
                     "value":"<p><strong>Har du haft da\u030arlig samvittighed?<\/strong><\/p>\r\n<p>&ldquo;Ja. Jeg ha\u030abbede hver eneste dag, det ville blive opdaget. Ikke kun for at jeg kunne fa\u030a ham, men for at retf&aelig;rdigheden skulle ske fyldest. Hvis det var min k&aelig;reste, ville jeg gerne vide det, sa\u030a jeg selv kunne v&aelig;lge, om jeg ville blive sammen med ham. Det samme valg synes jeg, andre kvinder skal have. Men jeg ville aldrig kunne tilgive det. Jeg ved jo, hvad der sker hos den anden kvinde, og hvor mange f&oslash;lelser der er involveret.&rdquo;<\/p>\r\n<p>&nbsp;<\/p>\r\n<p><strong>Hvad kommer der ud af at v&aelig;re sammen med en optaget mand?<\/strong><\/p>\r\n<p>&ldquo;Ikke noget godt. Elskerinden fa\u030ar ikke det forhold, hun gerne vil have. Hans k&aelig;reste har ikke den k&aelig;reste, hun gerne vil have, og hvis manden har bare en smule samvittighed, ga\u030ar han jo ogsa\u030a og grubler og har det da\u030arligt.&rdquo;<\/p>\r\n<p><strong>Kunne du finde pa\u030a at g&oslash;re det igen?<\/strong><\/p>\r\n<p>&ldquo;Det ha\u030aber jeg virkelig ikke. Jeg har fa\u030aet min egen k&aelig;reste nu og l&aelig;rt, at det godt kan betale sig, for s&aring; f&aring;r jeg alle de ting, som jeg nu ved, jeg ville have. Det er ikke kun sex, men ogs&aring; hygge i sofaen, n&aelig;rhed og f&oslash;lelsen af at v&aelig;re elsket.\"&nbsp;<\/p>",
                     "display_format":"text",
                     "shared_key":"a00bdb1ca81a649cdd5cb6e09e2bec14"
                  },
                  {  
                     "_id":"5614d9d7c0144367308b4593",
                     "label":"Body",
                     "value":"<h3>Livas r&aring;d: Forelsket i en optaget mand?&nbsp;<\/h3>\r\n<p><strong>V&aelig;r ikke venner<\/strong>&nbsp;<\/p>\r\n<p>Du narrer dig selv, hvis du tror, du kan v&aelig;re venner med en mand, du er forelsket i. F&oslash;rst na\u030ar du cutter kontakten helt, kan du l&oslash;srive dig.<\/p>\r\n<p>&nbsp;<\/p>\r\n<p><strong>Brug veninderne<\/strong><\/p>\r\n<p>Dine veninder synes, du har fortjent bedre, sa\u030a lad dem st&oslash;tte dig. Bind dig til aftaler med dem, sa\u030a du ikke bliver fristet til at m&oslash;des med ham.<\/p>\r\n<p>&nbsp;<\/p>\r\n<p><strong>Bliv bevidst<\/strong><\/p>\r\n<p>Er det behovet for bekr&aelig;ftelse eller beg&aelig;r, der fa\u030ar dig til at ga\u030a i f&aelig;lden? Find ud af det, sa\u030a du lettere kan sta\u030a imod og eventuelt fa\u030a dine behov d&aelig;kket et andet sted.<\/p>\r\n<p>&nbsp;<\/p>\r\n<p><em>Bragt f&oslash;rste gang i Woman nr. 160.&nbsp;<\/em><\/p>",
                     "display_format":"text",
                     "shared_key":"cb100ffd3807c95b93b3c8c0f726fadb"
                  }
               ],
               "user":null
            },
            {  
               "_id":"5614da13c0144374308b45c0",
               "revision_count":1,
               "entity_id":"5614d9d7c0144367308b458b",
               "state":"state-missing",
               "user_id":null,
               "updated_at":"2015-10-07 08:38:43",
               "created_at":"2015-10-07 08:38:43",
               "fields":[  
                  {  
                     "_id":"5614da13c0144374308b45c1",
                     "label":"Image source",
                     "value":"http:\/\/bonnier.imgix.net\/istock_000066575771_medium-KeyYtTCnCiF-eZXYeXsESg.jpg",
                     "display_format":"image",
                     "group":"group_1071454",
                     "shared_key":"4d3050b476bca0f683d8254b8170b3bc"
                  },
                  {  
                     "_id":"5614da13c0144374308b45c2",
                     "label":"Body",
                     "value":"<h3>Jeg har mistet tilliden til m\u00e6nd<\/h3>\r\n<p>F\u00f8rste gang Lina\u00a0var sammen med en optaget mand, var hun sikker pa\u030a, han ville ga\u030a fra k\u00e6resten. Men efter tre l\u00e6ngevarende forhold til optagede m\u00e6nd har hun efterha\u030anden l\u00e6rt, at det altid er elskerinden, der ender med at blive droppet.<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan startede det?<\/strong> \u201cJeg m\u00f8dte en mand gennem arbejdet. Han var s\u00f8d, men efter et par gange n\u00e6vnte han, at han havde en k\u00e6reste. Sa\u030a bakkede jeg lidt ud. En dag ringede han fra sit job, og vi begyndte at snakke hver dag. Jeg sagde: \u201cVi skal ikke lave noget, du har en k\u00e6reste.\u201d<\/p>\r\n<p><strong>Hvad skete der sa\u030a?<\/strong> \u201cVi jokede med, at han ikke turde tage mig med ned i k\u00e6lderen pa\u030a sit arbejde. Men en dag endte vi dernede og kyssede for f\u00f8rste gang. Der gik to ma\u030aneder, f\u00f8r vi kyssede, og fem ma\u030aneder, f\u00f8r vi gik i seng med hinanden. Forholdet varede halvandet a\u030ar.\u201d<\/p>\r\n<p><strong>Hvad lavede I sammen?<\/strong> \u201cHan ringede til mig, og vi sa\u030a hinanden hver dag. Det f\u00f8ltes som et rigtigt forhold. Det var vildt sp\u00e6ndende, fordi det var forbudt. Men lige sa\u030a meget som jeg gl\u00e6dede mig til at se ham, lige sa\u030a meget hadede jeg det, na\u030ar han tog af sted igen. Jeg vidste jo godt, at han skulle hjem pa\u030a sofaen og se film med k\u00e6resten, og det var det, jeg gerne ville.\u201d<\/p>",
                     "display_format":"text",
                     "shared_key":"4a044fa6f2291b690d5c23778198a637"
                  },
                  {  
                     "_id":"5614da13c0144374308b45c3",
                     "label":"Body",
                     "value":"<p><strong>Hvad ha\u030abede du, der ville komme ud af det?<\/strong><\/p>\r\n<p>\u201cJeg ha\u030abede selvf\u00f8lgelig, han ville ga\u030a fra sin k\u00e6reste. Jeg var vildt forelsket, og det tror jeg ogsa\u030a, han var. Han sagde aldrig direkte, at han ville ga\u030a fra hende, men han sagde, at han elskede mig, og at det ikke gik godt derhjemme. Det er en klassiker, har jeg senere fundet ud af. Det irriterede mig, men jeg var vanvittigt forelsket og t\u00e6nkte: \u2018Selvf\u00f8lgelig ga\u030ar han fra sin k\u00e6reste\u2019.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan sluttede det?<\/strong><\/p>\r\n<p>\u201cHan kom til at tale over sig en dag derhjemme. Sa\u030a ringede han til mig og sagde: \u2018Kit, det er slut. Vi kan ikke se hinanden mere\u2019. Jeg blev selvf\u00f8lgelig enormt ked af det og savnede ham helt vildt. Jeg lavede de sidste krampetr\u00e6kninger og ringede til ham hele tiden og sagde: \u2018Jeg vil sa\u030a gerne se dig\u2019. Vi m\u00f8dtes nogle gange derefter, men sa\u030a fik jeg et nyt job og m\u00f8dte en mand der, som jeg blev rigtigt glad for. Han var gift. Sa\u030a de overlappede hinanden, og det var sa\u030adan, jeg kom ud af det.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan havde du det efter de f\u00f8rste to gange?<\/strong><\/p>\r\n<p>\u201cDa svor jeg, at jeg aldrig ville g\u00f8re det igen. Det er ikke fedt. Jeg gider ikke, at en mand skal fa\u030a mig til at sla\u030a mig selv i hovedet og t\u00e6nke: \u2018Hvor er jeg ogsa\u030a dum\u2019.\u201d<\/p>",
                     "display_format":"text",
                     "shared_key":"01336c6dfd20b7d645688a11df2a831b"
                  },
                  {  
                     "_id":"5614da13c0144374308b45c4",
                     "label":"Body",
                     "value":"<p><strong>Hvorfor gjorde du det igen?<\/strong><\/p>\r\n<p>\u201cJeg har v\u00e6ret forelsket i alle tre m\u00e6nd, og de har givet udtryk for, at de ville ga\u030a fra deres k\u00e6rester. Ellers havde jeg aldrig indledt noget! Jeg har et princip om, at jeg ikke l\u00e6gger an pa\u030a en optaget mand, men na\u030ar jeg ved, der ikke kan ske noget mellem os, slapper jeg af, og sa\u030a opsta\u030ar kemien. Det er altid startet med venskab, der bliver til forelskelse, men jeg pr\u00f8ver samtidig at sige: \u2018Det ga\u030ar ikke. Du har en k\u00e6reste\u2019. Men m\u00e6ndene er blevet ved med at kontakte mig i ma\u030anedsvis, og sa\u030a har jeg t\u00e6nkt: \u2018Det ma\u030a v\u00e6re, fordi han vil mig\u2019, og givet efter. Nu ved jeg, at de aldrig ga\u030ar fra deres k\u00e6rester.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan f\u00f8ltes det at v\u00e6re elskerinden?<\/strong><\/p>\r\n<p>\u201cDet var frustrerende, for jeg var ked af det og savnede en masse ting. Hver gang jeg skulle til familief\u00f8dselsdag eller holde jul, var jeg alene. Det irriterede mig gr\u00e6nsel\u00f8st at t\u00e6nke pa\u030a, at han var ude for at finde en fin gave til sin k\u00e6reste, na\u030ar jeg ikke fik noget. At v\u00e6re elskerinde er ikke ligesom pa\u030a film, hvor man bliver overd\u00e6nget med blomster og gaver. Det er der ikke noget af. Og samtidig gav jeg ogsa\u030a afkald pa\u030a at finde en anden.\u201d<\/p>",
                     "display_format":"text",
                     "shared_key":"8420b84b005d8cf6d4419990e0e453f6"
                  },
                  {  
                     "_id":"5614da13c0144374308b45c5",
                     "label":"Body",
                     "value":"<p><strong>Hvorfor gik du ikke fra dem?\u00a0<\/strong><\/p>\r\n<p>glad og forelsket. Det var f\u00f8rst, na\u030ar der gik et par dage imellem, at jeg blev irriteret. Jeg har altid troet, at det var mig, der bestemte, men det var det ikke. Na\u030ar jeg fortalte mine veninder om det, sagde de: \u2018Kan du ikke se, han bare leger med dig?\u2019 Og det kunne jeg jo godt! Hvis han sa\u030a ikke lige ringede, t\u00e6nkte jeg, at han ma\u030a v\u00e6re sammen med k\u00e6resten. Men hvis jeg sa\u030a ham ofte, na\u030aede jeg ikke at t\u00e6nke de tanker.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan har m\u00e6ndene haft det?<\/strong><\/p>\r\n<p>\u201cDen f\u00f8rste, jeg var sammen med, var samvittighedstynget. Den anden havde v\u00e6ret utro f\u00f8r, sa\u030a jeg tror ikke, han lagde sa\u030a meget i det. Den sidste havde ingen skrupler overhovedet, og jeg fandt ogsa\u030a ud af, at jeg ikke var den eneste, han sa\u030as med.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvordan har det pa\u030avirket dit forhold til m\u00e6nd?<\/strong><\/p>\r\n<p>\u201cDet er ikke nemt for mig at stole pa\u030a m\u00e6nd. Jeg har v\u00e6ret sammen med tre, der havde k\u00e6rester, og jeg har fa\u030aet mange tilbud derudover. Hver gang giver det lidt n\u00e6ring til den spire, der har ligget derinde siden f\u00f8rste gang, som siger: \u2018Kan jeg stole pa\u030a en mand? Findes der en mand derude, som aldrig ville v\u00e6re sin k\u00e6reste utro?\u2019. Det er skideha\u030ardt.\u201d<\/p>",
                     "display_format":"text",
                     "shared_key":"3b5000a48e7f14a8caa3d5eccb37d06e"
                  },
                  {  
                     "_id":"5614da13c0144374308b45c6",
                     "label":"Body",
                     "value":"<p><strong>Har du haft da\u030arlig samvittighed?<\/strong><\/p>\r\n<p>\u201cJa. Jeg ha\u030abbede hver eneste dag, det ville blive opdaget. Ikke kun for at jeg kunne fa\u030a ham, men for at retf\u00e6rdigheden skulle ske fyldest. Hvis det var min k\u00e6reste, ville jeg gerne vide det, sa\u030a jeg selv kunne v\u00e6lge, om jeg ville blive sammen med ham. Det samme valg synes jeg, andre kvinder skal have. Men jeg ville aldrig kunne tilgive det. Jeg ved jo, hvad der sker hos den anden kvinde, og hvor mange f\u00f8lelser der er involveret.\u201d<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Hvad kommer der ud af at v\u00e6re sammen med en optaget mand?<\/strong><\/p>\r\n<p>\u201cIkke noget godt. Elskerinden fa\u030ar ikke det forhold, hun gerne vil have. Hans k\u00e6reste har ikke den k\u00e6reste, hun gerne vil have, og hvis manden har bare en smule samvittighed, ga\u030ar han jo ogsa\u030a og grubler og har det da\u030arligt.\u201d<\/p>\r\n<p><strong>Kunne du finde pa\u030a at g\u00f8re det igen?<\/strong><\/p>\r\n<p>\u201cDet ha\u030aber jeg virkelig ikke. Jeg har fa\u030aet min egen k\u00e6reste nu og l\u00e6rt, at det godt kan betale sig, for s\u00e5 f\u00e5r jeg alle de ting, som jeg nu ved, jeg ville have. Det er ikke kun sex, men ogs\u00e5 hygge i sofaen, n\u00e6rhed og f\u00f8lelsen af at v\u00e6re elsket.\"\u00a0<\/p>",
                     "display_format":"text",
                     "shared_key":"a00bdb1ca81a649cdd5cb6e09e2bec14"
                  },
                  {  
                     "_id":"5614da13c0144374308b45c7",
                     "label":"Body",
                     "value":"<h3>Livas r\u00e5d: Forelsket i en optaget mand?\u00a0<\/h3>\r\n<p><strong>V\u00e6r ikke venner<\/strong>\u00a0<\/p>\r\n<p>Du narrer dig selv, hvis du tror, du kan v\u00e6re venner med en mand, du er forelsket i. F\u00f8rst na\u030ar du cutter kontakten helt, kan du l\u00f8srive dig.<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Brug veninderne<\/strong><\/p>\r\n<p>Dine veninder synes, du har fortjent bedre, sa\u030a lad dem st\u00f8tte dig. Bind dig til aftaler med dem, sa\u030a du ikke bliver fristet til at m\u00f8des med ham.<\/p>\r\n<p>\u00a0<\/p>\r\n<p><strong>Bliv bevidst<\/strong><\/p>\r\n<p>Er det behovet for bekr\u00e6ftelse eller beg\u00e6r, der fa\u030ar dig til at ga\u030a i f\u00e6lden? Find ud af det, sa\u030a du lettere kan sta\u030a imod og eventuelt fa\u030a dine behov d\u00e6kket et andet sted.<\/p>\r\n<p>\u00a0<\/p>\r\n<p><em>Bragt f\u00f8rste gang i Woman nr. 160.\u00a0<\/em><\/p>",
                     "display_format":"text",
                     "shared_key":"cb100ffd3807c95b93b3c8c0f726fadb"
                  }
               ],
               "user":null
            }
         ],
         "original":{  
            "language_id":"55eae93ac01443a67a8b4567",
            "deadline":"2015-10-08 00:00:00",
            "original_entity_id":null,
            "application_id":4,
            "title":"Har du (ogs\u00e5) v\u00e6ret elskerinde? ",
            "update_endpoint_uri":"http:\/\/localhost:3000\/api\/v1\/translations",
            "updated_at":"2015-10-07 08:37:43",
            "created_at":"2015-10-07 08:37:41",
            "current_state":"state-waiting",
            "translations":[  
               {  
                  "id":"5614d9d6c0144367308b4570",
                  "locale":"sv_se"
               },
               {  
                  "id":"5614d9d6c0144367308b4579",
                  "locale":"nb_no"
               },
               {  
                  "id":"5614d9d6c0144367308b4582",
                  "locale":"fi_fi"
               },
               {  
                  "id":"5614d9d7c0144367308b458b",
                  "locale":"nl_nl"
               }
            ],
            "id":"5614d9d5c0144367308b4567"
         },
         "language":{  
            "_id":"55eae93ac01443a67a8b456c",
            "name":"Dutch",
            "locale":"nl_nl",
            "country":"Netherlands"
         }
      }
   ]
}
```

## <a name="/post/api/translations"></a> POST /api/v1/translations

Creates a new translation of the given type and returns the id for the newly created item.

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" -X POST -d "locale=da-dk&title=My title&image=http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png&content_type=article&publish_at=25-04-2015 15:15&created_at=26-04-2015 15:20&updated_at=27-04-2015 15:30&path=/path&active=true&content_url=http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2" http://trapp.whitealbum.dk/api/v1/translations
```
### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations/5DD845435D7B8BF6E9CDD6094BC79CF3');

$data = array('_method' => 'POST', 'locale' => 'da-dk', 'title' => 'My new title', 'image' => 'http://bonnier.imgix.net/ted-12-Dz6yqo0rVNdE8BQQjlKNYQ.png', 'content_type' => 'article', 'publish_at' => '25-04-2015 15:15', 'created_at' => '26-04-2015 15:20', 'updated_at' => '27-04-2015 15:30', 'path' => '/path', 'active' => true, 'content_url' => 'http://mmm.dk/konkurrencer/vind-en-ted-bamse-to-billetter-til-ted-2');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));

$response = json_decode(curl_exec($ch));
```

###### Response

```json
{
  "language_id": "56167aae6022b0b9080041a7",
  "deadline": "2015-10-22 11:40:00",
  "original_entity_id": null,
  "application_id": 1,
  "title": "En aweseome titel 222334",
  "updated_at": "2015-10-14 13:00:33",
  "created_at": "2015-10-14 13:00:33",
  "current_state": "state-waiting",
  "translations": [
    {
      "id": "561e51f16022b09d060041ad",
      "locale": "nl_nl"
    },
    {
      "id": "561e51f16022b09d060041b3",
      "locale": "sv_se"
    }
  ],
  "edit_uri": "http://local.trapp.dk/translation/561e51f16022b09d060041a7/edit",
  "id": "561e51f16022b09d060041a7",
  "revisions": [
    {
      "_id": "561e51f16022b09d060041a8",
      "comment": "en kommentar",
      "revision_count": 0,
      "entity_id": "561e51f16022b09d060041a7",
      "state": "state-waiting",
      "user_id": null,
      "updated_at": "2015-10-14 13:00:33",
      "created_at": "2015-10-14 13:00:33",
      "fields": [
        {
          "_id": "561e51f16022b09d060041a9",
          "label": "Title",
          "value": "http://test.com/haha",
          "display_format": "image",
          "shared_key": "0992872de9ad3a5f86a3d3560b28f3b4"
        },
        {
          "_id": "561e51f16022b09d060041aa",
          "label": "Body",
          "value": "Dette er en lang body tekst....",
          "display_format": "text",
          "max_length": 1000,
          "shared_key": "7ad9a153ca32dcc98a046f03fc9fd872"
        },
        {
          "_id": "561e51f16022b09d060041ab",
          "label": "Gruppe felt",
          "value": "Dette er et gruppe felt",
          "display_format": "text",
          "group": "Gruppe 1",
          "shared_key": "6dee999b6549d0cfd62e0ab390bc993e"
        },
        {
          "_id": "561e51f16022b09d060041ac",
          "label": "Gruppe text",
          "value": "Dette er et gruppe atribut",
          "display_format": "text",
          "group": "Gruppe 1",
          "shared_key": "623807a299f6ca4b0ebb980eeb69c87a"
        }
      ],
      "user": null
    }
  ],
  "original": null,
  "language": {
    "_id": "56167aae6022b0b9080041a7",
    "name": "Danish",
    "locale": "da_dk",
    "country": "Denmark"
  }
}
```

## <a name="/get/api/translations/id"></a> GET /api/v1/translations/[id]

Returns translation with matching id

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" https://trapp.whitealbum.dk/api/v1/translations/55b8f5b2214f48da0900421f
```

### PHP

###### Request

```php
$ch = curl_init('https://traoo.whitealbum.dk/api/v1/translations/472411B3EEE17052A861D1C34DF9C646');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));
        
$response = json_decode(curl_exec($ch));
```

#### Response

```json
{
  "language_id": "56167aae6022b0b9080041a7",
  "deadline": "2015-10-22 11:40:00",
  "original_entity_id": null,
  "application_id": 1,
  "title": "En aweseome titel 222334",
  "updated_at": "2015-10-14 13:00:33",
  "created_at": "2015-10-14 13:00:33",
  "current_state": "state-waiting",
  "translations": [
    {
      "id": "561e51f16022b09d060041ad",
      "locale": "nl_nl"
    },
    {
      "id": "561e51f16022b09d060041b3",
      "locale": "sv_se"
    }
  ],
  "edit_uri": "http://local.trapp.dk/translation/561e51f16022b09d060041a7/edit",
  "id": "561e51f16022b09d060041a7",
  "revisions": [
    {
      "_id": "561e51f16022b09d060041a8",
      "comment": "en kommentar",
      "revision_count": 0,
      "entity_id": "561e51f16022b09d060041a7",
      "state": "state-waiting",
      "user_id": null,
      "updated_at": "2015-10-14 13:00:33",
      "created_at": "2015-10-14 13:00:33",
      "fields": [
        {
          "_id": "561e51f16022b09d060041a9",
          "label": "Title",
          "value": "http://test.com/haha",
          "display_format": "image",
          "shared_key": "0992872de9ad3a5f86a3d3560b28f3b4"
        },
        {
          "_id": "561e51f16022b09d060041aa",
          "label": "Body",
          "value": "Dette er en lang body tekst....",
          "display_format": "text",
          "max_length": 1000,
          "shared_key": "7ad9a153ca32dcc98a046f03fc9fd872"
        },
        {
          "_id": "561e51f16022b09d060041ab",
          "label": "Gruppe felt",
          "value": "Dette er et gruppe felt",
          "display_format": "text",
          "group": "Gruppe 1",
          "shared_key": "6dee999b6549d0cfd62e0ab390bc993e"
        },
        {
          "_id": "561e51f16022b09d060041ac",
          "label": "Gruppe text",
          "value": "Dette er et gruppe atribut",
          "display_format": "text",
          "group": "Gruppe 1",
          "shared_key": "623807a299f6ca4b0ebb980eeb69c87a"
        }
      ],
      "user": null
    }
  ],
  "original": null,
  "language": {
    "_id": "56167aae6022b0b9080041a7",
    "name": "Danish",
    "locale": "da_dk",
    "country": "Denmark"
  }
}
```

## <a name="/put/api/translations/id"></a> PUT /api/v1/translations/[id]
Update item of type with the given id 

### CURL

###### Request
```
curl -H "Authorization: Basic [TOKEN]" -X POST -d "_method=PUT&title=My new title&description=My new description" https://trapp.whitealbum.dk/api/v1/translations/C36AF818BE94E41C1F2C52133BF85F33
```

### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations/5DD845435D7B8BF6E9CDD6094BC79CF3');

$data = array('_method' => 'PUT', 'title' => 'My new title', 'description' => 'My new description');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));

$response = json_decode(curl_exec($ch));
```

#### Response
```json
{
  "language_id": "56167aae6022b0b9080041a7",
  "deadline": "2015-10-22 11:40:00",
  "original_entity_id": null,
  "application_id": 1,
  "title": "En aweseome titel 222334",
  "updated_at": "2015-10-14 13:00:33",
  "created_at": "2015-10-14 13:00:33",
  "current_state": "state-waiting",
  "translations": [
    {
      "id": "561e51f16022b09d060041ad",
      "locale": "nl_nl"
    },
    {
      "id": "561e51f16022b09d060041b3",
      "locale": "sv_se"
    }
  ],
  "edit_uri": "http://local.trapp.dk/translation/561e51f16022b09d060041a7/edit",
  "id": "561e51f16022b09d060041a7",
  "revisions": [
    {
      "_id": "561e51f16022b09d060041a8",
      "comment": "en kommentar",
      "revision_count": 0,
      "entity_id": "561e51f16022b09d060041a7",
      "state": "state-waiting",
      "user_id": null,
      "updated_at": "2015-10-14 13:00:33",
      "created_at": "2015-10-14 13:00:33",
      "fields": [
        {
          "_id": "561e51f16022b09d060041a9",
          "label": "Title",
          "value": "http://test.com/haha",
          "display_format": "image",
          "shared_key": "0992872de9ad3a5f86a3d3560b28f3b4"
        },
        {
          "_id": "561e51f16022b09d060041aa",
          "label": "Body",
          "value": "Dette er en lang body tekst....",
          "display_format": "text",
          "max_length": 1000,
          "shared_key": "7ad9a153ca32dcc98a046f03fc9fd872"
        },
        {
          "_id": "561e51f16022b09d060041ab",
          "label": "Gruppe felt",
          "value": "Dette er et gruppe felt",
          "display_format": "text",
          "group": "Gruppe 1",
          "shared_key": "6dee999b6549d0cfd62e0ab390bc993e"
        },
        {
          "_id": "561e51f16022b09d060041ac",
          "label": "Gruppe text",
          "value": "Dette er et gruppe atribut",
          "display_format": "text",
          "group": "Gruppe 1",
          "shared_key": "623807a299f6ca4b0ebb980eeb69c87a"
        }
      ],
      "user": null
    }
  ],
  "original": null,
  "language": {
    "_id": "56167aae6022b0b9080041a7",
    "name": "Danish",
    "locale": "da_dk",
    "country": "Denmark"
  }
}
```

## <a name="/delete/api/translations/id"></a> DELETE /api/v1/translations/[id]
Delete translation with the matching id

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" -X POST -d "&_method=delete" https://trapp.whitealbum.dk/api/v1/translations/C36AF818BE94E41C1F2C52133BF85F33
```

### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations/0F18B76A2294449455595381FC49D092');

$data = array('_method' => 'DELETE');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));

$response = json_decode(curl_exec($ch));
```

#### Response

```json
{
	"id": "C36AF818BE94E41C1F2C52133BF85F33",
	"deleted": true
}
```

## <a name="/get/api/states"></a> GET /api/v1/states
Get a list of states a translation can be in.

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" -X POST -d "&_method=delete" https://trapp.whitealbum.dk/api/v1/translations/C36AF818BE94E41C1F2C52133BF85F33
```

### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations/0F18B76A2294449455595381FC49D092');

$data = array('_method' => 'DELETE');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));

$response = json_decode(curl_exec($ch));
```

#### Response

```json
{
"total": 4,
"rows": [
	"state-waiting",
	"state-missing",
	"state-progress",
	"state-translated"
	]
}
```

## <a name="/get/api/languages"></a> GET /api/v1/languages
Get a list of states a translation can be in.

### CURL

###### Request

```
curl -H "Authorization: Basic [TOKEN]" -X POST -d "&_method=delete" https://trapp.whitealbum.dk/api/v1/translations/C36AF818BE94E41C1F2C52133BF85F33
```

### PHP

###### Request

```php
$ch = curl_init('https://trapp.whitealbum.dk/api/v1/translations/0F18B76A2294449455595381FC49D092');

$data = array('_method' => 'DELETE');

curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Basic ' . base64_encode(sprintf('%s:%s', [USERNAME],[SECRET])));
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));

$response = json_decode(curl_exec($ch));
```

#### Response

```json
{
"total": 4,
"rows": [
		{
		"_id": "55f0343345726eb0500041b1",
		"name": "Danish",
		"locale": "da_dk",
		"country": "Denmark"
		},
		{
		"_id": "55f0343345726eb0500041b2",
		"name": "English",
		"locale": "en_gb",
		"country": "United Kingdom"
		},
		{
		"_id": "55f0343345726eb0500041b3",
		"name": "Finnish",
		"locale": "fi_fi",
		"country": "Finland"
		},
		{
		"_id": "55f0343345726eb0500041b4",
		"name": "Swedish",
		"locale": "sv_se",
		"country": "Sweden"
		},
		{
		"_id": "55f0343345726eb0500041b5",
		"name": "Norwegian",
		"locale": "nb_no",
		"country": "Norway"
		},
		{
		"_id": "55f0343345726eb0500041b6",
		"name": "Dutch",
		"locale": "nl_nl",
		"country": "Netherlands"
		}
	]
}
```
## <a name="update_callback"></a> Update callback

After Posting an update to a translation, a post request will be made to the update_endpoint_uri set on the entity.
The system expects to recieve a repsonse with code 200 when a update has been succesfully recieved. If a request times out or fails, then the system will attempt to post again. A total of 3 attempts will be made before the update job is discarded. Below is an example of the request body that will be sent along with the request.

#### Request body

```json
{
   "_id":"55b8f5b2214f48da0900421f",
   "application_id":1,
   "publish_date":{
      "date":"2015-07-05 21:29:34.000000",
      "timezone_type":3,
      "timezone":"UTC"
   },
   "update_endpoint_uri":"http://runolfsdottir.com/",
   "language_id":"55b8f5b2214f48da090041b2",
   "original_entity_id":null,
   "updated_at":"2015-07-29 15:48:02",
   "created_at":"2015-07-29 15:48:02",
   "application":{
      "id":1,
      "display_name":"Translation",
      "username":"Translation",
      "site_code":"trapp",
      "app_code":"trans",
      "last_activity":"2015-07-29 15:43:18",
      "created_at":"2015-07-17 11:47:14",
      "updated_at":"2015-07-29 15:43:18",
      "roles":[
         {
            "role":"application_index",
            "app_id":1,
            "created_at":"2015-07-17 12:40:52",
            "updated_at":"2015-07-17 12:40:52"
         },
         {
           	... // Removed for simplicity
         }
      ]
   },
   "revisions":[
      {
         "_id":"55b8f5b2214f48da09004220",
         "revision_count":0,
         "comment":"Autem odit laudantium corrupti ut. Aut aut dolor nam illum fuga. Dolorum et fugit aut. Nemo voluptas tenetur dolorem sed.",
         "created_at":"2015-07-19 22:51:55",
         "state_id":"55b8f5b2214f48da090041b8",
         "user_id":"55b8f5b1214f48da090041af",
         "entity_id":"55b8f5b2214f48da0900421f",
         "updated_at":"2015-07-29 15:48:02",
         "field_ids":[
            "55b8f5b2214f48da09004221"
         ],
         "fields":[
            {
               "_id":"55b8f5b2214f48da09004221",
               "label":"Miss",
               "value":"Harum pariatur possimus ut itaque illum animi. Qui distinctio id deleniti provident quo. Et vel dolor sed et aspernatur reprehenderit et. Quia tenetur veritatis voluptates omnis.",
               "display_format":"text",
               "updated_at":"2015-07-29 15:48:02",
               "created_at":"2015-07-29 15:48:02",
               "revision_ids":[
                  "55b8f5b2214f48da09004220"
               ]
            }
         ],
         "state":{
            "_id":"55b8f5b2214f48da090041b8",
            "name":"On Hold",
            "description":"",
            "state_order":0
         },
         "user":{
            "_id":"55b8f5b1214f48da090041af",
            "name":"Miss Shanie Ward",
            "email":"paula.ullrich@gmail.com",
            "updated_at":"2015-07-29 15:48:01",
            "created_at":"2015-07-29 15:48:01"
         }
      },
      {
   			... // Removed for simplicity
 	  }
   ],
   "original":null,
   "language":{
      "_id":"55b8f5b2214f48da090041b2",
      "name":"Danish",
      "locale":"da_dk"
   }
}
```
