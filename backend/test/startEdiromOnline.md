## Following services are called:
### 1. [getEditionURI.xql](../getEditionURI.md)

#### Examples for path definition:
return path same as $uri:
```
$uri :='xmldb:exist:///db/contents/testdata/edition.xml'
```
```
$uri :='/db/contents/testdata/edition.xml'
```
return path for first found edition file in database:
```
$uri :='db/contents/testdata/edition.xml'
```

```
$uri :=''
```
### 2. [getWorkID.xql](../getWorkID.md)
####  Conditions

1. First defined work will be returned.
2. xml:id attribute is mandatory in work in edition file.

### 3. [getPreferences.xql](../getPreferences.md)
#### Conditions
Same entry values in property file will be  overwritten with values from project file. 

#### Key definitions:
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
### 4. [getLanguageFile.xql](../getLanguageFile.md)
#### Key definitions:
for example show ../locale/edirom-lang-"$lang".xml

### 5. [getEdition.xql](../getEdition.md)
#### Conditions
xml:id for edition and editionName in edition file are optional.

### 6. [getWorks.xql](../getWorks.md)
#### Conditions:
Only first title for work will be returned/shown.

### 7. [getNavigatorConfig.xql](../getNavigatorConfig.md)
#### Conditions
Show items so than they ordered in edition file, no @sortNo attribute is used.

 [Example XML](TestXMLNavigatorConfig.md)

 [Generated HTML Result](TestXMLNavigatorConfigResult.md)

 [Navigator Screenshot](NavigatorConfig.md)


