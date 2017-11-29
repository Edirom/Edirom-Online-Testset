# getAnnotation
## Input parameters:
```
$edition := request:get-parameter('edition', '')

$uri := request:get-parameter('uri', '')

$target := request:get-parameter('target','')
```
## Import:
```
../xqm/source.xqm

../xqm/util.xqm

../xqm/annotation.xqm

../xqm/edition.xqm
```
## Following steps are executed
1. Returns a list of URIs addressed by an Annotation.
```
$docUri := substring-before($uri, '#')
$internalId := substring-after($uri, '#')
$doc := doc($docUri)
$annot := $doc/id($internalId)
$participants := annotation:getParticipants($annot)
```
in annotation.xqm
```
$ps := tokenize($anno/@plist, ' ')
$uris := distinct-values(for $uri in $ps return substring-before($uri,'#'))
```

2. Get a list of URIs addressed by an Annotation.
3. Get a string representing all Annotation categories.
4. In util.xqm get a comma separated list of document labels.
5. In source.xqm get a comma separated list of source sigla.
6. Return HTML fragment for Annotation.

## Example
### XML:
```
<annot type="editorialComment" xml:id="d1e518" plist="xmldb:exist:///db/contents/h-moll/neusatz.xml#measure-2-d4e27 xmldb:exist:///db/contents/h-moll/autograph.xml#edirom_measure_24f1c82e-43b8 xmldb:exist:///db/contents/h-moll/inselautograph.xml#edirom_measure_24f1c82e-43b8_insel">
	<title>1. Kyrie I, m. 19, Fl I, II</title>
	<p><rend rend="bold">A</rend>: with slur on 19/8–20/1</p>
	<ptr type="priority" target="#ediromAnnotPrio1"/>
	<ptr type="categories" target="#SLA"/>
</annot>
```
### HTML Result:
```
<div class="annotTip">
    <div class="metaBox">
        <div class="property priority">
            <div class="key">Priority</div>
            <div class="value">Priority 1</div>
        </div>
        <div class="property categories">
            <div class="key">Category</div>
            <div class="value">slurring in source A</div>
        </div>
        <div class="property sourceLabel">
            <div class="key">Sources</div>
            <div class="value">Full Score, A Autograph Score, A´ Facsimile Edition 1924</div>
        </div>
        <div class="property sourceSiglums">
            <div class="key">Source</div>
            <div class="value"></div>
        </div>
    </div>
    <div class="contentBox">
        <h1>1. Kyrie I, m. 19, Fl I, II</h1>
        <p xmlns:mei="http://www.music-encoding.org/ns/mei"><span class="bold" style="font-weight: bold;">A</span>: with slur on 19/8–20/1</p>
    </div>
</div>
```





