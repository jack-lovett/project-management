# Project Name

AI Use Case Register — Power Apps (Dataverse-backed)

# Purpose

Replace the existing Microsoft Lists-based register with a Dataverse + Power Apps solution to improve data integrity, governance, relational modeling, automation, and reporting. Provide an intuitive UI for registering, reviewing, assuring, and monitoring AI use cases across lifecycle stages and risk domains.

# Objectives

-   Centralize and standardize AI use case data (owners, status, lifecycle, risk ratings, domains, patterns, tech type).
-   Enable assurance workflows, auditability, and review cycles (last/next review).
-   Provide insightful dashboards (counts by lifecycle, risk distribution, domains/patterns, ownership).
-   Support governance processes (Assure & Align, legal checks, standards compliance).
-   Improve findability & navigation (active list, search/filter, shortcuts to resources/links).

# Scope

-   Canvas app UI built from a Figma mock-up (converted manually).
-   Core screens: Active list, use case create/edit, detailed view, dashboards, admin/reference management.
-   Robust ID strategy (business-facing Use Case Number) and core automations (status-driven timeline, review reminders).
-   Role-based experiences (viewers vs editors vs admins).

# Out of scope (for v1; can be v1.x/v2)

-   Advanced generative UI planning tools.
-   Complex PCF controls (unless needed later).
-   External system integrations beyond Microsoft 365 (except links).

# Data model notes

-   Use Case is the central entity with multiple lookups and two N:N relationships (Domains, Usage Patterns).
-   Ratings, Status, Stages, Tech Types are reference tables (maintained by admins).
-   Owners may use Dataverse users or a dedicated People table (to be confirmed).
-   Store assurance metadata (Assure & Align, legal flags, links, outcomes) directly on Use Case.

# ID strategy

-   Keep GUID as primary key.
-   Business ID: Dataverse Autonumber (preferred) with format UC-YYYY-###### or similar.
-   If you need fiscal-year reset or special rules: implement via Power Automate or Power Fx Function (server-side) and write back to the ID column.

# Automation & governance

-   On create: assign Use Case Number; create SharePoint/Teams folder (if required); initial timeline entry.
-   On status/stage change: append timeline entries; optionally send notifications.
-   Review cycle: compute next review date; reminders via Power Automate.
-   Assure & Align: capture result and links; optionally enforce field requirements by stage.

# UX principles

-   Task-first navigation (find, view, edit, assure, review).
-   Responsive layout using nested containers.
-   Clear distinction between list → details → edit flows.
-   Filters & search readily available; save common views.
-   Accessibility and readability over heavy decoration.

# Non-functional requirements

-   Performance: efficient queries and pagination in galleries.
-   Security: role-based permissions; field-level validation.
-   Maintainability: component library, reusable formulas/functions.
-   Auditability: timeline events, last/next review tracking.

# Why AI assistance is engaged

-   Structure and iterate the design plan, screen map, data modeling decisions, and automation patterns.
-   Generate Power Fx snippets, flow outlines, and component patterns.
-   Act as a memory of decisions, constraints, and rationale (this context package), and provide checklists for build & review.

# Entity Relationship Diagram

Table: Use Case

-   Primary Key (PK): ID (GUID; system primary key)
-   Columns (selected):

-   Title
-   Description
-   Business Need
-   Purpose
-   Expected Benefits
-   Lookup: Use Case Status → Use Case Status (1:N)
-   Lookup: Lifecycle Stage → Use Case Lifecycle Stage (1:N)
-   Many-to-Many: Use Case Domain ↔ via Dataverse auto-intersect table (N:N)
-   Many-to-Many: Use Case Usage Pattern ↔ via Dataverse auto-intersect table (N:N)
-   Lookup: Use Case Officer (person/owner)
-   Accountable Use Case Owner
-   Branch
-   Division
-   Assurance Officer
-   Review Status
-   Lookup: AI Technology Type → AI Technology Type (1:N)
-   Technical Standard Usage
-   Inherent Risk Rating → Use Case Risk Rating (1:N)
-   Residual Risk Rating → Use Case Risk Rating (1:N)
-   Other Risk Domain (text/lookup)
-   Other Risk Domain Rating → Use Case Risk Rating (1:N)
-   Is SaaS Product (boolean)
-   Been to Legal (boolean)
-   Assure and Align (boolean)
-   Assure and Align Link (URL)
-   Assure and Align Outcome (text)
-   DTA Lifecycle Stage (text/choice)
-   Last Review Date (date)
-   Next Review Date (date)
-   Case Notes (multiline)
-   CM9 Link (URL)

Table: Use Case Status

-   PK: Status Name
-   Description

Table: Use Case Lifecycle Stage

-   PK: Stage Name
-   Description

Table: Use Case Risk Rating

-   PK: Rating Name
-   Description

Table: Use Case Domain

-   PK: Domain Name
-   Description
-   Relationship: N:N with Use Case (auto-intersect Dataverse table)

Table: Use Case Usage Pattern

-   PK: Pattern Name
-   Description
-   Relationship: N:N with Use Case (auto-intersect Dataverse table)

Table: AI Technology Type

-   PK: Technology Name
-   Description
-   Relationship: 1:N referenced by Use Case

Relationship summary:

-   Use Case ↔ Use Case Domain: N:N
-   Use Case ↔ Use Case Usage Pattern: N:N
-   Use Case → Status / Lifecycle Stage / Risk Rating / AI Technology Type: 1:N lookups
-   People/owners are represented as lookups (specific implementation can be Dataverse user table or a custom People/Contacts table, depending on your environment).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM2NTA0NTk3XX0=
-->