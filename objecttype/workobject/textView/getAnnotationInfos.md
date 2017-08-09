# getAnnotationInfos.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')

request:get-parameter('edition', '')
```
## Show following data informations
### Categories
```
for $category in $annots/mei:ptr[@type="categories"]/replace(@target, '#', '')
```
#### id
$category in Categories
#### name
```
(collection(eutil:getPreference('edition_path', request:get-parameter('edition', '')))//id($category))[1]/mei:name/text()
```
### Priorities
```
for $priority in $annots/mei:ptr[@type="priority"]/replace(@target, '#', '')
```
#### id
$priority in Priorities
#### name
```
(collection(eutil:getPreference('edition_path', request:get-parameter('edition', '')))//id($priority))[1]/mei:name/text()  ```
            

