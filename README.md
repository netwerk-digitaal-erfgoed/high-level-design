# High-level functional design
Distributed network of digital heritage information

## Contents
- [Introduction](#introduction)
- [Status of this document](#status-of-this-document)
- [Audience](#audience)
- [Glossary](glossary.md)
- [Design considerations](considerations.md)
- [Building blocks](building-blocks.md)
- [Functions](functions.md)

## Introduction
This document outlines the _high-level functional design_ of the distributed network of digital heritage information. The document was commissioned by work program [Usable](http://www.den.nl/pagina/522/bruikbaar/) of the [Digital Heritage Network](https://www.rijksoverheid.nl/actueel/nieuws/2015/03/09/digitaal-erfgoed-zichtbaar-bruikbaar-en-houdbaar) (NDE), a partnership between cultural heritage institutions in the Netherlands.

The document describes the design of a new, cross-domain infrastructure for improving the usability of digital heritage information beyond the boundaries of archives, libraries, museums and research institutes. The design is _high-level_ because it describes the distributed network in general terms, not its details. The design is _functional_ because it describes the functionality of the distributed network, not for instance its organizational or technical considerations. Other types of designs — detailed, non-functional — will be made in the next steps of the program.

The document builds upon three other documents:

1. The [National Digital Heritage Strategy](https://www.government.nl/documents/reports/2015/07/02/national-digital-heritage-strategy) offers a perspective on developing a national, cross-sector infrastructure of digital heritage facilities.

1. The [Digital Heritage Reference Architecture](http://www.den.nl/standaard/412/Digitaal-Erfgoed-Referentie-Architectuur) (DERA 1.0; in Dutch) provides a coherent set of architectural goals, principles and requirements that enable cultural heritage institutions to work together in a shared infrastructure.

1. The position paper [Towards a distributed network of heritage information](https://github.com/netwerk-digitaal-erfgoed/general-documentation/blob/master/20160331%20Postion%20paper%20Towards%20a%20distributed%20network%20of%20heritage%20information.docx) (Word document) proposes an approach for connecting heritage information using state of the art concepts and technologies, such as Linked Data.

## Status of this document
This is a **working draft**. It may be updated at any time, evolving as we go. It is published for examination, experimental implementation and evaluation. Feedback is highly appreciated.

This document lays a — mostly theoretical — foundation for the future development of the infrastructure. In the upcoming months the ideas in this document are going to be applied and validated in various projects of cultural heritage institutions and related organizations. The outcomes will be used to strengthen the design.

## Audience
The intended audience of this document is threefold:

1. **IT strategists, architects, analysts and developers** from organizations that publish or use heritage information. For example: cultural heritage institutions, service portals or suppliers of IT solutions.

1. **Product owners and product managers** from organizations that publish or use heritage information. For example: cultural heritage institutions, terminology source providers or aggregator providers.

1. **Researchers** from the academic community. We hope that researchers will amend and improve the design in this document with insights from their own research findings.

The document assumes knowledge about topics such as aggregation, [web architecture](https://www.w3.org/TR/2004/REC-webarch-20041215/), [publishing data on the web](https://www.w3.org/TR/dwbp/) and [Linked Data](https://www.w3.org/standards/semanticweb/data).
