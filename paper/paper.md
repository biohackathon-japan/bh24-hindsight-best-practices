---
title: 'BioHackJP24 report: Best practices for providing RDF data revisisted'
title_short: 'BioHackJP24 #24: Hingsight for better RDF'
tags:
  - data provision
  - RDF
  - PubChem
  - UniProt
  - SPARQL
  - OWL
  - Reasoning
  - Examples
  - Documentation
  - FAIR
authors:
  - name: First Author
    affiliation: 1
  - name: Jerven Bolleman
    orcid: 0000-0000-0000-0000
    affiliation: 2
affiliations:
  - name: First Affiliation
    index: 1
  - name: SIB Swiss Institute of Bioinformatics
    index: 2
date: 8 November 2023
cito-bibliography: paper.bib
event: BHJP24
biohackathon_name: "BioHackathon Japan 2024"
biohackathon_url:   "https://2024.biohackathon.org/"
biohackathon_location: "Fukushima, Japan"
group: Project 24
# URL to project git repo --- should contain the actual paper.md:
git_url: https://github.com/biohackathon-japan/bh24-hindsight-best-practices
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: First Author \emph{et al.}
---


# Introduction

Note taking during lunch

Evan:
Questions: How to user experience as smooth as possible across different resources: “Make it rich as possible while being truthful” (Great point: Thomas: Reference to ontology mapping SSSOM, everything exact match while this might not be true….).   
“Do not change original identifiers” http vs https ….. If you create new identifier, https://
Duplication of nodes: How should that be handled – Jerven: Just delete stuff sometimes as things do go away 

Best practice schema changes: 
Announcement ahead of time 
Support change with the Construct query (Going back to old schema)
Identifiers: Design for human readability (maybe not 000000001), how much/long can you support your identifiers? They should be resolvable.  …… IRI    
Make your IRI predictable ….. Maybe separate IRI from identifiers


Yoko
Versioning and IRIs: Should versioning be part of the IRI - NO we should avoid this kind of stuff
identifiers.org: 6 ways of handling ids (http, https, …. And others) 
Don’t put pipes in your IRIs … only safe characters in your IRI 
If you model data, be aware of the consequences of your modeling for query performance 


Jerven
Keep multiple definitions for a concepts 
Things must have good identifier (reactions identifier for Julia, multiple thing come out of multiple ontologies, and different representations but do not get lost in creating identifiers forever) 
Materialize your reasoning  
Number of entities is causing problems - not the number of triples (to be considered when designing)
“Model the data you have, not the data you wish to have”
Don’t remodel reference data (e.g. use CHEBI even if you don’t like it) 
Being worried about performance instead of schema and data quality 
Do not use place strings strings 
“Don’t be scared of blanked notes” while Evan avoids them at all costs ;) 
Regret …. Not enough multilinguality in the projects 
Use the reasoner but do not please the reasoner (Rhea example. Sometimes do not go for OWL …. But you might want to include a shortcut property to support querying )



Thomas
User centric: Usefulness of a schema might be more important than getting lost in all sort of details [Potentially connection to readable IRIs, predicates etc] → Proposal: readable predicates 
Focus on what be strict and when to be flexible (e.g. strict with identifiers, but ok with multiple definitions for a concept) 
Shape we were missings in the past …. But do not overdo restricting 
Do not be scared of combining RDF with other resources/technologies 



Rhea regrets
rdf.rhea-db.org not purl.rhea-db.org ← do no make rdf part of your identifier   
Not always have rdf:type
Too scared of OWL
Not running a reasoner and materialize ahead of time

UniProt regrets
Not adding inferable information (fixed)
E.g. missing type to avoid to many triples
subClassOf hierarchy
Super predicates
up:annotation
rdfs:seeAlso
Custom code
Started in 2003, don’t do this in 2024
Not advertising enough

URI synonyms (yasunori)
Large (tier one?) datasets have their own identifier namespace ecosystem such as purl.uniprot.org or rdf.ncbi.nlm.nih.gov/pubchem . For those wanting to use them seamlessly we need to provide an infrastructure where conceptually identical identifiers are processed as such.
owl:sameAs would be a solution for machines to recognize them identically, but would it be the best practice?
Now I’m surveying which identifiers are synonymous with each other in the entire datasets stored at RDF Portal.
DBCLS has recommended our collaborating partners to use identifiers.org IDs when building RDF datasets. Consequently, many resultant datasets use the namespace as objects of the rdfs:seeAlso predicate whose subject are their original identifiers. This is much better than nothing, but machines cannot process them identically.
We are trying to build a synonym dictionary to support machines to process them seamlessly over the datasets.
Maybe the namespace of identifiers.org would be the “esperanto” identifiers.

(Shuichi)
I think that using identifiers.org URIs in RDF itself is a reasonable solution for the current situation. On the other hand, new database resources need to go through the EBI review process before they can be added to identifiers.org, and sometimes they are rejected, so it is not always possible to use them. (Jerven: bioregistry might help)


(Jerven)
Don’t follow examples of the large databases if you are not large. UniProt, PubChem has a certain scale of users and data. You might not have that, so don’t design for that.


(Julia)
Progress 24 tables, 21 tables but one 3 has three things. Some of the DB schema should not be exposed. Deal with the historical baggage of the relation database that you might have. One table might have multiple tables. KG as representations for our databases that are easier to use. 

(Jerven)
TIP: model your own data first, before starting to reuse/map.

(Thomas)
Start somewhere. Do a boxology, what are the key concepts and build from there. Your blackboard will likely match your core schema. Each box will be class, each arrow a predicate.

(Suichi)

Question: rdf.ncbi.nih.gov/pubmed/6/ and https://pubmed.ncbi.nlm.nih.gov/6/ 

Expasy will do purl.expasy.org/database we recommend the same. This allows us to redirect to deprecation and rehosting pages. Such IRIs should be reasonably a-political to allow for merger and organizational changes.

Prefer
Well maintained ontologies
Check for usage
Do they have community that allows you to participate
Mix and match, does it meet your needs, if in doubt map

Document your queries and put them in your sparql endpoint see: https://sib-swiss.github.io/sparql-examples/ for help with maintaining them (also https://github.com/sib-swiss/sparql-examples-utils/) 






# Formatting

This document use Markdown and you can look at [this tutorial](https://www.markdowntutorial.com/).

## Subsection level 2

Please keep sections to a maximum of only two levels.

## Tables and figures

Tables can be added in the following way, though alternatives are possible:

Table: Note that table caption is automatically numbered and should be
given before the table itself.

| Header 1 | Header 2 |
| -------- | -------- |
| item 1 | item 2 |
| item 3 | item 4 |

A figure is added with:

![Caption for BioHackrXiv logo figure](./biohackrxiv.png)

# Other main section on your manuscript level 1

Lists can be added with:

1. Item 1
2. Item 2

# Citation Typing Ontology annotation

You can use [CiTO](http://purl.org/spar/cito/2018-02-12) annotations, as explained in [this BioHackathon Europe 2021 write up](https://raw.githubusercontent.com/biohackrxiv/bhxiv-metadata/main/doc/elixir_biohackathon2021/paper.md) and [this CiTO Pilot](https://www.biomedcentral.com/collections/cito).
Using this template, you can cite an article and indicate _why_ you cite that article, for instance DisGeNET-RDF [@citesAsAuthority:Queralt2016].

The syntax in Markdown is as follows: a single intention annotation looks like
`[@usesMethodIn:Krewinkel2017]`; two or more intentions are separated
with colons, like `[@extends:discusses:Nielsen2017Scholia]`. When you cite two
different articles, you use this syntax: `[@citesAsDataSource:Ammar2022ETL; @citesAsDataSource:Arend2022BioHackEU22]`.

Possible CiTO typing annotation include:

* citesAsDataSource: when you point the reader to a source of data which may explain a claim
* usesDataFrom: when you reuse somehow (and elaborate on) the data in the cited entity
* usesMethodIn
* citesAsAuthority
* citesAsEvidence
* citesAsPotentialSolution
* citesAsRecommendedReading
* citesAsRelated
* citesAsSourceDocument
* citesForInformation
* confirms
* documents
* providesDataFor
* obtainsSupportFrom
* discusses
* extends
* agreesWith
* disagreesWith
* updates
* citation: generic citation


# Results


# Discussion

...

## Acknowledgements

...

## References
