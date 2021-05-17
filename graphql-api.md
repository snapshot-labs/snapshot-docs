# GraphQL API

Try the GraphQL API here:

{% embed url="https://hub.snapshot.page/graphql" %}

![](.gitbook/assets/image.png)

### Get a single space

[GraphQL query](https://hub.snapshot.page/graphql?query=query%20%7B%0A%20%20space%28id%3A%20%22yam.eth%22%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20name%0A%20%20%20%20about%0A%20%20%20%20network%0A%20%20%20%20symbol%0A%20%20%20%20members%0A%20%20%7D%0A%7D)

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

Returns

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

