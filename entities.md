# Entities

**In general.** Administrator comes to platform and creates `system`, where `members` sign up.
Next, administrator (actually `system` itself) issues coins, sends them to `members`, and after they start exchanging — all these operations generate `transactions`.
It’s possible not to send coins immediately and to hold them instead — there are `holds` for this purpose (for example, for contracts).
There are also `statements`, they help to calculate balances and track economy and wallets value.

> In our terminology, a **user** can be an administrator (essentially a **system**) or a **member** (of some system). Even though they’re completely different things

Different services are responsible for storing and processing different entities:

## Gateway

It works with `systems` and `members`. The NoSQL database MongoDB is used.

For the rest, it requests other services with information about the current system and the member, if required.

### System

The *local financial systems*. Each `system` is its own separate little independent economic world with its own coin, rules, users and intractions.

#### Fields:
- **name** — The unique name of the system
- **description** — Description
- **coin** — Name of the local coin
- **logo** — Coin logo (some configuration from editor)
- **restriction** — Visibility of transactions and other data to administrator and members (*private / public*). When public, all transactions are visible to all members, and when private — even the administrator doesn’t have the possibility to check them
- **core** — The core service to use (*core*)
- **issue**:
  - **type** — Whether the issue of coins is limited and what type of limit is used (*unlimited / limited*)
  - **limit** (*type = limited*) — The limit of coins to issue at system (unchangeble in the future)

### User

## Core (centralized)

Core

### Transaction

Transaction

### Hold

Hold

### Statement

Statement
