# Ontology Validation

Ontology validation is perfurmed using GSQ-created ontology rules formulated using the [SHACL constraint language](https://www.w3.org/TR/shacl/). The rules are given within files in this folder: `ontology-metadata.shape.ttl` etc.

There are several options for testing a given ontology with the relevant SHACL files but the main way is to use the [pySHACL tool](https://github.com/RDFLib/pySHACL) on the command line, something like this:

```
~$ pyshacl -s ontology-metadata.shape.ttl geoadminfeatures.ttl
```
This command will check that the *GeoAdmin Features Ontology*, contained within the file `geoadminfeatures.ttl` is validated against the *Ontology Metadata Shape* contained within the file `ontology-metadata.shape.ttl`.

For any given GSQ ontology, all the shapes starting with `ontology-` must be run to validate the metadata, the classes and so on.

Read the pySHACL documentation on how to install pySHACL or to use it online.
