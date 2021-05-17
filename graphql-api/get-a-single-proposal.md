# Get a single proposal

#### Input Arguments:

**`id: String`**

{% hint style="info" %}
#### [Example GraphQL query](https://hub.snapshot.page/graphql?operationName=Proposal&query=query%20Proposal%20%7B%0A%20%20proposal%28id%3A%22QmZ21uS8tVucpaNq2LZCbZUmHhYYXunC1ZS2gPDNWwPWD9%22%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20title%0A%20%20%20%20body%0A%20%20%20%20choices%0A%20%20%20%20start%0A%20%20%20%20end%0A%20%20%20%20snapshot%0A%20%20%20%20state%0A%20%20%20%20author%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%20%20name%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)
{% endhint %}

{% tabs %}
{% tab title="Request" %}
```graphql
query {
  proposal(id:"QmZ21uS8tVucpaNq2LZCbZUmHhYYXunC1ZS2gPDNWwPWD9") {
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
    "proposal": {
      "id": "QmZ21uS8tVucpaNq2LZCbZUmHhYYXunC1ZS2gPDNWwPWD9",
      "title": "Example Title",
      "body": "Example Body"
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
    }
  }
}
```
{% endtab %}
{% endtabs %}

