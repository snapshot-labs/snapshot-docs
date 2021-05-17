# Get single vote

#### Input Arguments:

**`id: String`**

{% hint style="info" %}
#### [Example GraphQL query](https://hub.snapshot.page/graphql?operationName=Proposal&query=query%20Proposal%20%7B%0A%20%20proposal%28id%3A%22QmZ21uS8tVucpaNq2LZCbZUmHhYYXunC1ZS2gPDNWwPWD9%22%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20title%0A%20%20%20%20body%0A%20%20%20%20choices%0A%20%20%20%20start%0A%20%20%20%20end%0A%20%20%20%20snapshot%0A%20%20%20%20state%0A%20%20%20%20author%0A%20%20%20%20space%20%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%20%20name%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)
{% endhint %}

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

