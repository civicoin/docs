# Entities

**In general.** Administrator comes to platform and creates `system`, where `members` sign up.
Next, administrator (actually `system` itself) issues coins, sends them to `members`, and after they start exchanging — all these operations generate `transactions`.
It’s possible not to send coins immediately and to hold them instead — there are `holds` for this purpose (for example, for contracts).
There are also `statements`, they help to calculate balances and track economy and wallets value

> In our terminology, a **user** can be an administrator (essentially a **system**) or a **member** (of some system). Even though they’re completely different things

Different services are responsible for storing and processing different entities:

## Gateway

It works with `systems` and `members`. The NoSQL database MongoDB is used

For the rest, it requests other services with information about the current system and the member, if required

### System

The *local financial systems*. Each `system` is its own separate little independent economic world with its own coin, rules, users and intractions

#### Fields:

- **id**
- **name** — The unique name of the system
- **description** — Description
- **coin** — Name of the local coin
- **logo** — Coin logo (some configuration from editor)
- **restriction** — Visibility of transactions and other data to administrator and members (*private / public*). When public, all transactions are visible to all members, and when private — even the administrator doesn’t have the possibility to check them
- **core** — The core service to use (*core*)
- **issuance**:
  - **type** — Whether the issue of coins is limited and what type of limit is used (*unlimited / limited*)
  - **limit** (*type = limited*) — The limit of coins to issue at system (unchangeble in the future)
- **password** — Hashed password
- **status** — System’s status (*active / deleted*)
- **created** — Timestamp
- **updated** — Timestamp

### Member

Member of some system

#### Fields:

- **id**
- **system** — The system where member exists
- **name** — Username, unique for system
- **password** — Hashed password
- **status** — Member’s status (*validating / rejected / active / deleted*)
- **created** — Timestamp
- **updated** — Timestamp

## Core (centralized)

Cores are services of transactions processing. The primary and comprehensive one — the Centralized Core (*Core*).
Works with `transactions`, `holds` and `statements`

### Transaction

Coin transactions. They are created, and never deleted or updated

#### Fields:

- **id**
- **system**
- **sender** — Sender member (*if coins are transferred*)
- **receiver** — Receiver member
- **amount** — Amount of coins to transfer
- **type** — Type of transaction (*issuance / transfer*)
- **created** — Timestamp

### Hold

It’s possible to hold coins instead of instant transfer, which is useful when fulfilling contracts. As distinct from transactions, holds are removed after certain conditions have occurred

### Statement

Statement is created for a member of some system at some timestamp, contains balance. Used to optimize of balances calculation and as historical data for members and system
