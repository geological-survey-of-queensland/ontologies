## 6. Validate the Class Hierarchy
It is beyond this short checklist to detail all the check sensible for ensuring a good ontology however it's likely that the ontology will present a class hierarchy and domain experts but with limited OWL ontology skills should check that the class hierarchy makes *prima facie* sense to their domain expertise. 

Class hierarchy testing can usually be done quite well by simple asking: "Is each member of a subset also a member of the superset?". For example, if the hierarchy has `<Mammal> rdfs:subClassOf <Animal>`, is every `<Mammal>` truly and `<Animal>` (yes)!


## 7. Validate Class metadata
Ensure that each class in the ontology is documented in a manner similar to the Concepts in a vocabulary, that is with a:

* a class statement
    * either `<...> rdf:type owl:Class ;` or `prefix:ClassName a owl:Class ;` 
    * by convention, Class URIs ID parts start with a capital and use CamelCase, e.g. `.../LithodemicFeature`
* subclass declarations
    * if the class is a subclass of any other (they almost always are), then it should include `<...> rdfs:subClassOf <...> ;`
    * it may be a sub class of multiple other classes
* a name
    * `skos:prefLabel` - and Classes conventionally use *proper* case (all words start with a capital)
* a definition
    * a `skos:definition`, if the class is defined in this ontology, as opposed to being reused from another ontology
    * Aristotelian definitions are best: "A X is a type of Y that is.." e.g., for <Mammal> "A Mammal is an Animal that is characterized by a covering of hair on the skin and, in the female, milk-producing mammary glands for nourishing the young"

e.g. (from the *GSQ Geological Administrative Features Ontology*)

```
geoaf:Block rdf:type owl:Class ;
    rdfs:subClassOf geoaf:AdministrativeFeature ;
    skos:definition "A Block is an administrative division of the State of Queensland that is used for tenure management. A Block is defined as five minutes of latitude by five minutes of longitude. Blocks are grouped by 1:1,000,000 map sheet areas, the names of which provide the containing Blocks with a four letter prefix (e.g. Clermont 1:1,000,000 provides CLER). Each sheet area contains 3456 Blocks, with the Blocks numbered between 1 and 3456 inclusive. A Block is divided into 25 Sub-Blocks."@en ;
    skos:prefLabel "Block" .
```
