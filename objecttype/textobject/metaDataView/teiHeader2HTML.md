# teiHeader2HTML.xsl
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
#### All Titel with optional attributes @type, @xml:lang
```
<xsl:template match="tei:title">
	<xsl:call-template name="makeProperty">
		<xsl:with-param name="node" select="."/>
		<xsl:with-param name="key" select="if(@type)then(concat(local-name(), '_', @type))else(local-name())"/>
	</xsl:call-template>
</xsl:template>
```

#### All autors with optional attributes @xml:id
```
<xsl:template match="tei:author">
	<xsl:call-template name="makeProperty">
		<xsl:with-param name="node" select="."/>
	</xsl:call-template>
</xsl:template>
```
#### Information form respStmt statements in form:
```
<resp>:<name>
```
     
#### All dates
```
<xsl:template match="tei:date">
	<xsl:call-template name="makeProperty">
		<xsl:with-param name="node" select="."/>
	</xsl:call-template>
</xsl:template>
```
#### Umfang
call ediromOnline_metadata.xsl makeSubProperty function: 
```
<xsl:template match="tei:extent" mode="bibl">
	<xsl:call-template name="makeSubProperty">
		<xsl:with-param name="node" select="."/>
	</xsl:call-template>
</xsl:template>
```
    
#### Publication
call ediromOnline_metadata.xsl makeProperty function, show distributor and address: 
```
<xsl:template match="tei:publicationStmt">
	<xsl:call-template name="makeProperty">
		<xsl:with-param name="node" select="."/>
	</xsl:call-template>
</xsl:template>
```
#### seriesStmt
### Quellenbeschreibung
call ediromOnline_metadata.xsl makeSection function:
```
<xsl:template match="tei:fileDesc | tei:sourceDesc | tei:profileDesc">
	<xsl:call-template name="makeSection"/>
</xsl:template>
```

### Angaben zu der Codierung
call ediromOnline_metadata.xsl makeSection function:
```
<xsl:template match="tei:encodingDesc">
	<xsl:call-template name="makeSection"/>
</xsl:template>
```

### Revisionen der Datei
List with:
Änderungen + Name:
```
<xsl:element name="div">
	<xsl:attribute name="class">value</xsl:attribute>
		<xsl:value-of select="concat(@who, ': ')"/>
	<xsl:apply-templates/>
</xsl:element>
```

Datum: 
```
<xsl:if test="@when">
	<xsl:element name="span">
		<xsl:attribute name="class">date</xsl:attribute>
		<xsl:value-of select="./@when"/>
	</xsl:element>
</xsl:if>
```

