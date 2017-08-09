# teiBody2HTML.xsl
### Input parameters:
```
<xsl:param name="lang">en</xsl:param>
<xsl:param name="base" as="xs:string"/>
<!-- OVERWRITE FOLLOWING TEI-PARAMS -->
<xsl:param name="numberHeadings">false</xsl:param>
<xsl:param name="autoHead">false</xsl:param>
<xsl:param name="graphicsPrefix"/>
<!-- END OVERWRITE TEI-PARAMS -->
<!-- FREIDI PARAMETER -->
<xsl:param name="textType"/>
```
## Show all information as HTML from tei:text/tei:body.

