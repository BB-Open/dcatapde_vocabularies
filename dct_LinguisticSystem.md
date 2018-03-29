# dct:LinguisticSystem

Is used as dct:language of dcat:Catalog, dcat:Dataset and dcat:Distribution.

**No Controlled vocabulary on [dcat-ap.de](http://www.dcat-ap.de/def) available**

What we learned:
* DCAT-AP.de http://www.dcat-ap.de/def/dcatde/1_0/implRules.pdf states

> Diese Eigenschaft bezieht sich auf die Sprache, welche in der textuellen Beschreibung der Metadaten der dem
> Katalog zugehörigen Datenstrukturen Verwendung findet (z.B. Titel, Beschreibungen usw.). Diese Eigenschaft kann wiederholt werden,
> falls die Metadaten in verschiedenen Sprachen zur Verfügung stehen.

Our position:

* The definition of dct:language http://udfr.org/docs/onto/dct_language.html states:
    > Recommended best practice is to use a controlled vocabulary such as RFC 4646.
* The definition of dct:LinguisticSystem:
    > Examples include written, spoken, sign, and computer languages.

We have the strong feeling that dct:LinguisticSystem is not the correct class to implement dct:Language. Dct:LinguisticSystem describes in which ways (Knots, bits, spoken words, noises) language
is expressed and transportet. But dct:Language is in the interpretation of DCAT-AP.de simply the set of languages in which the metadata e.g. Title/Description is stored.

How to proceed:

If we follow the interpretation of DCAT-AP.de and simply interpret dct:Language as a Language (en, de, it etc.) then a second question arises about the controlled vocabulary to use.

The DCAT-AP Implementation guide states https://lists.w3.org/Archives/Public/public-dwbp-wg/2015Jul/att-0010/DCAT-APimplementationguide.pdf

> dct :LinguisticSystem
> Here it is recommended to use 2 or 3 character codes provided in ISO 3166 https://www.iso.org/iso-3166-country-codes.html

​Govdata.de uses http://publications.europa.eu/resource/authority/language in alpha-3 (3 letter) notation. The SKOS file can be found here
http://publications.europa.eu/mdr/resource/authority/language/skos/languages-skos.rdf .

But be warned. The SKOS file is in a mixture of alpha-2 and alpha-3 notation:

> <skos:Concept rdf:about="http://publications.europa.eu/resource/authority/language/ENG">

> <skos:inScheme rdf:resource="http://publications.europa.eu/resource/authority/language"/>

> <at:authority-code>ENG</at:authority-code>

>  <at:op-code>ENG</at:op-code>

>  <atold:op-code>ENG</atold:op-code>

>  <dc:identifier>ENG</dc:identifier>

>  <skos:prefLabel xml:lang="bg">английски</skos:prefLabel>

>  <skos:prefLabel xml:lang="cs">angličtina</skos:prefLabel>

>  <skos:prefLabel xml:lang="da">engelsk</skos:prefLabel>

>  <skos:prefLabel xml:lang="de">Englisch</skos:prefLabel>

>  <skos:prefLabel xml:lang="el">αγγλικά</skos:prefLabel>

Please notice the xml:lang alpha-2 notation for the definition of an alpha-3 concept.

