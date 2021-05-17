# Get proposals

#### Input Arguments:

**`first: Int  
skip: Int  
orderBy: String  
orderDirection: OrderDirection  
where: ProposalWhere  
  
  
Type OrderDirection:  
asc or desc  
  
  
Type ProposalWhere:  
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
#### [Example GraphQL query](https://hub.snapshot.page/graphql?operationName=Proposals&query=query%20Proposals%20%7B%0A%20%20proposals%28%0A%20%20%20%20first%3A%2020%2C%0A%20%20%20%20skip%3A%200%2C%0A%20%20%20%20where%3A%20%7B%0A%20%20%20%20%20%20space_in%3A%20%5B%22balancer%22%2C%20%22yam.eth%22%5D%2C%0A%20%20%20%20%20%20state%3A%20%22closed%22%0A%20%20%20%20%7D%2C%0A%20%20%20%20orderBy%3A%20%22created%22%2C%0A%20%20%20%20orderDirection%3A%20desc%0A%20%20%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20title%0A%20%20%20%20body%0A%20%20%20%20choices%0A%20%20%20%20start%0A%20%20%20%20end%0A%20%20%20%20snapshot%0A%20%20%20%20state%0A%20%20%20%20author%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%20%20name%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)
{% endhint %}

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  proposals(
    first: 20,
    skip: 0,
    where: {
      space_in: ["balancer", "yam.eth"],
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
        "id": "QmZ21uS8tVucpaNq2LZCbZUmHhYYXunC1ZS2gPDNWwPWD9",
        "title": "Example Title",
        "body": "Example Body",
        "choices": [
          "Approve",
          "Reject"
        ],
        "start": 1620946800,
        "end": 1621206000,
        "snapshot": "12428834",
        "state": "closed",
        "author": "0xcc6A949DB9b26a7173648d50Cf7C55e800E6585B",
        "space": {
          "id": "balancer",
          "name": "Balancer"
        }
      },
      {
        "id": "QmUfV627SNpKTNqFc5bEdCXTLnHDF6KvgtbLcdmFmdqP3f",
        "title": "Example Title 2",
        "body": "Example Body 2",
        "choices": [
          "Approve",
          "Reject"
        ],
        "start": 1614985200,
        "end": 1615158000,
        "snapshot": "11980950",
        "state": "closed",
        "author": "0xcc6A949DB9b26a7173648d50Cf7C55e800E6585B",
        "space": {
          "id": "balancer",
          "name": "Balancer"
        }
      }
    ]
  }
}
```
{% endtab %}
{% endtabs %}

