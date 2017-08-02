# meiHead2HTML.xsl
## Input parameters:
in ediromOnline_params.xsl
```
<xsl:param name="lang"/>
<xsl:param name="base" as="xs:string"/>
<xsl:param name="pListKeyDelim">:</xsl:param>
```
## Imports:
ediromOnline_params.xsl
ediromOnline_functions.xsl
ediromOnline_metadata.xsl

## Following informations as HTML text are shown
### Datainformation
```
<xsl:value-of select="eof:getLabel('workDesc')"/>
```
Title:
```
<xsl:with-param name="key" select="local-name(.)"/>
```
Titlename:
```
<xsl:apply-templates select="mei:titleStmt"/>
```
Identifiers:
```
<xsl:if test="count(mei:identifier) gt 0">
	<xsl:element name="div">
	<xsl:call-template name="rendToProperty">
		<xsl:with-param name="key" select="string('identifier')"/>
	</xsl:call-template>
	<xsl:element name="div">
		<xsl:attribute name="class">value</xsl:attribute>
		<xsl:for-each select="mei:identifier">
			<xsl:call-template name="makeSubProperty">
				<xsl:with-param name="node" select="."/>
				<xsl:with-param name="key" select="@type"/>
			</xsl:call-template>
		</xsl:for-each>
		</xsl:element>
	</xsl:element>
</xsl:if>
```
Publication:
```
<xsl:with-param name="key" <xsl:apply-templates select="mei:pubStmt"/>
```
Classification:
```
<xsl:apply-templates select="mei:classification"/>
```
### Work Details
```
<xsl:with-param name="key" select="eof:getLabel('additionalMeta')"/>
```
Langauge, Edition:
```
<xsl:apply-templates select="mei:langUsage | mei:editionStmt" mode="plainCommaSep"/>                        
```
History:
```
<xsl:apply-templates select="mei:history"/>
```
### Musical Informations
```
<xsl:value-of select="eof:getLabel('musicalInfo')"/>
```
```
<xsl:element name="div">
	<xsl:attribute name="class">propertyList</xsl:attribute>
	<xsl:apply-templates select="mei:key | mei:meter | mei:perfMedium | mei:castList | mei:componentGrp"/>
</xsl:element>
```   
### Series
```  
<xsl:value-of select="eof:getLabel('series')"/>
```
```
<xsl:apply-templates select="mei:seriesStmt"/> 
```            
### Expressions:
```
<xsl:apply-templates select="mei:expressionList"/>
```
### Annotations
```
<xsl:apply-templates select="mei:notesStmt"/>
```

