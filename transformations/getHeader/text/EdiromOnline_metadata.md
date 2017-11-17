# ediromOnline_metadata.xsl
## makeSection function
create section title:
```
<xsl:element name="h1">
	<xsl:value-of select="eof:getLabel(local-name())"/>
</xsl:element>
```
create content:
```
<xsl:for-each select="@*">
	<xsl:call-template name="makeProperty">
		<xsl:with-param name="key" select="local-name(.)"/>
	</xsl:call-template>
</xsl:for-each>
```
## makeProperty function


