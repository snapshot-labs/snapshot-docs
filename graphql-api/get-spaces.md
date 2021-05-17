# Get spaces

#### Input Arguments:

**`first: Int  
skip: Int  
orderBy: String  
orderDirection: OrderDirection  
  
Type OrderDirection:  
asc or desc`**

{% hint style="info" %}
#### [Example GraphQL query](https://hub.snapshot.page/graphql?query=%0Aquery%20Spaces%20%7B%0A%20%20spaces%28%0A%20%20%20%20first%3A%2020%2C%0A%20%20%20%20skip%3A%200%2C%0A%20%20%20%20orderBy%3A%20%22created%22%2C%0A%20%20%20%20orderDirection%3A%20asc%0A%20%20%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20name%0A%20%20%20%20about%0A%20%20%20%20network%0A%20%20%20%20symbol%0A%20%20%20%20strategies%20%7B%0A%20%20%20%20%20%20name%0A%20%20%20%20%20%20params%0A%20%20%20%20%7D%0A%20%20%20%20admins%0A%20%20%20%20members%0A%20%20%20%20filters%20%7B%0A%20%20%20%20%20%20minScore%0A%20%20%20%20%20%20onlyMembers%0A%20%20%20%20%7D%0A%20%20%20%20plugins%0A%20%20%7D%0A%7D)
{% endhint %}

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



