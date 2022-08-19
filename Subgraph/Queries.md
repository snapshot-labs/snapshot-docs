---
sidebar_position: 3
title: Sample Queries
---

## Sample Queries

Below are some sample queries you can use to gather information from the Snapshot contracts.

You can build your own queries using a [GraphQL Explorer](https://graphiql-online.com/graphiql) and enter your endpoint to limit the data to exactly what you need.

### Get space delegations

```graphql
{
  delegations(
    block: { number: 11686897 }
    first: 1000
    where: { space_in: ["balancer", ""] }
  ) {
    delegate
    delegator
    space
  }
}
```

### Query signitures for a Gnosis Safe

```graphql
{
  sigs(
    first: 10
    where: { account: "0x78E1F985e36A2F5CF3b15a9d7214E71eCaEADFB0" }
  ) {
    id
    account
    msgHash
  }
}
```

### Get Delegations

```graphql
{
  delegations(
    block: { number: 11686897 }
    first: 1000
    where: {
      delegate_in: [
        "0x4C7909d6F029b3a5798143C843F4f8e5341a3473"
        "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7"
      ]
    }
  ) {
    delegator
    space
  }
}
```
