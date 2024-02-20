# Roadmap to DB Design

1. Collect requirements (users, views, constraints, tasks)
2. Model requirements and validate (ERD and EERD)
3. Map ERD to relational model
4. Verify mode with relational algebra
5. Build model using DBMS (SQL)
6. Optimize model (normalization and indexing)
7. Build transactions and other user tools

## Requirements

## Modelling

### Reasons for modelling

- learn from the modelling process
- reduce complexity by abstraction
- remember details
- communication with team and stakeholders
- documentation for future reference

### Entity-Relationship (ER) Model

Helpful for conceptualizing the real world. It shows a simple, static memory of a system.

[Terms]
`Entity`: A thing that exists.
`Entity Set`: A _group_ of similar `Entities`.
`Attribute`: Property of an `Entity` or `Relationship`, such as an ID.
`Domain`: A set of values allowed for an `Attribute`.
`Relationship`: Something that relates two `Entities`.
`Restraint`: A limitation to `Relationships`, including `Cardinality` and `Participation`.
NOTE: Entities are drawn in a rectangle, and attributes are connected with a line and enclosed in an oval.
Attributes can be linked to other attributes. Relationships are denoted by diamonds.

[Entity Types]
`Weak Entity`: Denoted with a double box, a weak entity does not have a strong key attribute and is identified by being related to specific entities from another entity type.

[Attribute Types]
`Single or Atomic Attribute`: An attribute that does not link to another attribute (leaf node).
`Composite Attribute`: Attribute that can be subdivided into other attributes (node with children).
`Multivalue Attribute`: Attribute with more than value (phone number(s)). Drawn with a double bubble.
`Derived Attribute`: Attribute that can be calculated, drawn with dotted bubble, not stored.  
`Partial Key`: Denoted with a dotted text underline, used to identify a `Weak Entity`.

[Restraint Types]
`Cardinality`: N is normal? 1 denotes only 1 assignment max, M is assignment to several at the same time, with an attribute matched.
`Participation`: Double line denotes total participation required on that side of the relationship.

Compound composite key is when two keys on an entity are required for identification.

## ERD Diagram Checklist

Entities

- [ ] Entity names are nouns
- [ ] Entity names are singular
- [ ] Entity names are descriptive
- [ ] Entity names are unique
- [ ] Entity names are concise

Attributes

- [ ] Fields and Column headings should be considered
- [ ] Attributes

Multivalue Attributes

- [ ] Multivalue Attribute is is not simple and cardinality is not important

# Enhanced Entity-Relationship (EER) Model

## Subclasses & Superclasses & Inheritance

A subclass of an entity is a child of that entity. A subclass inherits all attributes of its parent entity. A subclass can have its own attributes. A subclass can have its own relationships.

A superclass of an entity is a parent to that entity. A superclass can have its own attributes. A superclass can have its own relationships.

We can denote inheritance with a circle. A superclass connects to a circle which connects to a subclass(es). The circle is labelled with a `d` for disjoint or an `o` for overlapping. Disjoint means that an entity can only be in one subclass. Overlapping means that an entity can be in multiple subclasses. Superclasses and subclasses are differentiated by rounded arrows on the relationship lines.

A subclass inherits all attributes of its parent entity.

## Union

We can union superclasses together into a joint class

## Specialization

## Generalization

## Constraints
