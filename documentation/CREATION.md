# Ontology Creation

GSQ does not currently have strong procedures for creating ontologies. At this stage, the best advice that can be given is:

### 1. Establish 
Establish the start of your ontology by copying at least the main `owl:Ontology` declaration and metadata from an existing GSQ ontology. You should also just exactly replicate the details of the publisher - GSQ - from existing ontologies unless, by the time you read this, they have changed.

### 2. Protege
Use [Protege](https://protege.stanford.edu/) to create the main structures of the ontology

### 3. Text editing
Edit the ontology source file by hand until it appears to match requirements for vlaidation
    * Use a text editor such as [Visual Studio Code](https://code.visualstudio.com) which has plugins for linine RDF validation

### 4. Validate
Validate the ontology as per [VALIDATION](VALIDATION.md)

You may expect to flip back and forth between Protege and hand-editing of RDF files while creating an ontology.
