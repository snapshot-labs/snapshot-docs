
# Aliases

When querying a single field with different arguments, soon enough you’ll run into this issue:  GraphQl does not allow you to  query the same field with different arguments. This is where aliases come along. With aliases, you can re-name the results of a query to your interest. This is also helpful for the client-side data fetching. 

If you try to run the code below, it will throw this error ```      "message": "Fields \"space\" conflict because they have differing arguments. Use different aliases on the fields to fetch both if this was intentional.",```

{% tabs %} {% tab title="Request" %}
```
query {
  space(id: "ens.eth") {
    id
    name
    about
    network
    symbol
    members
  } 
  space(id: "uniswap") {
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

    {  "errors": [
    {
      "message": "Fields \"space\" conflict because they have differing arguments. Use different aliases on the fields to fetch both if this was intentional.",
      "locations": [
        {
          "line": 2,
          "column": 3
        },
        {
          "line": 10,
          "column": 3
        }
      ]
    }
 
{% endtab %} {% endtabs %}

For fixing this issue, you can use aliases to re-name the results 
***Example***
{% tabs %} {% tab title="Request" %}
```
query {
  ensSpace: space(id: "ens.eth") {
    id
    name
    about
    network
    symbol
    members
  } 
  uniswapSpace: space(id: "uniswap") {
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
```
{
  "data": {
    "ensSpace": {
      "id": "ens.eth",
      "name": "ENS",
      "about": "",
      "network": "1",
      "symbol": "ENS",
      "members": [
        "0x5A384227B65FA093DEC03Ec34e111Db80A040615",
        "0xb8c2C29ee19D8307cb7255e1Cd9CbDE883A267d5",
        "0x983110309620D911731Ac0932219af06091b6744",
        "0x866B3c4994e1416B7C738B9818b31dC246b95eEE",
        "0x0904Dac3347eA47d208F3Fd67402D039a3b99859",
        "0x9297A132AF2A1481441AB8dc1Ce6e243d879eaFD",
        "0x75cac0CEb8A39DdB4942A83AD2aAfaF0C2A3e13f"
      ]
    },
    "uniswapSpace": {
      "id": "uniswap",
      "name": "Uniswap",
      "about": "Only delegated UNI may be used to vote on proposals. You can delegate to yourself or another address here: https://app.uniswap.org/#/vote",
      "network": "1",
      "symbol": "UNI",
      "members": []
    }
  }
}
```
{% endtab %} {% endtabs %}
