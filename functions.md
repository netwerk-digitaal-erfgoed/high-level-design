# Functions
This section outlines the primary functions of the cross-domain building blocks. The functions are a refinement of the descriptions in section [Building blocks](building-blocks.md). A function is described only insofar it interacts with another building block.

## Contents
- [Registry](#registry)
    - [Register organization profiles](#register-organization-profiles)
    - [Register dataset profiles](#register-dataset-profiles)
    - [Register object profiles](#register-object-profiles)
    - [Expose profiles](#expose-profiles)
    - [Exchange profiles with distributed registries](#exchange-profiles-with-distributed-registries)
- [Network of Terms](#network-of-terms)
    - [Retrieve dataset profiles from Registry](#retrieve-dataset-profiles-from-registry)
    - [Load terms in datasets](#load-terms-in-datasets)
    - [Search terms in datasets of external terminology sources](#search-terms-in-datasets-of-external-terminology-sources)
    - [Search terms by collection manager](#search-terms-by-collection-manager)
    - [Propose terms by collection manager](#propose-terms-by-collection-manager)
    - [Exchange terms with distributed networks of terms](#exchange-terms-with-distributed-networks-of-terms)
- [Knowledge Graph](#knowledge-graph)
    - [Retrieve profiles from Registry](#retrieve-profiles-from-registry)
    - [Verify relations in profiles](#verify-relations-in-profiles)
    - [Typify objects descriptions](#typify-objects-descriptions)
    - [Retrieve related terms from Network of Terms](#retrieve-related-terms-from-network-of-terms)
    - [Search for relations by browser](#search-for-relations-by-browser)
    - [Exchange relations with distributed knowledge graphs](#exchange-relations-with-distributed-knowledge-graphs)
- [Browser](#browser)
    - [Select identifiers from Knowledge Graph](#select-identifiers-from-knowledge-graph)
    - [Retrieve term descriptions from terminology management systems](#retrieve-term-descriptions-from-terminology-management-systems)
    - [Retrieve object descriptions from collection management systems](#retrieve-object-descriptions-from-collection-management-systems)
    - [Translate user queries to term identifiers](#translate-user-queries-to-term-identifiers)

## Registry

### Register organization profiles
The Registry keeps a list of the organizations that contribute data to the distributed network of heritage information. For example: cultural heritage institutions, aggregator providers or terminology source providers. Each organization has a distinct organization profile, containing for instance its name and identifier. This allows users of the Registry to identify an organization unambiguously.

A maintainer of an organization is responsible for maintaining the profile of his organization. There are two ways of doing this. First, the maintainer can use his registration system — such as a collection management system or terminology management system — to make changes to his profile; the registration system then updates the profile in the Registry. Second, the maintainer can logon to the administration interface of the Registry and make changes there.

The Registry assigns identifiers to the organization profiles. These identifiers can then be used for retrieving the profiles. For example, the identifier of museum A can look like this: `http://registry.nde.nl/organizations/a`. If a user looks up this URI, the Registry returns the profile of A. If an organization has its own organization identifier — persistent and dereferencable — it can be added to the profile so as to signify the relation between both.

### Register dataset profiles
The Registry keeps a list of the datasets that are available to the distributed network of heritage information. Each dataset has a distinct dataset profile. The profile contains administrative, descriptive and structural data about the dataset. For example: identifier, title and curating organization. This allows users of the Registry to identify a dataset unambiguously. The actual content of a dataset, however, is not part of the profile. Instead, the profile contains a reference — a URL — to the location where the content can be found.

Currently we distinguish four dataset profile types:

1. A [profile for a dataset of term descriptions](#register-profiles-of-datasets-of-term-descriptions)
1. A [profile for a dataset of alignments](#register-profiles-of-datasets-of-alignments)
1. A [profile for a dataset of object descriptions](#register-profiles-of-datasets-of-object-descriptions)
1. A [profile for a dataset of annotations](#register-profiles-of-datasets-of-annotations)

Each type will be explained hereafter.

A maintainer of an organization is responsible for maintaining the profiles of his datasets. There are two ways of doing this. First, the maintainer can use his registration system — such as a collection management system or terminology management system — to make changes to his profiles; the registration system then updates the profiles in the Registry. Second, the maintainer can logon to the administration interface of the Registry and make changes there.

The Registry assigns identifiers to the dataset profiles. These identifiers can then be used for retrieving the profiles. For example, the identifier of dataset B of organization A can look like this: `http://registry.nde.nl/organizations/a/datasets/b`. If a user looks up this URI, the Registry returns the profile of B. If an organization has its own dataset identifiers — persistent and dereferencable — these can be added to the dataset profiles so as to signify the relation between both.

#### Register profiles of datasets of term descriptions
The Registry maintains the profiles of datasets of term descriptions. A dataset contains the descriptions of terms from a terminology source, such as [Iconclass](http://www.iconclass.org/) or [WO2 Thesaurus](http://oorlogsbronnen.nl/wo2-thesaurus).

The dataset may include alignments with other terms. For example: the terms in the Erfgoedthesaurus refer to their equivalents in DBpedia. A terminology source may also use a separate dataset and corresponding dataset profile for describing the alignments between terms (see function [Register profiles of datasets of alignments](#register-profiles-of-datasets-of-alignments)).

A maintainer of a terminology source may register multiple versions of his dataset in the Registry. Each version corresponds to a dataset and has its own dataset profile. For example: if there are two officially supported versions of RKDartists&, dataset profile A describes version one and dataset profile B describes version two. Both profiles may refer to different locations where the term descriptions in the datasets can be found.

#### Register profiles of datasets of alignments
The Registry maintains the profiles of datasets of alignments. A dataset contains the relations between terms that are described in different datasets, possibly from different terminology sources. For example: a relation between person A in dataset B and person C in dataset D. This type of dataset is also known as a _linkset_.

A dataset of alignments can be created by either a maintainer of a terminology source or a maintainer of the Network of Terms. The corresponding dataset profile contains provenance information to denote the origin of the alignments.

#### Register profiles of datasets of object descriptions
The Registry maintains the profiles of datasets of object descriptions. A dataset contains the descriptions of objects from a cultural heritage institution. For example: the dataset _Nationale Bibliografie_ ("National Bibliography") comprises the publications of the National Library of the Netherlands.

A collection manager may register as many or as few dataset profiles as he sees fit, reflecting the collection strategy of his institution. For example: one organization can register one profile for its entire collection of objects whereas another organization can register separate profiles for each object type in its collection, such as books, magazines and newspapers.

#### Register profiles of datasets of annotations
The Registry maintains the profiles of datasets of annotations. Annotations enrich the descriptions of cultural heritage objects.

For example: an expert at an institution can annotate objects by adding historical context information. The resulting set of annotations can be registered in the Registry in its own dataset profile. Another example: an editor of a cultural heritage app can write child-friendly summaries about objects. The set of summaries can be registered in the Registry in a dataset profile. Another example: an end user of a service portal can compose his own collection or mash-up of his favorite paintings via the website of an institution, such as the Rijksmuseum's [Rijksstudio](https://www.rijksmuseum.nl/nl/rijksstudio). This kind of _user-generated content_, too, can be registered in the Registry.

A dataset profile of annotations contains provenance information. This allows users — such as service portals or end users — to trace the origin of the dataset and to decide upon its usefulness in a particular context.

The design of annotations and their datasets and dataset profiles is not finished yet. Further details are going to be added to this document later on.

### Register object profiles
The Registry keeps a list of object profiles that are available to the distributed network of heritage information. These profiles are provided by cultural heritage institutions or their aggregator providers.

An object profile consists of four types of identifiers. First, the identifier of the object. Second, the identifier of the dataset to which the object belongs. Third, the identifiers of the terms — if any — that describe the object. Fourth, the identifiers of objects — if any — that have a relationship with the object, such as the preliminary studies of a painting or the volumes of a book. Note that other types of information that are typically part of an object's description, such as its type, title or date of creation, are not part of an object profile.

A collection manager of a cultural heritage institution is responsible for maintaining the profiles of his objects. Note that an object profile is a subset of an object description, not a new record that needs separate maintenance.

A change to an object profile can be registered in the Registry in either of two ways. First, by notifying the Registry instantly, when the change occurs. This ensures the topicality of information; the Registry has the current state of the object's profile. Second, by notifying the Registry periodically, for example once a day. The Registry will then batch process the changes. The best approach for registering changes needs further investigation and will be added to this document later on.

Contrary to an organization profile and a dataset profile, the Registry does not assign an identifier to an object profile. An object profile has its own identifier, issued by the cultural heritage institution or its aggregator provider. This identifier is persistent and dereferencable. For example, an identifier of an object profile can look like this: `https://www.rijksmuseum.nl/nl/collectie/RP-P-OB-79.671`. Alternatively, a Handle can be used: `http://hdl.handle.net/10934/RM0001.COLLECT.446245`. If a user looks up this URI, the provider's system returns the object's description, expressed in RDF.

Ideally there is only one object profile of an object in the Registry, identified by the object's identifier. But this will not always be the case. If a collection management system of a cultural heritage institution cannot issue URIs for its objects, the institution's aggregator will do this. An institution can, however, deliver its object descriptions to multiple aggregators, in which case each aggregator assigns its own URIs to the descriptions and sends these to the Registry. Consequently the Registry has multiple object profiles for one object.

### Expose profiles
The primary task of the Registry is to register organization, dataset and object profiles. It leaves the task of using this information to other building blocks. For example: the Network of Terms wants to get the profiles of datasets of term descriptions from the Registry so that it can collect the terms from terminology sources. Another example: a service portal wants to get the profiles of datasets of object descriptions so that it can present the datasets in its user interface, akin to CKAN. The Registry exposes its information by supporting two features.

First, by returning profiles of organizations and datasets. These profiles are maintained by the Registry and can be retrieved using their Registry-assigned identifier. For example: `http://registry.nde.nl/organizations/a` or `http://registry.nde.nl/organizations/a/datasets/b`.

Second, by synchronizing profiles of organizations, datasets and objects. A building block can get the profiles from the Registry by making an initial synchronization request. The Registry, in turn, delivers its current profiles. The building block can stay in sync with the Registry by requesting a change list of the profiles that were added, changed or removed since its previous request. The Registry, in turn, delivers the corresponding profiles.

### Exchange profiles with distributed registries
The Registry can be a distributed service, consisting of multiple registries instead of one comprehensive service. These registries must be able to exchange organization, dataset and object profiles with each other. The design of this distributed service is not finished yet. Further details are going to be added to this document later on.

## Network of Terms

### Retrieve dataset profiles from Registry
The Network of Terms exposes the term descriptions from selected terminology sources. These sources are registered in dataset profiles in the Registry. The Network obtains these profiles by retrieving (a change list of) the profiles from the Registry periodically, for example once a day. It then processes each profile.

First, if a dataset profile is new or has been updated, the Network of Terms records that the term descriptions in the corresponding dataset are eligible for (re-)loading (see function [Load terms in datasets](#load-terms-in-datasets)). Second, if a dataset profile is no longer available in the Registry — for instance: it was deleted by its maintainer — the Network of Terms removes all of its references to this profile and the corresponding term descriptions.

### Load terms in datasets
The Network of Terms, after retrieving a dataset profile from the Registry, loads the term descriptions in the dataset.

The Network of Terms first addresses the dataset using the access information specified in the dataset profile, such as the location of the dataset and the method for requesting the dataset. The access information depends on the capabilities of the terminology management system. For example: one dataset can be retrieved by downloading a data dump and another dataset can be retrieved by querying the system's repository via a protocol such as OAI-PMH.

The term descriptions in a dataset are expressed in RDF and standard vocabularies, such as SKOS. The Network of Terms performs basic validation to ensure the well-formedness of the structure of the dataset. It does not, however, make corrections. If a dataset, for whatever reason, is ill-formed, it's the responsibility of the maintainer of the terminology source or alignments to fix it and publish a valid dataset.

The Network of Terms then processes the term descriptions. It saves a subset of each description in its data store, consisting of the information that is required for finding and understanding the term, such as type and label.

The Network of Terms periodically checks and processes the datasets again, for example once a day. This ensures that the Network has current term descriptions. First, if a description had been added to or updated in the dataset, the Network adds or updates the description too. Second, if a description is no longer available in the dataset, the Network of Terms removes this description. It can happen that users of the Network of Terms — notably the maintainers of cultural heritage institutions — use references to the obsolete term. It's the responsibility of the maintainer of the terminology source to inform his users, for example by requesting them to use alternative references, and the responsibility of the terminology management system to return an appropriate error if an obsolete term description is requested.

### Search terms in datasets of external terminology sources
The Network of Terms exposes terms from a variety of terminology sources, but it only loads terms from national sources. Loading terms from external sources — for instance: DBpedia — would make the Network large and unwieldy. Instead, the Network acts as a _mediator_ for such sources. This allows a user to query the Network for a term in an external source. Invisible to the user, the Network routes the user's query to the source, addressing the source's own services for finding term descriptions. The Network then returns the search result to the user.

The design for searching external terminology sources is not finished yet. Further details are going to be added to this document later on.

### Search terms by collection manager
When describing an object in his collection management system, a collection manager of a cultural heritage institution is searching for terms that define the object adequately. The collection manager can then use these terms to enrich or annotate the object description.

Ideally the collection management system of the collection manager searches for terms by querying the terminology sources registered in the Registry. This, however, can be challenging: each collection management system must then implement the APIs of the terminology sources and keep track of changes in the Registry, such as the addition of new and the removal of old terminology sources.

The Network of Terms therefore supports the collection management system with this search by offering a unified interface to the different terminology sources. This interface allows a collection manager to search for terms. First, by finding the terms that match the collection manager's query. For example: all terms with a specific status (e.g. no candidate terms) or type (e.g. only "persons") or stemming from a specific terminology source (e.g. Nederlandse Thesaurus van Auteursnamen or DBpedia) or organization (e.g. Koninklijke Bibliotheek). Second, by auto-completing the collection manager's query. For example: all terms of which the label starts with "Ams", possibly limited to a specific type (e.g. only "places") or one or more terminology sources (e.g. Erfgeothesaurus).

The Network of Terms returns specific information per term description. First, descriptive information for understanding the term, such as type, preferred and alternative label, scope notes and relations. Second, administrative information, such as the candidate status of the term. If a collection manager needs more information about a term, such as the birthdate of a person or the geographic coordinates of a place, the collection management system can get this information from the corresponding terminology source by dereferencing the URI of the term. The collection management system decides what must be done with the resulting information, for example by disposing it after use or by saving it in its data store for the performance of future use.

Note that the Network of Terms merely facilitates a collection manager in finding terms. The Network, however, does not warn the collection manager of changes. For example: it may happen that the label of a term alters; this may or may not alter its meaning ("semantic drift"). Even though the identifier of the term remains the same, the new label may or may not be fitting to the collection manager. It's the responsibility of the maintainer of the terminology source to inform his users about changes.

### Propose terms by collection manager
A collection manager of a cultural heritage institution may not find the term he's looking for when describing an object in his collection management system. For example: an artist may not have been included in RKDartists& or a subject may be missing from Iconclass. The collection manager should then be able to propose a term — a _candidate term_ or _provisional term_ — to a terminology source.

Ideally the collection manager contacts the maintainer of the terminology source directly, using the procedures set by the source. This, however, can be challenging; a collection manager must know these procedures.

The Network of Terms therefore supports the collection manager in proposing a term. The collection manager can send the information about a candidate term to the Network of Terms. This information includes for example the terminology source to which the term should be added, the label of the term and a motivation. The Network of Terms then passes this information to the appropriate terminology source. What happens next depends on the source. For instance, the source can register the candidate term for review by its maintainer. The source can also generate and return a provisional identifier for this term — a URI. The collection manager of the cultural heritage institution can save this identifier with the object's description and continue his work.

Meanwhile, the maintainer of the terminology source reviews the candidate term and either rejects or approves it. He then notifies the proposer — the collection manager — about his decision. On approval the maintainer of the terminology source adds the term to the dataset of the source. The Network of Terms subsequently loads the dataset, including the description of the newly added term. The maintainer of the institution can then search for the term and use it in his object descriptions.

Note that the Network of Terms supports candidate terms only insofar a terminology source has an API to which the candidate terms can be proposed automatically. If a source doesn't have an API — for instance: candidate terms can only be proposed manually — the collection manager must contact the terminology source himself.

### Exchange terms with distributed networks of terms
The Network of Terms can be a distributed service, consisting of multiple networks of terms instead of one comprehensive service. These networks of terms must be able to exchange term descriptions with each other. The design of this distributed service is not finished yet. Further details are going to be added to this document later on.

## Knowledge Graph

### Retrieve profiles from Registry
The Knowledge Graph contains the relations between organizations, datasets, objects and terms. These relations originate from the profiles in the Registry. The Knowledge Graph obtains these by retrieving (a change list of) the profiles from the Registry periodically, for example once a day. It then processes each profile.

First, if a profile is new, the Knowledge Graph gets the identifiers in the profile and stores these in its data store. For example: an organization profile includes the identifier of the organization (`http://registry.nde.nl/organizations/a`); a dataset profile includes the identifier of the license (`http://standaarden.overheid.nl/owms/terms/cc0.rdf`); an object profile includes the identifier of the object (`https://www.rijksmuseum.nl/nl/collectie/RP-P-1910-2115`) and its terms (`http://www.iconclass.org/rdf/?notation=45K1`).

Second, if a profile has been updated, the Knowledge Graph gets the identifiers in the profile. New identifiers in the profile are added to the data store and identifiers that no longer exist in the profile are removed from the data store.

Third, if a profile is no longer available in the Registry — for instance: it was deleted by its maintainer — the Knowledge Graph removes all references to this profile.

As a result the Knowledge Graph has the most recent identifiers used in the latest version of the profiles. The Knowledge Graph can then connect these and create a network of relations, ready for querying by browsers or service portals.

### Verify relations in profiles
The relations in the Knowledge Graph tell how organizations, datasets, objects and terms are connected. The integrity of these relations is therefore of utmost importance. Even though maintainers at cultural heritage institutions and terminology sources providers are responsible for managing the relations in their profiles, the Knowledge Graph also verifies the relations in order to safeguard their integrity.

First, if a profile has been synchronized by the Knowledge Graph with the Registry, it validates the containing relations, such as the identifiers of organizations, datasets, objects and terms. If this validation fails — for instance: an identifier is not a valid URI — the Knowledge Graph rejects the relation. If this validation succeeds, the Knowledge Graph accepts the relation provisionally.

Second, the Knowledge Graph performs a deep validation of the relations. This is a deferred process that happens asynchronously. The Knowledge Graph fetches the resource to which a relation points, such as an object or term description, by dereferencing its URI. If this validation fails — for instance: the object or term description does not exist — the Knowledge Graph rejects the relation. If this validation succeeds, the Knowledge Graph accepts the relation.

Third, the Knowledge Graph periodically validates the accepted relations again, for example once a month. This rerun of the deep validation ensures that the relations remain up-to-date, independent of the changes that were — or weren't — provided by the maintainer of a cultural heritage institution or terminology sources provider. For example: if an object or term description, for whatever reason, no longer exists, making its identifier a _dead link_, the Knowledge Graph rejects the relation. Note that a description may not exist temporarily, for instance due to system maintenance. A relation is therefore rejected only if the description is unavailable for several times in a row. The maintainer of the Knowledge Graph can gather the rejected relations periodically and contact the maintainers of the concerning cultural heritage institutions or terminology sources providers.

### Typify objects descriptions
The Knowledge Graph contains the relations of objects, taken from the object profiles in the Registry. The types of the objects, however, are not part of the profiles, but are helpful to users when querying the Knowledge Graph: a user typically does not want to request all object descriptions, regardless of what they represent, but an intersection of object descriptions, matching one or more types. For example: publications, not buildings.

To enable these queries the Knowledge Graph determines the type of each object description. There are two ways of doing this. First, by using the type information in the profile of the dataset to which an object belongs. This profile can denote that all of the objects in its dataset are of a particular type. Second, by extracting the object's type from its description, for instance after dereferencing its identifier and verifying its relations (see function [Verify relations in profiles](#verify-relations-in-profiles)). The best approach for determining the type needs further investigation and will be added to this document later on.

The Knowledge Graph typifies object descriptions on a high-level by mapping specific types to generic types. For example: if a collection manager of a cultural heritage institution has typified an object as "[Clipping](http://dbpedia.org/resource/Clipping_(publications))", the Knowledge Graph typifies it as "[Written Work](http://dbpedia.org/ontology/WrittenWork)". This allows users to query the Knowledge Graph without having to know the exact types used by institutions. If, however, a user needs to have the exact types, it can collect the object descriptions and determine the types itself (see function [Retrieve object descriptions from collection management systems](#retrieve-object-descriptions-from-collection-management-systems)).

### Retrieve related terms from Network of Terms
The Knowledge Graph contains two types of terms. First, terms that appear in profiles from the Registry. These terms have been assigned by maintainers while describing their organizations, datasets and objects. Second, terms that are related to the terms from the profiles. These related terms support users in finding information. For example: if a user is looking for object descriptions using the geographical term "_Den Haag_", the Knowledge Graph also returns object descriptions that use the city's alternative name, "_‘s-Gravenhage_".

Related terms are not part of the profiles. The Knowledge Graph gathers these by querying the Network of Terms. For each term used in a profile the Knowledge Graph requests its equivalent, associated and hierarchical terms, independent of the originating terminology or alignment sources.

The extent to which the Knowledge Graph should retrieve related terms needs further investigation. Principally the Knowledge Graph gathers the directly related terms of a term, but it may be useful to also gather indirectly related terms. For example: the broader term of the broader term of a term, such as the province ("_Zuid-Holland_") of the municipality ("_Gemeente Den Haag_") of the city of Den Haag.

### Search for relations by browser
The Knowledge Graph helps the browser of a service portal to find relations between organizations, datasets, objects and terms. For this purpose a browser can query the Knowledge Graph with a set of conditions. In reply the Knowledge Graph returns the relations matching the conditions.

For example: if a portal wants to present heritage information related to the Dutch colony of _Dutch East Indies_, the portal's browser can request the identifiers of objects that match specific organization, dataset and/or term criteria. For instance, the objects must belong to organizations Museum Bronbeek and National Archives, must be part of datasets that are available under the license CC0 and must have the terms "_Java_" or "_Sumatra_".

The Knowledge Graph can be queried in real-time, instantly giving answers to questions of users. However, this type of querying is unlikely: the Knowledge Graph only returns identifiers, not the metadata of organizations, datasets, objects or terms. The metadata must be retrieved from their respective sources, such as collection management systems and terminology management systems. This makes real-time querying a considerable challenge to browsers. Instead, the Knowledge Graph will typically be queried periodically, for example once a day. This allows a browser to collect the metadata of the matching identifiers in a deferred process.

### Exchange relations with distributed knowledge graphs
The Knowledge Graph can be a distributed service, consisting of multiple knowledge graphs instead of one comprehensive service. These knowledge graphs must be able to exchange relations with each other. The design of this distributed service is not finished yet. Further details are going to be added to this document later on.

## Browser

### Select identifiers from Knowledge Graph
A browser helps a service portal to select the identifiers of organizations, datasets, objects and terms that are related to the topic of the portal. These identifiers can then be used for retrieving information about the organizations, datasets, objects and terms.

For example: a service portal wants to present object descriptions from cultural heritage institutions that are part of the [Netwerk Zuiderzeecollectie](http://www.zuiderzeemuseum.nl/nl/657/vrienden/nieuwsnetwerk-zuiderzeecollectie-van-start-in-enkhuizen/?id=5015). The portal's browser selects the identifiers of objects that belong to these institutions by querying the Knowledge Graph, using the identifiers of the institutions, registered in the organization profiles of the Registry, as input. This query returns a set of matching object identifiers.

Another example: a service portal wants to present the cultural heritage institutions that have information about the topic _Dutch East Indies_. The portal's browser first selects the terms that are related to this topic by querying the Knowledge Graph. This query returns a set of terms, originating from various terminology sources, that have a relation with the topic — for instance: the term "_Nederlands-Indië_" in DBpedia, the narrower term "_Java_" in the Brinkman Thesaurus or the related term "_KNIL_" in WO2 Thesaurus. The browser then selects the curating institutions by querying the Knowledge Graph, using the identifiers of the terms as input. This query returns a set of matching organization identifiers.

A browser typically saves the identifiers found by the Knowledge Graph in its own data store. It queries the Knowledge Graph again periodically, for example once a week. This ensures that the browser uses current identifiers: if identifiers are added to or removed from the Knowledge Graph, the browser can update its identifiers accordingly.

The design for selecting identifiers is not finished yet. For example: instead of selecting object identifiers directly from the Knowledge Graph, it could be an option to select these indirectly, from their sources. A browser then queries the Knowledge Graph using term identifiers as input. In reply the Knowledge Graph returns a set of dataset profiles of which the datasets contain object descriptions referencing the term identifiers. The browser subsequently queries the datasets for retrieving the object descriptions. This approach could benefit the scalability of the distributed network. Further details will be added to this document later on.

### Retrieve term descriptions from terminology management systems
The Knowledge Graph has limited information about terms from terminology sources: it does not have the full descriptions of terms, such as birthdates of persons or geographic coordinates of places. If a service portal needs these descriptions for serving its users, the portal's browser can collect the descriptions at their source, the terminology management system. It does so by dereferencing the URIs of the term descriptions. A terminology management system then returns the description for each URI, expressed in RDF and term vocabularies such as SKOS.

The browser typically saves the term descriptions in its own data store, principally for performance. For example: it can build a faceted index by indexing the labels and identifiers in the descriptions.

The browser retrieves the term descriptions again periodically, for example once a week. This ensures that the browser uses current descriptions: if the maintainer of a terminology source updates a description — for instance: by correcting the birthdate of a person — the browser can update its description accordingly.

The browser acts upon the response of a terminology management system when requesting a term description. For example: a description that no longer exists triggers the system to yield a specific status ([410 Gone](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.11)). This status causes the browser to remove the description from its data store.

### Retrieve object descriptions from collection management systems
The Knowledge Graph has limited information about objects from cultural heritage institutions: it does not have the full descriptions of objects, such as their title, summary or date of creation. If a service portal needs these descriptions for serving its users, the portal's browser can collect the descriptions at their source, the collection management system of the institution (or its aggregator). It does so by dereferencing the URIs of the object descriptions. A collection management system then returns the description for each URI, expressed in RDF and a domain-specific or domain-independent vocabulary.

The browser, based on the input of the service portal, determines which object descriptions are usable and which are not. For example: a service portal may wish to use only objects of a specific type, such as a book, monument or painting. Or a service portal may wish to use only objects that have an image or that were created in a certain time period. The browser subsequently filters object descriptions, keeping what it wants.

The browser typically saves the remaining objects descriptions in its own data store, principally for performance. For example: it can build a full-text index by indexing the words in the descriptions, such as titles or summaries. This allows a user of a service portal to find heritage information not only by using controlled terms but also by using free-form words (which is especially useful for object descriptions that lack terms, such as archival records).

The browser retrieves the object descriptions again periodically, for example once a week. This ensures that the browser uses current descriptions: if a collection manager updates a description — for instance: by changing the summary of a book — the browser can update its description accordingly.

The browser acts upon the response of a collection management system when requesting an object description. For example: a description that no longer exists triggers the system to yield a specific status ([410 Gone](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.11)). This status causes the browser to remove the description from its data store.

### Translate user queries to term identifiers
A browser keeps the term descriptions of terminology sources (see function [Retrieve term descriptions from terminology management systems](#retrieve-term-descriptions-from-terminology-management-systems)). The browser can use these descriptions to support a user of a service portal in finding specific information.

First, by translating a user's query to identifiers of terms in terminology sources. For example: if a user searches for "_NSB_" or "_Nationaal-Socialistische Beweging_", the browser looks for term descriptions with these labels. The browser may then find a term description in the WO2 Thesaurus with identifier `https://data.niod.nl/WO2_Thesaurus/2244`. Another example: if a user searches for "_Slag Mookerheide_", the browser looks for term descriptions with these labels. The browser may then find a term description in DBpedia with identifier `http://nl.dbpedia.org/resource/Slag_op_de_Mookerheide`.

Second, by searching for heritage information that uses the identifiers. For example: the browser can query its collection of object descriptions and find the descriptions that contain the identifiers. For identifier `https://data.niod.nl/WO2_Thesaurus/2244` this may result in newspapers of or archival records about the NSB. For identifier `http://nl.dbpedia.org/resource/Slag_op_de_Mookerheide` this may result in paintings of or books about the battle.

Contrary to a full-text search, this search for identifiers allows a user to find information with greater accuracy and relevancy. A full-text search yields all resources in which the user's search terms somehow occur, whereas an identifier search yields only those resources to which the identifier was explicitly assigned by a collection manager.
