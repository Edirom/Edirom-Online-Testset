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
Title:
```
<xsl:value-of select="./titleStmt/title[1]/text()"/>
```
Subtitle:
```
<xsl:apply-templates select="mei:titleStmt">
	<xsl:with-param name="sub" tunnel="yes"/>
</xsl:apply-templates>
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
<xsl:apply-templates select="./mei:pubStmt"/>
```
Physical Description:
```
<xsl:apply-templates select="mei:physDesc"/>
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
<xsl:apply-templates select="./key | ./meter | ./perfMedium | ./castList | mei:componentGrp"/>
```
### Series
```
<xsl:value-of select="eof:getLabel('series')"/>
```
```
<xsl:apply-templates select="./seriesStmt"/>
```
### Classification
```
<xsl:apply-templates select="mei:classification"/>
```
### Item List
```
<xsl:apply-templates select="mei:itemList"/>
```
### Annotations
```
<xsl:apply-templates select="mei:notesStmt"/>
```

