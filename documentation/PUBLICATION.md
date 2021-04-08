# Ontology Publication

## 0. Create it
*Creating the ontology strictly outside the publication process. See [CREATION](CREATION.md) for more details for this step.*


## 1. Ontology Name
1. Verify that the ontology name reflects the ontology content.
2. Use only plain English words. 
3. If the ontology is about GSQ-only concepts, then the name must start with "GSQ",  
  e.g. `GSQ Geological Administrative Features Ontology`.
4. If the vocabulary is about universal concepts, then do not prefix with "GSQ",  
  e.g. `SWEET Geological Features Profile Ontology`.


## 2. Persistent URI
GSQ's ontologies, as well as their SKOS vocabularies and RDF datasets, are allocated persistent web addresses by the [Australian Government Linked Data Working Group (AGLDWG)](http://wwww.linked.data.gov.au). Each address allocated must be requested via the AGLDWG's catalogue: <http://catalogue.linked.data.gov.au>.

The AGLDWG publishes guidelines that describe approprate URIs:

* <https://github.com/AGLDWG/guidelines/>

Persistent URIs for all GSQ ontologies will be of the form:

* `https://linked.data.gov.au/def/` + `TOKEN`

Where:

* `linked.data.gov.au` 
  * is the AGLDWG's controlled namespace
* `/def/` 
  * is for "definitional" items which includes ontologies and vocabularies
* `TOKEN` 
  * is an identifier for the particular ontology
    * it must not contain unusual characters
    * pretty much: lowercase letters; numbers & "-"
    * it must, in some hard to pin down way, truely reflect the purpose of the ontology and be as unambiguous as possible
    * acronyms are sensible to use, e.g. "AGRIF" in <https://linked.data.gov.au/def/agrif> for the *Australian Government Records Interoperability Framework*

Existing persistent URIs for ontologies issued to GSQ are:

* <https://linked.data.gov.au/def/geofeatures> - Geological Features Ontology
* <https://linked.data.gov.au/def/geoadminfeatures> - GSQ Geological Administrative Features Ontology
* <https://linked.data.gov.au/def/borehole> - GSQ Borehole Profile
* <https://linked.data.gov.au/def/geou> - Geo Profile of QUDT Ontology

A URI should be requested when the ontology is being made.


## 3. Ontology metadata
The ontology must include one and only one `owl:Ontology` declaration.  

The `owl:Ontology` object in the ontology must be described in the form:  
```
<ontology-URI> a owl:Ontology ;
    skos:prefLabel "GSQ Geological Administrative Features Ontology"@en ;
    skos:definition "This ontology describes classes of geospatial feature relevant to the administrative duties of the Geological Survey of Queensland...."@en ;
    dcterms:created "2019-12-04"^^xsd:date ;
    dcterms:modified "2020-01-08"^^xsd:date ;
    dcterms:creator [
        ...
    ] ;
    dcterms:publisher <https://linked.data.gov.au/org/gsq> ;
    sdo:codeRepository <https://github.com/geological-survey-of-queensland/gsq-geoadmin-features-ont> ;

    [additional-properties] 
.
```

These properties are used by the [pyLODE program](https://github.com/RDFLib/pyLODE/) to create HTML documentation (see Step 6).

pyLODE documents the properties it undertands but the rule is that properties required by [AGOP](https://linked.data.gov.au/def/agop) must be used (see next step).


## 4. Validate the data
An ontology *must* pass validation before it may be published. GSQ ontologies must be valid according to the [Australian Government Ontology Profile (AGOP)](https://linked.data.gov.au/def/agop) which presents a series of validator files for this purpose.

See the instructions in [VALIDATION](VALIDATION.md) in this directory for details.


## 5. Generate HTML
An HTML document must be generated from an ontology's RDF source so that it can be presented to users for documentation. While any system for generating HTMl for an ontology may be used (there are lots), [pyLODE](https://github.com/RDFLib/pyLODE/) is specially configured for Australian Government ontologies.

See the pyLODE documentation. Ensure the AGOP profile is selected.


## 6. Host it
You ontology will need to be hosted publicly for a public URI to be able to resolve to it. Existing ontologies use GitHub for this purpose e.g.:

<https://linked.data.gov.au/def/borehole>  

is hosted in the repository  

<https://github.com/geological-survey-of-queensland/gsq-borehole-profile>

You will need to host, at least, the RDF & HTML files. You may host any other content with those files too: SHACL validators, images etc.


## 7. Have it reviewed
Ontology review should follow essentially the same process as vocabulary validation except that review cannot take place within the *vocabularies* repository since each ontology is hosted in its own repository.


## 8. Enable persistent URI

Once an ontology is approved by GSQ data managers for publication, the final step is to have the allocated AGLDWG URI redirect to it. This can be done by communicating to the AGLDWG that the ontology is ready. They will review and, if everything appears ok, point the requested URI to the ontology with the necissary redirection mechanics. They will send you a redirects infromation file for storage in the ontology repository.

At this point, the ontology will be published at `https://linked.data.gov.au/def/TOKEN` and absorbed into several ontology collectiosn by GSQ and the AGLDWG.
