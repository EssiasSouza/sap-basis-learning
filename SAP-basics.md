# SAP Basics learning
This is my basic studies of SAP that I have structured by myself.

- [Structure](#structure)
- [SAP SECURITY BASICS](#sap-security-basics)



## Structure
This is a short discription of SAP structure.

- SAP S/4HANA → The ERP system (application)
- SAP NetWeaver → Application server
- SAP HANA → Database
- Linux → Operating system
- Cloud / Server → Infrastructure

Stack
```
Users
  ↓
SAP S/4HANA
  ↓
NetWeaver
  ↓
SAP HANA (Database)
  ↓
Linux
  ↓
Server / Cloud
```

### SAP SECURITY BASICS

User administration in SAP is one of the core responsibilities of SAP BASIS, and it revolves around a few key concepts:

- Users
- Roles
- Profiles
- Authorizations
- Authorization Objects

Users are created and managed in transaction `SU01`

A SAP user contains:

- Username
- Password
- User type
- Roles Assigned
- Validity dates
- Default parameters

#### SAP User types

| Type          | Purpose                        |
| ------------- | ------------------------------ |
| Dialog        | Normal human user              |
| System        | System-to-system communication |
| Communication | RFC / external systems         |
| Service       | Shared users                   |
| Reference     | Used only to assign roles      |

#### Roles

Roles are created in `PFCG`

A role is a container of permissions and it defines:

- Transactions the user can execute
- Authorization objects
- Field restrictions (company code, plant, etc)

Example:

| Role        | Access               |
| ----------- | -------------------- |
| FI_USER     | Finance transactions |
| MM_USER     | Materials            |
| BASIS_ADMIN | Admin transactions   |
| HR_USER     | HR transactions      |


#### Profiles

Profiles are generated from roles

```
Role → generates → Profile → contains → Authorizations
---
User
  ↓
Role
  ↓
Profile
  ↓
Authorizations
  ↓
Authorization Objects
  ↓
Fields (Company code, activity, etc.)
```

#### Authorization Objects

An authorization object controls access based on fields like:

- Activity (read, write, delete)
- Company code
- Plant
- Sales organization
- Document Type

Example:

Authorization Object: F_BKPF_BUK


Fields

| Field | Meaning      |
| ----- | ------------ |
| BUKRS | Company Code |
| ACTVT | Activity     |

Activity values

| Value | Meaning |
| ----- | ------- |
| 01    | Create  |
| 02    | Change  |
| 03    | Display |
| 06    | Delete  |

So you could allow a user to:

- Display documents
- Only for company 1000
- But not change

#### Important transactions for User Administration

| Transaction | Purpose                      |
| ----------- | ---------------------------- |
| SU01        | Create/change user           |
| PFCG        | Roles                        |
| SUIM        | User reports                 |
| SU53        | Authorization error analysis |
| ST01        | Authorization trace          |
| SM19        | Security audit log           |
| SM20        | Security audit log analysis  |

**PRAM was replaced by PFCG-based role concept**
---
- Consultants - Specialist that knows how to configure through `customizing` panel the functions asked by `key users` in the project.
- ABAP Developer or ABAP contaultant - A ABAP developer responsible to develop functions that the consultant doesn't achieve to do using the `customize` interface.
- Key users - Users from the company that knows the business and their areas and are responsible to inform what is needed.

### Kinds of SAP Project
- Implement SAP project - To implement the SAP on a company that doesn't have an ERP yet.
- Rollout SAP Project - To implement the SAP in a company branch
- Upgrade SAP Project - To implement upgrades and updates in a company
- Improvements SAP project - To create improvements.

### Common SAP modules

When a company buy the system receives some done modules to implement in a company.

- PP - Production Planing
- FI - Financial Account
- CO - Controlling
- SD - Sales and Distribution

All what happens in SAP is a transaction, that is a alphanumeric code of 20 characters.

## SAP LANDSCAPE

- DEV (D01) - Environment of Development
- QAS (Q01) - Environment focused to be used in tests of quality
- PROD (P01) - Environment used by final user

## ASAP Methodology

This is a special methodology used by SAP to manage projects in SAP environments

1. Inicial preparation - Part of project for a aproximated 1 hour to an inicial planing, define infrastructure, mapping the procedures and do a Kickoff
   This time is also to create a `Project Plan` that is firmed by all of envolveds, timeline of project, Kickoff meeting and define:
   - Functional Consultant
   - Technician Consultants (BASIS and ABAP)
   - Key users
   - Project manager in duty
   - Consultancy
    
2. Busines Blue Print - Design to soluction 
   To document:
   - AS IS - How is the program and the problem todady
   - TO BE - How it need to be
   
3. Realization - Time to start the effective development of was asked until step 3 of ASAP methodology.
   Examples of configuration from a Functional Consultant
    - Definition of expedition local
    - Creation of a cost center
    - Definition of tax calculation
  - Settings
  - Developments
  - Unit Tests - Tests of a unit of what was asked is ok.
  - Integrated tests - In this kind of tests the homologation needs to check all of process that are included in the process of the request are not broken by this new feature. Important to be mapped and followed by the Project manager if all of envolved people are testing the whole test process.
  - After homologation this fase is finished.
   
4. Final preparation - Trainings and Cutover
 - Cutover - Actions to be done next fo the implementation time. Exemple: Inform that this will be changed, anticipate sales and etc.
 - Training all envolved users to know how is the function after realization step.

5. Go live and Support
 - Go-live - Time to deploy it
 - Support - Following possible erros.
 - KT - Knowlegde Transfer
 - Project finish - It is usually done in the night or when the users aren't using the system.
 - Assisted operation - The project team is available to follow for a while to support the next days after the implementment
 - Finishing project - This is finished when the client firm it as accepted.

## Clients

Clients are isolated environments in the SAP System to enclosures some access, right and other things about this X process.

There are 2 ways of installation.
  1. IDES
     There are 7 clients create with the installation process
     ```
     000 - Master client
     001 - Master client
     066 - Early watch client
     800
     810
     811
     812
     ```
  3. NON-IDES
     There are 3 clients create with the installation process
     ```
     000 - Master client
     001 - Master client
     066 - Early watch client
     ```

## SOLMAN - SOLUTION MANAGER

This is a tool that gives improvement opportunities included used to create a Blue Print.
This solution can measure the system usage to improve that.
Also used to do and manage `integrated tests`.
This tool allows versioning the Blue Print document.

## PROJECT LIBRE

This is a tool of management of project timeline

## SAP ACTIVATE METHODOLOGY

---

# LEARNING STRATEGY

### Books to learn
1. SAP Administration — Practical Guide
 - A wide vision of administration of the system
 - Investigate:
    - landscape
    - monitoring
    - users
    - logs
    - Administrative tasks
2. SAP NetWeaver AS ABAP — System Administration
 - Administration of application server:
    - work processes
    - jobs
    - dumps
    - RFC
    - load balancing

3. SAP HANA 2.0 Installation and Administration
   - Investigate:
    - memory
    - queries
    - locks
    - index
    - storage

---
# SAP ACTIVATE

SAP ACTIVATE is a project management methodology to perform changes on a SAP environment to implement, fix, update, configure or develop some new features.

This methodology 







<!--
- 1️⃣ Como montar um ambiente SAP para estudar (de graça)
- 2️⃣ Quais transações BASIS você precisa dominar primeiro
- 3️⃣ qual certificação SAP BASIS vale a pena
- 4️⃣ qual livro da SAP Press vem depois desse-->
