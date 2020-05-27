# Ontology Validation

## 1. Validation rules and files

Ontology validation is performed using GSQ-created ontology rules formulated using the [SHACL constraint language](https://www.w3.org/TR/shacl/). The rules are presented as *SHACL* validation language files - known as 'shapes' - in the folder [shapes/](../shapes/).

These SHACL shapes files test for syntax correctness and patterns within RDF graphs, in this case an RDF graph describing an ontology.

All GSQ and perhaps eventually Qld/Aust. government requirements for ontology publication *must* be characterised as *shapes* within files in this directory or else the rules are not known with precision.

For an ontolology to be assessed as valid (in contrast to being assessed for sensibility & appropriateness - SME tasks!), it must pass all the validators in the [shapes/](../shapes/) directory.

The validators relevant for GSQ ontologies are:

1. [Australian Government Ontology Profile (AGOP)](http://linked.data.gov.au/def/agop) validators
    * these validators check for basic ontology metadata, the formulation of agents (people, orgs) related to the ontology and basic Class and Property elements such as titles & descriptions
2. GSQ validators
    * these validators go beyond AGOP's to look for things GSQ deems necissary in its ontologies
    * e.g. the publisher of a GSQ ontology must be GSQ, not any other government organisation, as per AGOP


## 2. Performing validation

There are several options for testing a given ontology with the relevant shape files:

### 1. pySHACL

Use the [pySHACL tool](https://github.com/RDFLib/pySHACL) on the command line to validate the ontology RDF document according to each shape file in the directory in turn - any order is fine. Something like this:

```
~$ pyshacl -s ontology-metadata.shape.ttl geoadminfeatures.ttl
```
This command will check that the *GeoAdmin Features Ontology*, contained within the file `geoadminfeatures.ttl` is validated against the *Ontology Metadata Shape* contained within the file `ontology-metadata.shape.ttl`.

Read the pySHACL documentation on how to install pySHACL or to use it online.

### 2. ChekaBox

This tool is not yet available but, when it is, it will present a web page interface into which you can copy 'n paste ontology content for validation. Under the hood it uses pySHACL. Use of this tool will mean you don't have to install or run anything on your local PC.


## 3. Results
Validation - by pySHACL, ChekaBox or other SHACL-based validator - will report errors if present which the violating part of the data too, so they can usually be read and addressed. 

All SHACL validators also validate RDF syntax before graph pattern validating, so if they are used, a separate RDF syntax validator is not needed.