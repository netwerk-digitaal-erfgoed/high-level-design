# Glossary
The glossary explains the key terms used in the design of the distributed network of digital heritage information. The definitions are going to be discussed with partners in the cultural heritage community in order to connect to existing glossaries.

## Contents
- [Collection](#collection)
- [Cultural heritage institution](#cultural-heritage-institution)
- [Cultural heritage object](#cultural-heritage-object)
- [Dataset](#dataset)
- [Dataset profile](#dataset-profile)
- [Object](#object)
- [Object description](#object-description)
- [Object profile](#object-profile)
- [Organization](#organization)
- [Organization profile](#organization-profile)
- [Provenance](#provenance)
- [Provider](#provider)
- [Term](#term)
- [Term description](#term-description)
- [Terminology source](#terminology-source)

## Collection
A group of cultural heritage objects to be seen, studied, or kept together. For example: the paintings of a museum, the books of a library or the records of an archive. A collection has meaning to its maintainers and users; it deals, for instance, with a certain topic. A collection can be available in one or more datasets, suitable for processing by the distributed network.

## Cultural heritage institution
An organization that curates a collection of cultural heritage objects. For example: an archive, a library, a museum or a research institute that maintains a cultural heritage collection.

## Cultural heritage object
A heritage asset, physical or born-digital, curated or made available by a cultural heritage institution. For example: a book, an article in an electronic journal, an archive of historical records, a monument or a painting.

## Dataset
A selection of data, published or curated by a single agent, and available for access or download in one or more formats<sup>[1](#fn1)</sup>. For example: a dataset can contain object descriptions, term descriptions or links between two datasets ("alignments").

## Dataset profile
The metadata of a dataset describing its characteristics, both administrative, descriptive and structural. For example: the identifier, title, curating organization, language, terms or provenance information of a dataset.

## Object
An item of interest to cultural heritage, physical or born-digital. An object can be anything, depending on the curating institution: it can be a cultural heritage object or stem from a cultural heritage object. For example: a monument (such as a fortification) or the parts of a monument (such as the gates, towers or walls of a fortification). Or a magazine, the articles in the magazine or the paragraphs in the article of a magazine. Or a set of archival records or an annotation by an expert about these records. An object typically has an object description.

## Object description
The metadata of an object, both administrative, descriptive and structural. For example: the title, date of creation, terms or provenance information of an object. An object description is maintained in a _collection management system_.

## Object profile
A small subset of the metadata of an object containing its URI and the URIs of the terms that characterize the object, the datasets to which the object belongs and other, related objects (for instance, the parts of a multi-volume book).

## Organization
A body that represents a collection of people organized together into a community or other social, commercial or political structure<sup>[2](#fn2)</sup>. For example: a cultural heritage institution, an aggregator provider or a terminology source provider.

## Organization profile
The metadata of an organization describing its characteristics, both administrative, descriptive and structural. For example: the identifier, name or address of an organization.

## Provenance
A statement of any changes in ownership and custody of the resource since its creation that are significant for its authenticity, integrity and interpretation. The statement may include a description of any changes successive custodians made to the resource<sup>[3](#fn3)</sup>.

## Provider
An organization that contributes data to the distributed network of heritage information. For example: a cultural heritage institution, aggregator provider or terminology source provider.

## Term
A word or phrase used to describe a thing or to express a concept<sup>[4](#fn4)</sup>. For example: the name of a person or place, the title of a work or the subject of a painting. A term typically is part of an object description; a term supports the object's discoverability for users.

## Term description
The metadata of a term, both administrative, descriptive and structural. For example: the identifier, label, language, scope notes or place in hierarchy of a term. A term description is maintained in a _terminology management system_.

## Terminology source
A structured list of terms. For example: a classification system of subjects, a thesaurus of persons or an authority list of places or time periods. A terminology source has a controlled vocabulary; its terms are predefined and approved by the maintainer of the source. A terminology source is maintained by a _terminology source provider_.

## _References_
* <a name="fn1">1</a>: This definition is based on [DCAT's](https://www.w3.org/TR/vocab-dcat/#Class:_Dataset). However, the DCAT term "collection" is omitted intentionally: "collection" in this design is a collection of cultural heritage objects, not a collection of data.
* <a name="fn2">2</a>: https://www.w3.org/TR/2014/REC-vocab-org-20140116/#org:Organization
* <a name="fn3">3</a>: http://dublincore.org/documents/2012/06/14/dcmi-terms/?v=terms#provenance
* <a name="fn4">4</a>: https://en.oxforddictionaries.com/definition/term
