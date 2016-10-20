WP3 Data Model
==============

* [What is the status of this document?][statuses]
* [See the index of all other EWP Specifications][develhub]


Summary
-------

This document describes the **data model**. This is basically a PDF document 
in E-R (Entity-Relationship) notation, describing the underlying information
structure the APIs expose.


Notation
--------

 * Entity and attribute names are in Initcaps With Spaces (e.g. Cooperation
   Condition and Mobility Type). This translates to lowercase-with-hyphens in
   the XSDs (e.g. cooperation-condition and mobility-type).

 * Entity and attribute names are sometimes abbreviated for diagram clarity.
   Attributes that naturally belong in pairs are often abbreviated to a single
   attribute with a slash (e.g. Start/End Date = Start Date + End Date).

 * Primary keys (identifiers) can consist of more than one attribute, are
   underscored, denoted by PK and positioned above the entity line.

 * Mandatory attributes are in boldface.

 * Relationships are usually 1:many, where the "many" end is denoted by
   a circle and "crow's feet", denoting "0 or more". The connected entities are
   called "owner" and "member" respectively. The relationship is implemented by
   foreign key attributes (denoted by FK) in the member entity. Some
   relationships have labels, usually specifying a **role** (if there are more
   than one relationship between the entities in question and/or it's not
   self-evident what the relationship "means").

 * Relationships can be identifying or non-identifying. If a relationship is
   identifying, it means the connection from member (in the "many" end) to
   owner **partly identifies** the member. Identifying relationships have a
   solid line, non-identifying relationships are dashed.

 * Non-identifying relationships can be mandatory or optional. Mandatory
   relationships have two crossbars (|-|) at the owner end, denoting "minimum
   1, maximum 1". Optional relationships have a circle and a crossbar (O-|),
   denoting "minimum 0, maximum 1".

 * Recursive relationships (from an entity to itself) implement a **hierarchy**.
   Relationships referencing this entity can point to any level in the
   hierarchy. Exceptions are explicitly stated on the relationship in
   parentheses - e.g. "(always institution)".


Special entitities
------------------
Inst/Org Unit models both Institution and Department: It has a recursive
relationship, implementing a hierarchy where the top level is the institution
itself.


[develhub]: http://developers.erasmuswithoutpaper.eu/
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management#statuses
[discovery-api]: https://github.com/erasmus-without-paper/ewp-specs-api-discovery
[echo]: https://github.com/erasmus-without-paper/ewp-specs-api-echo
[error-handling]: https://github.com/erasmus-without-paper/ewp-specs-architecture#error-handling