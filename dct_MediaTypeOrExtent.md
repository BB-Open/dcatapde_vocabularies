# dct:MediaTypeOrExtent

Is used as dct:format and dct:mediaType of dcat:Distribution

**No Controlled vocabulary on [dcat-ap.de](http://www.dcat-ap.de/def) available**

There is an interesting discussion on dct:format vs. dct:MediaType in DCAT-AP:
https://joinup.ec.europa.eu/discussion/pr22-remove-dcatmediatype-and-only-use-dctformat

Also there is a thread with some pointers about the IANA standards in RDF
https://www.ietf.org/mail-archive/web/media-types/current/msg00685.html

What we learned:
* DCAT-AP.de http://www.dcat-ap.de/def/dcatde/1_0/implRules.pdf states
> DCAT-AP sieht zur Kennzeichnung des Dateiformats vor, dass für
> dct:format das MDR authority file und für
> dcat:mediaType die IANA Media Types zu verwenden sind
* There are more data formats than the IANA list covers. E.g. INSPIRE

We will screen grab the IANA list and publish a SKOS file [here](.iana_codes.skos).

The MDR authority file can be found here http://publications.europa.eu/mdr/resource/authority/file-type/skos/filetypes-skos.rdf
