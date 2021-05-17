# GraphQL API

Try the GraphQL API here:

{% embed url="https://hub.snapshot.page/graphql" %}

![](.gitbook/assets/image.png)

### Get a single space

GraphQL query

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

