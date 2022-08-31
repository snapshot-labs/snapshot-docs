---
sidebar_position: 2
title: Subgraph Entities
---

## Entities

- [`Delegation`](#delegation)
- [`Block`](#block)
- [`Sig`](#sig)

## Delegation

Description:

| Field     | Type    | Description |
| --------- | ------- | ----------- |
| id        | ID!     |             |
| delegator | Bytes!  |             |
| space     | String! |             |
| delegate  | Bytes!  |             |
| timestamp | Int!    |             |

## Block

Description:

| Field     | Type       | Description |
| --------- | ---------- | ----------- |
| id        | ID!        |             |
| number    | BigInt!    |             |
| timestamp | Timestamp! |             |

## Sig

Description:

| Field     | Type    | Description |
| --------- | ------- | ----------- |
| id        | ID!     |             |
| account   | Bytes!  |             |
| msgHash   | String! |             |
| timestamp | BigInt! |             |
