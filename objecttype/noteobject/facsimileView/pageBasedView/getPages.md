# getPages.xql
## Input parameters:
```
$uri := request:get-parameter('uri', '')
```
## Show following data informations
### For MEI-Format
For each mei:surface:

1. Facsimile:
```
let $graphic := $surface/mei:graphic[@type='facsimile']
```

2. ID:
```
$surface/string(@xml:id)
```

3. Path:
```
$graphic/string(@target)
```

4. Name:
```
$surface/string(@n)
```

5. Width:
```
$graphic/string(@width)
```

6. Height:
```
$graphic/string(@height)
```
                
### For TEI-Format
For each tei:surface:

1. Facsimile:
```
let $graphic := $surface/tei:graphic[1]
```

2. ID:
```
$surface/string(@xml:id)
```

3. Path:
```
$graphic/string(@url)
```

4. Name:
```
$surface/string(@n)
```

5. Width:
```
replace($graphic/string(@width), 'px', '')
```

6. Height:
```
replace($graphic/string(@height), 'px', '')
```
## Example
XML:
``` 
<surface xml:id="edirom_surface_d9e3eead-c3a9" n="I">
	<graphic target="h-moll/source_P_180/P_180_002.jpg" xml:id="graphic_facsimile-P_180_002" type="facsimile" width="772" height="1200" label="002"/>
</surface>
``` 
JSON Result/Output: 
```            
id: "edirom_surface_d9e3eead-c3a9", path: "h-moll/source_P_180/P_180_002.jpg", name: "I", width: "772", height: "1200"}
```
                







