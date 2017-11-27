## backend/getWorkID.md
### Major: 
Error handling if xml:id in work in edition file not exist.

## backend/getNavigatorConfig.xql
### Minor: 
Items show so than they ordered in edition file, no @sortNo attribute is used.

## objecttype/textobject/metaDataView/teiHeader2HTML.xsl
### Minor:
Formatting of titles is different;
Formatting komplett;
Not all Information were shown
(for details: s. testdata in this directory)

## objecttype/workobject/facsimileView/pageBasedView/annotationsMenu/schowHideAnnotations.md
### Minor:
All Annotations for workobject ere returned although id for selected page as input parameter is exists. (Is is correct?)

## objecttype/workobject/facsimileView/pageBasedView/goTo
### Major: 
not work: no measure is shown

## objecttype/workobject/facsimileView/pageBasedView/goTo/getMovementsOrNumber.md
### Minor:
Return second zone id in surface. (Is is correct?)
```
($mei/id($movementId)//mei:measure)[1]/string(@facs)
```

## objecttype/workobject/facsimileView/measureBasedView/annotationsMenu
### Prio 1: 
show Annotations not work: not annotations are shown

## objecttype/workobject/facsimileView/measureBasedView/partSelection
### Prio 1: 
no work. (or bad example?)

