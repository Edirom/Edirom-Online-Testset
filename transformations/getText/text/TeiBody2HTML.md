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
## Following informations as HTML text are shown
Show all information from tei:text/tei:body.

