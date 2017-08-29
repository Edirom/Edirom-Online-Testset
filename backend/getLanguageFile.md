# getLanguageFile.xql
### Input parameters:
```
$lang := request:get-parameter('lang', '')

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

load language file form:
```
$file := doc(concat('../locale/edirom-lang-', $lang, '.xml'))
```

load language project file from:
```
$projectFile := doc(edition:getLanguageFileURI($edition, $lang))
```
in edition.xqm get language file path defined in edition file:
```
doc($uri)//edirom:language[@xml:lang eq $lang]/string(@xlink:href)
```

return language and version from language project file:
```
'lang: "', $file/langFile/lang/text(), '",',
'version: "', $file/langFile/version/text(), '",',
```
return keys and values as names from both language files:

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
### Key definitions:
for example show ../locale/edirom-lang-"$lang".xml

