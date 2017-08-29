# getPreferences.xql
### Input parameters:
```
$mode := request:get-parameter('mode', '')

$edition := request:get-parameter('edition', '')
```
### Import:
```
../xqm/edition.xqm
```
### Following steps are executed
```
$mode = 'json'
```

load file property form:
```
$file := doc('../prefs/edirom-prefs.xml')
```
load project property file from:
```
$projectFile := doc(edition:getPreferencesURI($edition))
```
in edition.xqm get property file path defined in edition file:
```
doc($uri)//edirom:preferences/string(@xlink:href)
```

return informations from both property files:

```
for $entry in $file//entry
return
	concat('"', $entry/string(@key), '":"', $entry/string(@value), '"')
```

```
for $entry in $projectFile//entry
return
	concat('"', $entry/string(@key), '":"', $entry/string(@value), '"')
```
### Conditions
Same entry values in property file will be  overwritten with values from project file. 

### Key definitions:
key="application_language"
key="annotation_layout"
key="image_prefix"
key="edition_path"

#### plugins: 
concat "plugin_" + name
for example:
```
key="plugin_textView" value="../exist/rest/db/contents/js/TextView.js"
```

#### XQuery:
for example:
```
key="data/xql/getLinkTarget.xql"
value="../exist/rest/db/contents/xql/getLinkTarget.xql"
```


