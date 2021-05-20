---
description: >-
  You can use the GraphQL API to create flexible queries for the data you need
  to integrate with Snapshot.
---

# GraphQL API

## Explorer

You can run queries on real Snapshot data using the GraphQL Explorer, an integrated development environment in your browser that includes docs, syntax highlighting, and validation errors. Try here:

{% embed url="https://hub.snapshot.page/graphql" %}

![](.gitbook/assets/image.png)

## Endpoints

Production hub

```text
https://hub.snapshot.page/graphql
```

Demo hub

```text
https://testnet.snapshot.page/graphql
```

## Queries

### Get a single space <a id="space"></a>

#### Arguments

id `string`

#### Example

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  space(id: "yam.eth") {
    id
    name
    about
    network
    symbol
    members
  }
}
```
{% endtab %}

{% tab title="Response" %}
```javascript
{
  "data": {
    "space": {
      "id": "yam.eth",
      "name": "Yam Finance",
      "about": "",
      "network": "1",
      "symbol": "YAM",
      "members": [
        "0x683A78bA1f6b25E29fbBC9Cd1BFA29A51520De84",
        "0x9Ebc8AD4011C7f559743Eb25705CCF5A9B58D0bc",
        "0xC3edCBe0F93a6258c3933e86fFaA3bcF12F8D695",
        "0xbdac5657eDd13F47C3DD924eAa36Cf1Ec49672cc",
        "0xEC3281124d4c2FCA8A88e3076C1E7749CfEcb7F2"
      ]
    }
  }
}
```
{% endtab %}
{% endtabs %}

Try on [GraphiQL](https://hub.snapshot.page/graphql?query=query%20%7B%0A%20%20space%28id%3A%20%22yam.eth%22%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20name%0A%20%20%20%20about%0A%20%20%20%20network%0A%20%20%20%20symbol%0A%20%20%20%20members%0A%20%20%7D%0A%7D)

### Get multiple spaces <a id="spaces"></a>

#### Arguments

first `number`  
skip `number`  
where:  
    - id`string`  
    - id\_in`array`  
orderBy `string`  
orderDirection `asc` or `desc`

#### Example

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  spaces(
    first: 20,
    skip: 0,
    orderBy: "created",
    orderDirection: asc
  ) {
    id
    name
    about
    network
    symbol
    strategies {
      name
      params
    }
    admins
    members
    filters {
      minScore
      onlyMembers
    }
    plugins
  }
}
```
{% endtab %}

{% tab title="Response" %}
```javascript
{
  "data": {
    "spaces": [
      {
        "id": "bonustrack.eth",
        "name": "Fabien",
        "about": "",
        "network": "1",
        "symbol": "TICKET",
        "strategies": [
          {
            "name": "erc20-balance-of",
            "params": {
              "symbol": "DAI",
              "address": "0x6B175474E89094C44Da98b954EedeAC495271d0F",
              "decimals": 18
            }
          }
        ],
        "admins": [],
        "members": [
          "0x24A12Fa313F57aF541d447c594072A992c605DCf"
        ],
        "filters": {
          "minScore": 0,
          "onlyMembers": false
        },
        "plugins": {
          "quorum": {
            "total": 500,
            "strategy": "static"
          }
        }
      }
    ]
  }
}
```
{% endtab %}
{% endtabs %}

Try on [GraphiQL](https://hub.snapshot.page/graphql?query=%0Aquery%20Spaces%20%7B%0A%20%20spaces%28%0A%20%20%20%20first%3A%2020%2C%0A%20%20%20%20skip%3A%200%2C%0A%20%20%20%20orderBy%3A%20%22created%22%2C%0A%20%20%20%20orderDirection%3A%20asc%0A%20%20%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20name%0A%20%20%20%20about%0A%20%20%20%20network%0A%20%20%20%20symbol%0A%20%20%20%20strategies%20%7B%0A%20%20%20%20%20%20name%0A%20%20%20%20%20%20params%0A%20%20%20%20%7D%0A%20%20%20%20admins%0A%20%20%20%20members%0A%20%20%20%20filters%20%7B%0A%20%20%20%20%20%20minScore%0A%20%20%20%20%20%20onlyMembers%0A%20%20%20%20%7D%0A%20%20%20%20plugins%0A%20%20%7D%0A%7D)

### Get a single proposal <a id="proposal"></a>

#### Arguments <a id="arguments"></a>

id `string`‌

#### Example

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  proposal(id:"QmWbpCtwdLzxuLKnMW4Vv4MPFd2pdPX71YBKPasfZxqLUS") {
    id
    title
    body
    choices
    start
    end
    snapshot
    state
    author
    created
    plugins
    network
    strategies {
      name
      params
    }
    space {
      id
      name
    }
  }
}
```
{% endtab %}

{% tab title="Response" %}
```javascript
{
  "data": {
    "proposal": {
      "id": "QmWbpCtwdLzxuLKnMW4Vv4MPFd2pdPX71YBKPasfZxqLUS",
      "title": "Select Initial Umbrella Metapool",
      "body": "Eventually, we hope that anyone will be able to create a metapool and fund a protection market for their project, but right now we want to start small and pick one pool that we will debut as a beta launch for Umbrella that will help us gather information and insight into the state of the market. In the future we can have all of these and more. Here are the choices:\n### Option 1: BlueChips MetaPool\n\nYou might consider this the safest of the pools. It contains a collection of different “blue-chip projects” across multiple verticals that have proven track records and are considered industry leaders. These include:\n\n* (3) Bluechip protocols: MakerDAO, Compound, and Uniswap. These are commonly seen as the most battletested and trusted DeFi projects on Ethereum.\n* (2) Centralized exchanges: Coinbase and Binance. These are the most popular and generally considered to be most reputable exchanges around. *note: Payout occurs only if Safu funds or the exchange’s insurance do not cover losses.\n* (2) Hardware Wallet companies, Ledger and Trezor, including the Ledger Nano S and X, and the Trezor Model T and One. This would cover large scale exploits in their hardware or firmware and would not cover individual loss due to phishing or poor security.\n\n### Option 2: Hot New Projects MetaPool\n\nThis pool targets newer projects on Ethereum that are considered reputable and have high TVL but are less battle tested and therefore may be more risky. While they may be more risky, this may mean that there is more demand for coverage for them in the market. This list is preliminary but internal discussions considered including:\n\n * Alchemix\n*  OHM\n*  Liquity\n*  FEI\n*  Integral\n*  Reflexer\n\n### Option 3: Integrated DegenV2 MetaPool\n\nThis last option focuses more closely on YAM products, specifically DegenV2 and the constituent protocols that it uses. This option would let us insure our own users and potentially test out our products in a more limited environment. The covered protocols would be:\n\n * UMA\n * Sushiswap/Uniswap depending on where our pools live\n * Any YAM contracts that are used\n *  Any future contracts included in future versions of Degen.\n\n### Choose wisely!\n",
      "choices": [
        "Option 1: BlueChips MetaPool",
        "Option 2: Hot New Projects MetaP",
        "Option 3: Integrated DegenV2 Met"
      ],
      "start": 1620676800,
      "end": 1620806400,
      "snapshot": "12408670",
      "state": "closed",
      "author": "0xEC3281124d4c2FCA8A88e3076C1E7749CfEcb7F2",
      "space": {
        "id": "yam.eth",
        "name": "Yam Finance"
      }
    }
  }
}
```
{% endtab %}
{% endtabs %}

Try on [GraphiQL](https://hub.snapshot.page/graphql?operationName=Proposal&query=query%20Proposal%20%7B%0A%20%20proposal%28id%3A%22QmWbpCtwdLzxuLKnMW4Vv4MPFd2pdPX71YBKPasfZxqLUS%22%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20title%0A%20%20%20%20body%0A%20%20%20%20choices%0A%20%20%20%20start%0A%20%20%20%20end%0A%20%20%20%20snapshot%0A%20%20%20%20state%0A%20%20%20%20author%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%20%20name%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)

### Get proposals <a id="proposals"></a>

#### Arguments

first `number`  
skip `number`  
where:  
    - id`string`  
    - id\_in`array`  
    - space:`string`  
    - space\_in:`array`  
    - author:`string`  
    - author\_in:`array`  
    - network: `string`  
    - network\_in: `array`  
    - state: `array`  
orderBy `string`  
orderDirection `asc` or `desc`

#### Example

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  proposals (
    first: 20,
    skip: 0,
    where: {
      space_in: ["yam.eth"],
      state: "closed"
    },
    orderBy: "created",
    orderDirection: desc
  ) {
    id
    title
    body
    choices
    start
    end
    snapshot
    state
    author
    space {
      id
      name
    }
  }
}
```
{% endtab %}

{% tab title="Response" %}
```javascript
{
  "data": {
    "proposals": [
      {
        "id": "QmWbpCtwdLzxuLKnMW4Vv4MPFd2pdPX71YBKPasfZxqLUS",
        "title": "Select Initial Umbrella Metapool",
        "body": "Eventually, we hope that anyone will be able to create a metapool and fund a protection market for their project, but right now we want to start small and pick one pool that we will debut as a beta launch for Umbrella that will help us gather information and insight into the state of the market. In the future we can have all of these and more. Here are the choices:\n### Option 1: BlueChips MetaPool\n\nYou might consider this the safest of the pools. It contains a collection of different “blue-chip projects” across multiple verticals that have proven track records and are considered industry leaders. These include:\n\n* (3) Bluechip protocols: MakerDAO, Compound, and Uniswap. These are commonly seen as the most battletested and trusted DeFi projects on Ethereum.\n* (2) Centralized exchanges: Coinbase and Binance. These are the most popular and generally considered to be most reputable exchanges around. *note: Payout occurs only if Safu funds or the exchange’s insurance do not cover losses.\n* (2) Hardware Wallet companies, Ledger and Trezor, including the Ledger Nano S and X, and the Trezor Model T and One. This would cover large scale exploits in their hardware or firmware and would not cover individual loss due to phishing or poor security.\n\n### Option 2: Hot New Projects MetaPool\n\nThis pool targets newer projects on Ethereum that are considered reputable and have high TVL but are less battle tested and therefore may be more risky. While they may be more risky, this may mean that there is more demand for coverage for them in the market. This list is preliminary but internal discussions considered including:\n\n * Alchemix\n*  OHM\n*  Liquity\n*  FEI\n*  Integral\n*  Reflexer\n\n### Option 3: Integrated DegenV2 MetaPool\n\nThis last option focuses more closely on YAM products, specifically DegenV2 and the constituent protocols that it uses. This option would let us insure our own users and potentially test out our products in a more limited environment. The covered protocols would be:\n\n * UMA\n * Sushiswap/Uniswap depending on where our pools live\n * Any YAM contracts that are used\n *  Any future contracts included in future versions of Degen.\n\n### Choose wisely!\n",
        "choices": [
          "Option 1: BlueChips MetaPool",
          "Option 2: Hot New Projects MetaP",
          "Option 3: Integrated DegenV2 Met"
        ],
        "start": 1620676800,
        "end": 1620806400,
        "snapshot": "12408670",
        "state": "closed",
        "author": "0xEC3281124d4c2FCA8A88e3076C1E7749CfEcb7F2",
        "space": {
          "id": "yam.eth",
          "name": "Yam Finance"
        }
      },
      ...
    ]
  }
}
```
{% endtab %}
{% endtabs %}

Try on [GraphiQL](https://hub.snapshot.page/graphql?operationName=Proposals&query=query%20Proposals%20%7B%0A%20%20proposals%20%28%0A%20%20%20%20first%3A%2020%2C%0A%20%20%20%20skip%3A%200%2C%0A%20%20%20%20where%3A%20%7B%0A%20%20%20%20%20%20space_in%3A%20%5B%22yam.eth%22%5D%2C%0A%20%20%20%20%20%20state%3A%20%22closed%22%0A%20%20%20%20%7D%2C%0A%20%20%20%20orderBy%3A%20%22created%22%2C%0A%20%20%20%20orderDirection%3A%20desc%0A%20%20%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20title%0A%20%20%20%20body%0A%20%20%20%20choices%0A%20%20%20%20start%0A%20%20%20%20end%0A%20%20%20%20snapshot%0A%20%20%20%20state%0A%20%20%20%20author%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%20%20name%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)

### Get a single vote <a id="vote"></a>

#### Arguments <a id="arguments"></a>

id `string`‌

#### Example

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  vote (
    id: "QmeU7ct9Y4KLrh6F6mbT1eJNMkeQKMSnSujEfMCfbRLCMp"
  ) {
    id
    voter
    created
    proposal
    choice
    space {
      id
    }
  }
}
```
{% endtab %}

{% tab title="Response" %}
```javascript
{
  "data": {
    "vote": {
      "id": "QmeU7ct9Y4KLrh6F6mbT1eJNMkeQKMSnSujEfMCfbRLCMp",
      "voter": "0x96176C25803Ce4cF046aa74895646D8514Ea1611",
      "created": 1621183227,
      "proposal": "QmPvbwguLfcVryzBRrbY4Pb9bCtxURagdv1XjhtFLf3wHj",
      "choice": 1,
      "space": {
        "id": "spookyswap.eth"
      }
    }
  }
}
```
{% endtab %}
{% endtabs %}

Try on [GraphiQL](https://hub.snapshot.page/graphql?operationName=Vote&query=query%20Vote%20%7B%0A%20%20vote%20%28%0A%20%20%20%20id%3A%20%22QmeU7ct9Y4KLrh6F6mbT1eJNMkeQKMSnSujEfMCfbRLCMp%22%0A%20%20%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20voter%0A%20%20%20%20created%0A%20%20%20%20proposal%0A%20%20%20%20choice%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)

### Get votes <a id="votes"></a>

#### Arguments

first `number`  
skip `number`  
where:  
    - id`string`  
    - id\_in`array`  
    - space:`string`  
    - space\_in:`array`  
    - voter:`string`  
    - voter\_in:`array`  
    - proposal: `string`  
    - proposal\_in: `array`  
orderBy `string`  
orderDirection `asc` or `desc`

#### Example

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  votes (
    first: 1000
    skip: 0
    where: {
      proposal: "QmPvbwguLfcVryzBRrbY4Pb9bCtxURagdv1XjhtFLf3wHj"
    }
    orderBy: "created",
    orderDirection: desc
  ) {
    id
    voter
    created
    proposal
    choice
    space {
      id
    }
  }
}
```
{% endtab %}

{% tab title="Response" %}
```javascript
{
  "data": {
    "votes": [
      {
        "id": "QmeU7ct9Y4KLrh6F6mbT1eJNMkeQKMSnSujEfMCfbRLCMp",
        "voter": "0x96176C25803Ce4cF046aa74895646D8514Ea1611",
        "created": 1621183227,
        "proposal": "QmPvbwguLfcVryzBRrbY4Pb9bCtxURagdv1XjhtFLf3wHj",
        "choice": 1,
        "space": {
          "id": "spookyswap.eth"
        }
      },
      {
        "id": "QmZ2CV86QH6Q6z7L6g7yJWS3HfgD9aQ3uTYYMXkMa5trHf",
        "voter": "0x2686EaD94C5042e56a41eDde6533711a4303CC52",
        "created": 1621181827,
        "proposal": "QmPvbwguLfcVryzBRrbY4Pb9bCtxURagdv1XjhtFLf3wHj",
        "choice": 1,
        "space": {
          "id": "spookyswap.eth"
        }
      },
      ...
    ]
  }
}
```
{% endtab %}
{% endtabs %}

Try on [GraphiQL](https://hub.snapshot.page/graphql?operationName=Votes&query=query%20Votes%20%7B%0A%20%20votes%20%28%0A%20%20%20%20first%3A%201000%0A%20%20%20%20skip%3A%200%0A%20%20%20%20where%3A%20%7B%0A%20%20%20%20%20%20proposal%3A%20%22QmPvbwguLfcVryzBRrbY4Pb9bCtxURagdv1XjhtFLf3wHj%22%0A%20%20%20%20%7D%0A%20%20%20%20orderBy%3A%20%22created%22%2C%0A%20%20%20%20orderDirection%3A%20desc%0A%20%20%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20voter%0A%20%20%20%20created%0A%20%20%20%20proposal%0A%20%20%20%20choice%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A)



