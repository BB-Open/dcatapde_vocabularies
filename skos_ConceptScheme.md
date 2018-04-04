# dct:ConceptScheme

Used as dcat:Catalog->dcat:ThemeTaxonomy

What we learned:

The implementation guide states http://www.dcat-ap.de/def/dcatde/1_0/spec/specification.pdf :
> Der zu verwendende Wert für diese Eigenschaft ist
die URI des Vokabulars selbst - die des Konzept
Schemas, nicht die URIs aus dem Konzept des
Vokabulars.
http://publications.europa.eu/resource/authority/data-theme

Our commentary:

The cardinality of this field is * so there can be more than one categorisation scheme for a catalog.

Imagine a simple example:

A catalog X or a collection X may consist of many datasets A, B, C, D, .. Q with potential concepts from two different concept schemes DT (the required data-theme scheme) and OT an other scheme.

For example A has the concept DT.foo
A->(DT.foo)
and B has the concept DT.bar
B->(DT.bar)
and C has both concepts.
C->(DT.bar, DT.foo)
..
Q->(DT.bar)

X consists of all the datasets
X\[A,B,C, ...,Q\]

it follows that X has concepts from DT concept scheme only
X -> (DT).

But if only one dataset gets a concept from a different scheme e.g.
A->(DT.foo, OT.test)
all catalogs, collections including A have to change their concept schemes list.

**But a dataset does not know the catalogs it participates. So there has to be some backtracking to gain the information to which catalogs belongs the dataset to. And while formulating your backtracking algorithm please keep in mind that catalogs can contain catalogs**
OK let us assume that the backtracking works and the catalog get its X -> (DT, OT) scheme list.

Now the data is tranfered to the next node in the DCAT-AP.de network and due to a minor syntactically error (which has nothing to do with concepts at all. imagine an utf8-decoding error)
dataset A cannot be parsed and is neglected. Then we find catalog X with the information that it contains concepts of
a skos:conceptScheme OT for which not a single concept exists in the whole data base. Ergo: We have inconsistent data.

On the other hand if all the datasets were harvested and stored in an arbitrary data base system it will be an easy query to find the concepts of all datasets of e.g. a particular catalog of interest.
And due to the nature of skos each skos concept knows to which concept scheme it belongs. So it is an easy task to derive the true content of the field dcat:ThemeTaxonomy even if it does not exist.

And even if it exists what use does it have? If one wants to be sure that the data is consitent one has to verify the concepts.
In fact our application PKAN works perfectly well without using dcat_schemeTaxonomy at all.
