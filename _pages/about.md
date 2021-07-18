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
    Service
    Component
    Squad
    Individual
    Role
    Stack
    Increment
    Tribe o-- "*" Proposition : owns
    Proposition o-- "*" Service : composed_of
    Service o-- "*" Component : composed_of
    Tribe o-- "*" Squad : membership
    Squad o-- "*" Individual: membership
    Individual --> "1" Role: is_a
    Squad --> "*" Service: owns
    Service --> "*" Stack: uses
    Tribe o-- "*" Increment: planned_by
</div>

| Class           | Description                                                                          | Collection   |
|-----------------|--------------------------------------------------------------------------------------|--------------|
| [Tribe](#tribe) | A delivery organisation focused on a set of related product propositions.           | Manual       |

### Tribe

> A delivery organisation focused on a set of related product propositions.

The top-level class for the whole dashboard. The [Tribe](#Tribe) owns the majority of the other items in the Dashboard.

A Tribe is defined using the [tribe.html]() layout.

| Data/Association | Description                                                                                       |
|------------------|---------------------------------------------------------------------------------------------------|
| Title            | The name of the tribe                                                                             |


### Proposition

### Service

### Component