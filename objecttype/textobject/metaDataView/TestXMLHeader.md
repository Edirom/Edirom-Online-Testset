```
<TEI xmlns="http://www.tei-c.org/ns/1.0">
<teiHeader>
	<fileDesc>
		<titleStmt>
			<title>One Title</title>
			<title type="alt">Alt Title</title>
			<title type="sub">Sub Title</title>
			<title xml:lang="de" type="reg">Reg Title</title>
			<author xml:id="Author_1_id">Author_1</author>
			<author>Author_2</author>
			<respStmt>
				<resp>Copy_1</resp>
				<name>Author_3</name>
			</respStmt>
			<respStmt xml:id="Copy_2_id">
				<resp>Copy_2</resp>
				<name>Author_4</name>
			</respStmt>
		</titleStmt>
		<editionStmt>
			<edition>
				<date>2014-10-01</date>
				<date>2014-10-02</date>
			</edition>
		</editionStmt>
		<extent>400 Seiten</extent>
		<publicationStmt>
			<distributor>Oxford Text Archive.</distributor>
			<address>
				<addrLine>Oxford University Computing Services,</addrLine>
				<addrLine>13 Banbury Road,</addrLine>
				<addrLine>Oxford OX2 6RB,</addrLine>
				<addrLine>UK</addrLine>
			</address>
		</publicationStmt>
		<seriesStmt>
			<title>Machine-Readable Texts for the Study of Indian Literature</title>
			<respStmt>
				<resp>ed. by</resp>
				<name>Jan Gonda</name>
			</respStmt>
			<biblScope unit="volume">1.2</biblScope>
			<idno type="ISSN">0 345 6789</idno>
		</seriesStmt>
		<notesStmt>
			<note>Brief notes on the text are in a supplementary file.</note>
		</notesStmt>
		<sourceDesc>
			<biblStruct>
				<monogr>
					<editor>Foner, Philip S.</editor>
					<title>The collected writings of Thomas Paine</title>
					<imprint>
						<pubPlace>New York</pubPlace>
						<publisher>Citadel Press</publisher>
						<date>1945</date>
					</imprint>
				</monogr>
			</biblStruct>
		</sourceDesc>
	</fileDesc>
	<encodingDesc>
		<projectDesc>
			<p>Originally prepared for use in the production of a series of old-spelling concordances in 1968, this text was extensively checked and revised for use during the editing of the new Oxford Shakespeare (Wells and Taylor, 1989).</p>
		</projectDesc>
		<samplingDecl>
			<p>Editorial notes in the Foner edition have not been reproduced. </p>
			<p>Blank lines and multiple blank spaces, including paragraph indents, have not been preserved. </p>
		</samplingDecl>
		<refsDecl xml:id="ASLREF">
			<cRefPattern matchPattern="(\S+) ([^.]+)\.(.*)" replacementPattern="#xpath(//div1[@n='$1']/div2/[@n='$2']//lb[@n='$3'])">
			<p>A reference is created by assembling the following, in the reverse order as that listed here: 
				<list>
					<item>the <att>n</att> value of the preceding <gi>lb</gi>
					</item>
					<item>a period</item>
					<item>the <att>n</att> value of the ancestor <gi>div2</gi></item>
					<item>a space</item>
					<item>the <att>n</att> value of the parent <gi>div1</gi></item>
				</list>
			</p>
			</cRefPattern>
		</refsDecl>
		<editorialDecl>
			<correction status="high"  method="silent">
				<p>The following errors in the Foner edition have been corrected:
					<list>
						<item>p. 13 l. 7 cotemporaries contemporaries</item>
						<item>p. 28 l. 26 [comma] [period]</item>
						<item>p. 84 l. 4 kin kind</item>
						<item>p. 95 l. 1 stuggle struggle</item>
						<item>p. 101 l. 4 certainy certainty</item>
						<item>p. 167 l. 6 than that</item>
						<item>p. 209 l. 24 publshed published</item>
					</list>
				</p>
			</correction>
			<normalization>
				<p>No normalization beyond that performed by Foner, if any. </p>
			</normalization>
			<quotation marks="all">
				<p>All double quotation marks rendered with ", all single quotation marks with apostrophe. </p>
			</quotation>
			<hyphenation eol="none">
				<p>Hyphenated words that appear at the end of the line in the Foner edition have been reformed.</p>
			</hyphenation>
			<stdVals>
				<p>The values of <att>when-iso</att> on the <gi>time</gi> element always end in the format <val>HH:MM</val> or <val>HH</val>; i.e., seconds, fractions thereof, and time zone designators are not present.</p>
			</stdVals>
			<interpretation>
				<p>Compound proper names are marked. </p>
				<p>Dates are marked. </p>
				<p>Italics are recorded without interpretation. </p>
			</interpretation>
		</editorialDecl>
		<classDecl>
			<taxonomy xml:id="lcsh">
				<bibl>Library of Congress Subject Headings</bibl>
			</taxonomy>
			<taxonomy xml:id="lc">
				<bibl>Library of Congress Classification</bibl>
			</taxonomy>
		</classDecl>
	</encodingDesc>
	<profileDesc>
		<creation>
			<date>1774</date>
		</creation>
		<langUsage>
			<language ident="en" usage="100">English.</language>
		</langUsage>
		<textClass>
			<keywords scheme="#lcsh">
				<term>Political science</term>
				<term>United States -- Politics and government —cRevolution, 1775-1783</term>
			</keywords>
			<classCode scheme="#lc">JC 177</classCode>
		</textClass>
	</profileDesc>
	<revisionDesc>
		<listChange>
			<change n="P2.2" who="#BZ">
				<date when="2015-08-28">2015-08-28</date>
				<p>Anlegen der Datei und Ersterfassung</p>
			</change>
			<change who="#LDB">
				<date when="2015-08-31">2015-08-28</date>
				<p>Anlegen der Datei und Ersterfassung Test</p>
			</change>
		</listChange>
	</revisionDesc>
</teiHeader>
<text>
	<body>
		<div></div>
	</body>
</text>
</TEI>
```


