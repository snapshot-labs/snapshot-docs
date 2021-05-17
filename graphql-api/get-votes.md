# Get votes

#### Input Arguments:

**`first: Int  
skip: Int  
orderBy: String  
orderDirection: OrderDirection  
where: VoteWhere  
  
  
Type OrderDirection:  
asc or desc  
  
  
Type VoteWhere:  
id: String  
id_in: [String]  
space: String  
space_in: [String]  
author: String  
author_in: [String]  
network: String  
network_in: [String]  
state: [String]`**

{% hint style="info" %}
#### [Example GraphQL query](https://hub.snapshot.page/graphql?operationName=Votes&query=query%20Votes%20%7B%0A%20%20votes%20%28%0A%20%20%20%20first%3A%201000%0A%20%20%20%20skip%3A%200%0A%20%20%20%20where%3A%20%7B%0A%20%20%20%20%20%20proposal%3A%20%22QmPvbwguLfcVryzBRrbY4Pb9bCtxURagdv1XjhtFLf3wHj%22%0A%20%20%20%20%7D%0A%20%20%20%20orderBy%3A%20%22created%22%2C%0A%20%20%20%20orderDirection%3A%20desc%0A%20%20%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20voter%0A%20%20%20%20created%0A%20%20%20%20proposal%0A%20%20%20%20choice%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A)
{% endhint %}

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
      {
        "id": "QmYpUghFNYiS5y2vqNzJfczJmhXCMbzq17PJ1jjaP3BYib",
        "voter": "0xF6F7a399405ca3A6434b390d0221353748cf1884",
        "created": 1621175990,
        "proposal": "QmPvbwguLfcVryzBRrbY4Pb9bCtxURagdv1XjhtFLf3wHj",
        "choice": 1,
        "space": {
          "id": "spookyswap.eth"
        }
      }
    ]
  }
}
```
{% endtab %}
{% endtabs %}

