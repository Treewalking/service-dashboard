---
permalink: /about/
title: "About"
toc: true
---

## Introduction

## Model

The Treewalking Dashboard uses a set of well-defined Classes to describe the structure of the organisation. These data
items are then declared either by a Markdown page, or via a data extraction script. Usually, Markdown files represent
data that changes at a glacial pace, i.e. squad names and membership, etc, while other types of data is more real-time
thus is extracted using automated scripts, i.e. Sprint/Kanban metrics, Availability, etc.

For each of these Classes, we'll indicate the data type, i.e. manual vs automation.

{% include mermaid.html %}

<div class="mermaid">
    classDiagram
    Tribe
    Proposition
    Product
    Service
    Component
    Squad
    Individual
    Role
    Skill
    Stack
    Platform
    Increment
    Sprint
    Review
    Standard
    Process
    Decision
    Pattern
    Tribe o-- "*" Proposition : owns
    Proposition o-- "*" Service : composed_of
    Proposition o-- "*" Product : composed_of
    Service o-- "*" Component : composed_of
    Service --> "*" Product : delivers 
    Tribe o-- "*" Squad : membership
    Squad o-- "*" Individual: membership
    Individual --> "1" Role: is_a
    Individual --> "*" Skill : experienced_in
    Squad --> "*" Service: owns
    Service --> "*" Stack: uses
    Tribe o-- "*" Increment: planned_by
    Stack <|-- Platform
    Stack <|-- MicroService
    Stack <|-- FrontEnd
    Stack <|-- Storage
    Stack <|-- Messaging
    Increment o-- "*" Sprint : contains
    Sprint o-- "*" Review : ends_with
    Review --> "1" Squad
    Tribe o-- "*" Standard : has
    Tribe o-- "*" Process : has
    Tribe o-- "*" Decision : has
    Decision --> "*" Proposition : targets
    Decision --> "*" Squad : targets
    Decision --> "*" Service : targets
    Decision --> "*" Component : targets
    Decision --> "*" Stack : targets
    Decision --> "*" Standard : targets
    Decision --> "*" Process : targets
    Decision --> "*" Pattern : targets
    Decision --> "1" Increment : decided
    Decision --> "1..*" Individual : decider
    Tribe o-- "*" Pattern : has
</div>

| Class                       | Description                                                                          | Collection   | Template        |
|-----------------------------|--------------------------------------------------------------------------------------|--------------|-----------------|
| [Tribe](#tribe)             | A delivery organisation focused on a set of related product propositions             | Manual       |                 |
| [Proposition](#proposition) | A grouping of related products and services that provide a common business objective | Manual       | 


### Tribe

> A delivery organisation focused on a set of related product propositions.

The top-level class for the whole dashboard. The [Tribe](#Tribe) owns the majority of the other items in the Dashboard.


| Data/Association | Description                                                                                       |
|------------------|---------------------------------------------------------------------------------------------------|
| Title            | The name of the tribe                                                                             |


### Proposition

> A grouping of related products and services that provide a common business objective.

We group a related set of products/services/assets into a [Proposition](#proposition) so that we can organise our
requirements, designs, squads, ownership and leadership for a set of common business and engineering outcomes. Its 
creates a high level business and engineering bounded context.

| Data/Association | Description                                                                                          |
|------------------|------------------------------------------------------------------------------------------------------|
| Title            | The name of the Proposition                                                                          |
| Description      | The TL;DR description for the [Proposition](#proposition)                                            |
| Leads            | A list of [Proposition](#proposition) Product and Engineering leadership [Individual](#individual)'s |
| Site             | URL to the [Proposition](#proposition)'s micro-site                                                  |

### Service

### Component