# skos:Concept

Is used as dcat:Dataset->dcat:theme (dct:type), and dct:LicenseDocument->dct:type
and dcat:Distribution->adms:status, and foaf:Agent->dct:type.

### skos:Concept is used in DCAT-AP.de in many ways (of which some are IMHO no skos:concepts at all). So please refer to the different usage paragraphs and do not expect a homogenous solution.

### dcat:Dataset->dcat:theme

What we learned:

DCAT-AP.de http://www.dcat-ap.de/def/dcatde/1_0/spec/specification.pdf states for dcat:Dataset->dcat:theme
> Diese Eigenschaft bezieht sich auf die der
Datenstruktur zugewiesenen Kategorie. Mit
einer Datenstruktur können mehrere
Kategorien assoziiert sein. Es MUSS das
MDR data theme des Publication Offices
verwendet werden.

The autorative Controlled Vocabulary for dcat:Dataset->dcat:theme can be found at http://publications.europa.eu/mdr/resource/authority/data-theme/skos/data-theme-skos.rdf

### dcat:Dataset->dct:type

What we learned:
* DCAT-AP.de http://www.dcat-ap.de/def/dcatde/1_0/spec/specification.pdf states for dcat:Dataset->dcat:theme

> Diese Eigenschaft bezieht sich auf den Typ
der Datenstruktur. Zur Gruppierung von
linearen und nichtlinearen
Reihen/Kollektionen ist gemäß DCAT-
AP.de Konventionenhandbuch eine
Gruppenstruktur vom Typ „Kollektion
anzulegen, die auf die gruppierten
Datensätze mittels „Weitere Version“
(dct:hasVersion) verweist.
Alle gruppierten Datensätze verweisen
dann mittels "ist Version von“
(dct:isVersionOf) auf die  URI (http://dcat-ap.de/def/datasetTepes/collection) dieser
logischen Klammer.
Feldübergreifende Beispiele und das Zusammenspiel mit der Eigenschaft
hasVersion sind im Konventionenhandbuch
dokumentiert.

The URI quoted is not available on the server so we assume that http://dcat-ap.de/def/datasetTypes/collection is the correct URI and
http://www.dcat-ap.de/def/datasetTypes/1_0.rdf the owl file with only one class (lines stripped):

>   <owl:Ontology rdf:about="http://dcat-ap.de/def/datasetTypes">
  </owl:Ontology>

>  <owl:Class rdf:about="http://dcat-ap.de/def/datasetTypes/collection">
    <rdfs:label xml:lang="de">Datenreihe</rdfs:label>
    <rdfs:comment xml:lang="de">Zeitreihen und sonstige linear und nicht linear angeordnete Elemente einer Reihe als Kollektionen von Datenstrukturen.</rdfs:comment>
    <rdfs:subClassOf rdf:resource="http://dcat-ap.de/def/datasetTypes"/>
  </owl:Class>
</rdf:RDF>

Our commentary:

**We are pretty sure that the rdfs:subClassOf statement is not correct. rdfs:subClassOf relates two classes but owl:Ontology is not a class.**
If the idea of this statement is meant as a backreference in owl backreferences to the ontology are implicit. Also Class identifiers should be camel case.

**Also we do not understand why a new class has to be founded for dct:type.** The Collection class of the controlled vacabulary
DCMITYPE http://dublincore.org/documents/dcmi-type-vocabulary/ for dct:type already comes with dct:isVersionOf and dct:hasVersion and does suffice for the usage proposed.

**Also neither the Ontology http://dcat-ap.de/def/datasetTypes nor the http://purl.org/dc/dcmitype/Collection has any relation to skos:Concept**
It would  be more consistent to form a new dcat entity Collection with the same prominence as dcat:CatalogRecord.

### dct:LicenseDocument->dct:type

What we learned:
> Diese Eigenschaft bezieht sich auf den
Typ einer Lizenz., z.B. “Public Domain”
oder „royalties required“
http://purl.org/adms/licencetype/

Our commentary:

There is a controlled vocabulary for the licenses to be used on http://dcat-ap.de see [skos:LicenseDocument](./dct_LicensDocument.md) but the dct:type of the individual licenses does not comply with the vocabulary
http://purl.org/adms/licencetype/.

> <owl:Class rdf:about="http://dcat-ap.de/def/licenses/official-work">

> <rdfs:label xml:lang="de">officialWork</rdfs:label>

> ...

> **<dct:type rdf:resource="offen"/>**



 **So the controlled vocabulary for the licenses is virtually useless for the classification of the licenses. Therefore the implementer has to come up with its own classification of the license types according to http://purl.org/adms/licencetype/ which breaks the authority of http://dcat-ap.de.**


### dcat:Distribution->adms:status

Use the controlled vocabulary http://purl.org/adms/status/1.0

### foaf:Agent->dct:type

Use this vocabulary  http://purl.org/adms/publishertype/, but with the following regulation:
> Es wird lediglich eine Auswahl aus den ADMS Begriffen erlaubt: lokal, regional, national, supranational
