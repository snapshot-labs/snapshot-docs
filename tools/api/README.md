---
description: >-
  You can use the Hub GraphQL API to create flexible queries for the data you
  need to integrate with Snapshot.
---

# API

{% hint style="info" %}
There is a limit of 60 requests per minute with the API, to get higher limits please apply for an API Key by following this guide: [api-keys.md](api-keys.md "mention")
{% endhint %}

## Hub GraphQL API - Explorer

You can run queries on Snapshot data using a GraphQL Explorer.

We have exposed an integrated development environment in the browser that includes docs, syntax highlighting, and validation errors. Click the link below to access the interface.

{% embed url="https://hub.snapshot.org/graphql" %}

![](<../../.gitbook/assets/image (53).png>)

## Endpoints

Production hub

```
https://hub.snapshot.org/graphql
```

Demo hub

```
https://testnet.hub.snapshot.org/graphql
```

## Queries

### Get a single space <a href="#space" id="space"></a>

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

Try on [GraphiQL](https://hub.snapshot.org/graphql?query=query%20%7B%0A%20%20space\(id%3A%20%22yam.eth%22\)%20%7B%0A%20%20%20%20id%0A%20%20%20%20name%0A%20%20%20%20about%0A%20%20%20%20network%0A%20%20%20%20symbol%0A%20%20%20%20members%0A%20%20%7D%0A%7D)

### Get multiple spaces <a href="#spaces" id="spaces"></a>

#### Arguments

first `number`\
skip `number`\
where:\
\- id`string`\
\- id\_in`array`\
orderBy `string`\
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

Try on [GraphiQL](https://hub.snapshot.org/graphql?query=%0Aquery%20Spaces%20%7B%0A%20%20spaces\(%0A%20%20%20%20first%3A%2020%2C%0A%20%20%20%20skip%3A%200%2C%0A%20%20%20%20orderBy%3A%20%22created%22%2C%0A%20%20%20%20orderDirection%3A%20asc%0A%20%20\)%20%7B%0A%20%20%20%20id%0A%20%20%20%20name%0A%20%20%20%20about%0A%20%20%20%20network%0A%20%20%20%20symbol%0A%20%20%20%20strategies%20%7B%0A%20%20%20%20%20%20name%0A%20%20%20%20%20%20params%0A%20%20%20%20%7D%0A%20%20%20%20admins%0A%20%20%20%20members%0A%20%20%20%20filters%20%7B%0A%20%20%20%20%20%20minScore%0A%20%20%20%20%20%20onlyMembers%0A%20%20%20%20%7D%0A%20%20%20%20plugins%0A%20%20%7D%0A%7D)

### Get a single proposal <a href="#proposal" id="proposal"></a>

#### Arguments <a href="#arguments" id="arguments"></a>

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
    scores
    scores_by_strategy
    scores_total
    scores_updated
    plugins
    network
    strategies {
      name
      network
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

Try on [GraphiQL](https://hub.snapshot.org/graphql?operationName=Proposal\&query=query%20Proposal%20%7B%0A%20%20proposal\(id%3A%22QmWbpCtwdLzxuLKnMW4Vv4MPFd2pdPX71YBKPasfZxqLUS%22\)%20%7B%0A%20%20%20%20id%0A%20%20%20%20title%0A%20%20%20%20body%0A%20%20%20%20choices%0A%20%20%20%20start%0A%20%20%20%20end%0A%20%20%20%20snapshot%0A%20%20%20%20state%0A%20%20%20%20author%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%20%20name%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)

### Get proposals <a href="#proposals" id="proposals"></a>

#### Arguments

first `number`\
skip `number`\
where:\
\- id`string`\
\- id\_in`array`\
\- space:`string`\
\- space\_in:`array`\
\- author:`string`\
\- author\_in:`array`\
\- network: `string`\
\- network\_in: `array`\
\- state: `array`\
orderBy `string`\
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
    scores
    scores_by_strategy
    scores_total
    scores_updated
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

Try on [GraphiQL](https://hub.snapshot.org/graphql?operationName=Proposals\&query=query%20Proposals%20%7B%0A%20%20proposals%20\(%0A%20%20%20%20first%3A%2020%2C%0A%20%20%20%20skip%3A%200%2C%0A%20%20%20%20where%3A%20%7B%0A%20%20%20%20%20%20space\_in%3A%20%5B%22yam.eth%22%5D%2C%0A%20%20%20%20%20%20state%3A%20%22closed%22%0A%20%20%20%20%7D%2C%0A%20%20%20%20orderBy%3A%20%22created%22%2C%0A%20%20%20%20orderDirection%3A%20desc%0A%20%20\)%20%7B%0A%20%20%20%20id%0A%20%20%20%20title%0A%20%20%20%20body%0A%20%20%20%20choices%0A%20%20%20%20start%0A%20%20%20%20end%0A%20%20%20%20snapshot%0A%20%20%20%20state%0A%20%20%20%20author%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%20%20name%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)

### Get a single vote <a href="#vote" id="vote"></a>

{% hint style="warning" %}
Choices are indexed 1-based. The first choice has index 1.
{% endhint %}

#### Arguments <a href="#arguments" id="arguments"></a>

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
    vp
    vp_by_strategy
    vp_state
    created
    proposal {
      id
    }
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
      "proposal": {
        "id": "QmPvbwguLfcVryzBRrbY4Pb9bCtxURagdv1XjhtFLf3wHj"
      },
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

Try on [GraphiQL](https://hub.snapshot.org/graphql?operationName=Vote\&query=query%20Vote%20%7B%0A%20%20vote%20\(%0A%20%20%20%20id%3A%20%22QmeU7ct9Y4KLrh6F6mbT1eJNMkeQKMSnSujEfMCfbRLCMp%22%0A%20%20\)%20%7B%0A%20%20%20%20id%0A%20%20%20%20voter%0A%20%20%20%20created%0A%20%20%20%20proposal%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%7D%0A%20%20%20%20choice%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)

### Get votes <a href="#votes" id="votes"></a>

{% hint style="warning" %}
Choices are indexed 1-based. The first choice has index 1.
{% endhint %}

#### Arguments

first `number`\
skip `number`\
where:\
\- id`string`\
\- id\_in`array`\
\- space:`string`\
\- space\_in:`array`\
\- voter:`string`\
\- voter\_in:`array`\
\- proposal: `string`\
\- proposal\_in: `array`\
orderBy `string`\
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
    vp
    vp_by_strategy
    vp_state
    created
    proposal {
      id
    }
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
        "proposal": {
          "id": "QmPvbwguLfcVryzBRrbY4Pb9bCtxURagdv1XjhtFLf3wHj"
        },
        "choice": 1,
        "space": {
          "id": "spookyswap.eth"
        }
      },
      {
        "id": "QmZ2CV86QH6Q6z7L6g7yJWS3HfgD9aQ3uTYYMXkMa5trHf",
        "voter": "0x2686EaD94C5042e56a41eDde6533711a4303CC52",
        "created": 1621181827,
        "proposal": {
          "id": "QmPvbwguLfcVryzBRrbY4Pb9bCtxURagdv1XjhtFLf3wHj"
        },
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

Try on [GraphiQL](https://hub.snapshot.org/graphql?operationName=Votes\&query=query%20Votes%20%7B%0A%20%20votes%20\(%0A%20%20%20%20first%3A%201000%0A%20%20%20%20skip%3A%200%0A%20%20%20%20where%3A%20%7B%0A%20%20%20%20%20%20proposal%3A%20%22QmPvbwguLfcVryzBRrbY4Pb9bCtxURagdv1XjhtFLf3wHj%22%0A%20%20%20%20%7D%0A%20%20%20%20orderBy%3A%20%22created%22%2C%0A%20%20%20%20orderDirection%3A%20desc%0A%20%20\)%20%7B%0A%20%20%20%20id%0A%20%20%20%20voter%0A%20%20%20%20created%0A%20%20%20%20proposal%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%7D%0A%20%20%20%20choice%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A)

### Get voting power

#### Arguments

voter `string`\
space `string`\
proposal `string`

#### Example

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  vp (
    voter: "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7"
    space: "fabien.eth"
    proposal: "0x4903dd16990de740b7dc7effe1a0bc8bd49a510a04992bc30596c9a0d0f69455"
  ) {
    vp
    vp_by_strategy
    vp_state
  } 
}
```
{% endtab %}

{% tab title="Response" %}
```
{
  "data": {
    "vp": {
      "vp": 1,
      "vp_by_strategy": [
        1
      ],
      "vp_state": "final"
    }
  }
}
```
{% endtab %}
{% endtabs %}

Try on [GraphiQL](https://hub.snapshot.org/graphql?query=query%20%7B%0A%20%20vp%20\(%0A%20%20%20%20voter%3A%20%220xeF8305E140ac520225DAf050e2f71d5fBcC543e7%22%0A%20%20%20%20space%3A%20%22fabien.eth%22%0A%20%20%20%20proposal%3A%20%220x4903dd16990de740b7dc7effe1a0bc8bd49a510a04992bc30596c9a0d0f69455%22%0A%20%20\)%20%7B%0A%20%20%20%20vp%0A%20%20%20%20vp\_by\_strategy%0A%20%20%20%20vp\_state%0A%20%20%7D%20%0A%7D%0A)

### Get follows <a href="#follows" id="follows"></a>

#### Arguments

first `number`\
skip `number`\
where:\
\- id`string`\
\- id\_in`array`\
\- space:`string`\
\- space\_in:`array`\
\- follower:`string`\
\- follower\_in:`array`\
orderBy `string`\
orderDirection `asc` or `desc`

#### Example

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  follows(
    first: 10,
    where: {
      follower: "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7"
    }
  ) {
    follower
    space {
      id
    }
    created
  }
}
```
{% endtab %}

{% tab title="Response" %}
```javascript
{
  "data": {
    "follows": [
      {
        "follower": "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7",
        "space": {
          "id": "gnosis.eth"
        },
        "created": 1629732280
      },
      {
        "follower": "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7",
        "space": {
          "id": "aavegotchi.eth"
        },
        "created": 1629725098
      },
      {
        "follower": "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7",
        "space": {
          "id": "yam.eth"
        },
        "created": 1629723970
      },
      {
        "follower": "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7",
        "space": {
          "id": "balancer.eth"
        },
        "created": 1629723960
      }
    ]
  }
}
```
{% endtab %}
{% endtabs %}

Try on [GraphiQL](https://hub.snapshot.org/graphql?query=query%20%7B%0A%20%20follows\(%0A%20%20%20%20first%3A%2010%2C%0A%20%20%20%20where%3A%20%7B%0A%20%20%20%20%20%20follower%3A%20%220xeF8305E140ac520225DAf050e2f71d5fBcC543e7%22%0A%20%20%20%20%7D%0A%20%20\)%20%7B%0A%20%20%20%20follower%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%7D%0A%20%20%20%20created%0A%20%20%7D%0A%7D)

### Get users

#### Arguments

first `number`\
skip `number`\
where:\
\- id:`string`\
\- id\_in:`array`\
orderBy `string`\
orderDirection `asc` or `desc`

#### Example

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  users(first: 10, where: { id_in: ["0xF78108c9BBaF466dd96BE41be728Fe3220b37119"] }) {
    id
    name
    about
    avatar
  }
}
```
{% endtab %}

{% tab title="Response" %}
```
{
  "data": {
    "users": [
      {
        "id": "0xF78108c9BBaF466dd96BE41be728Fe3220b37119",
        "name": "John Doe",
        "about": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda asperiores a quis accusamus tenetur sed",
        "avatar": "ipfs://QmNXTswsKJEHHEmGCgQKEAqbq3ib1eBCd4U8SRPgcuVJBX"
      }
    ]
  }
}
```
{% endtab %}
{% endtabs %}

Try on [GraphiQL](https://hub.snapshot.org/graphql?query=query%20%7B%0A%20%20users\(first%3A%2010%2C%20where%3A%20%7B%20id\_in%3A%20%5B%220xF78108c9BBaF466dd96BE41be728Fe3220b37119%22%5D%20%7D\)%20%7B%0A%20%20%20%20id%0A%20%20%20%20name%0A%20%20%20%20about%0A%20%20%20%20avatar%0A%20%20%7D%0A%7D%0A)

### Get roles

#### Arguments

first `number`\
skip `number`\
where:\
\- address:`string`\
orderBy `string`\
orderDirection `asc` or `desc`

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  roles(where:{address:"0xE029Ef62e47E394BC852EFf633eB5aa4A223ECa6"}) {
    space
    permissions
  }
}
```
{% endtab %}

{% tab title="Response" %}
```graphql
{
  "data": {
    "roles": [
      {
        "space": "fabien.eth",
        "permissions": [
          "moderator"
        ]
      },
      {
        "space": "zuzazuber.eth",
        "permissions": [
          "moderator"
        ]
      }
    ]
  }
}
```
{% endtab %}
{% endtabs %}

Try on GraphiQL

### Aliases

TBD

### Get messages <a href="#messages" id="messages"></a>

Messages are all the actions (votes, proposals, space settings etc..) that was confirmed on Snapshot, it also include the order on which these actions were confirmed with the field "mci". These messages can be used to replay the whole Snapshot hub API.

#### Arguments

first `number`\
skip `number`\
where:\
\- timestamp`string`\
\- space`array`\
\- space\_in:`array`\
\- type:`string`\
\- type\_in:`string`\
orderBy `string`\
orderDirection `asc` or `desc`

#### Example

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  messages (
    first: 20
    where: { space: "ens.eth" }
    orderBy: "mci"
    orderDirection: desc
  ) {
    id
    address
    ipfs
    receipt
    type
    mci
  }
}

```
{% endtab %}

{% tab title="Response" %}
```javascript
{
  "data": {
     "messages": [
      {
        "id": "0x7d99e11ffe3a333229bdcda59866bc5b66b0b7e5c4b5353862a3b8ccbfa26c83",
        "address": "0xdbB1740e424C41E935599634828f5E5c4dF23D43",
        "ipfs": "bafkreiduchkd35btpv3uttrg3f2kx3g52uh44tiruawip6xlgvjbcuo4w4",
        "receipt": "0xaa4d557085872ed82b8bfba5af4247650395eda46ed61672d940eabc74bcde67415db974361f4b24361565d2f9ee6ee636ae935a1dc830c207204ea29ad498741b",
        "type": "follow"
        "mci": 1345000
      },
      ...
    ]
  }
}
```
{% endtab %}
{% endtabs %}

Try on [GraphiQL](https://hub.snapshot.org/graphql?query=query%20%7B%0A%20%20messages%20\(%0A%20%20%20%20first%3A%2020%0A%20%20%20%20where%3A%20%7B%20space%3A%20%22ens.eth%22%20%7D%0A%20%20%20%20orderBy%3A%20%22timestamp%22%0A%20%20%20%20orderDirection%3A%20desc%0A%20%20\)%20%7B%0A%20%20%20%20id%0A%20%20%20%20address%0A%20%20%20%20ipfs%0A%20%20%20%20receipt%0A%20%20%20%20type%0A%20%20%7D%0A%7D%0A)
