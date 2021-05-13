# Rest API

### Get all spaces

{% embed url="https://hub.snapshot.page/api/spaces" %}

### Get a single space

{% embed url="https://hub.snapshot.page/api/spaces/yam" %}

### Get all proposals of a space

{% embed url="https://hub.snapshot.page/api/balancer/proposals" %}

### Get all votes of a proposal

{% embed url="https://hub.snapshot.page/api/balancer/proposal/QmQpKL29E6ydTvC6p9NoEbTda9ddDkVtWe2YWpWK3NFYqq" %}

### Get a proposal

You can get a proposal content from IPFS directly using the proposal id:[ https://ipfs.io/ipfs/QmQpKL29E6ydTvC6p9NoEbTda9ddDkVtWe2YWpWK3NFYqq](https://ipfs.io/ipfs/QmQpKL29E6ydTvC6p9NoEbTda9ddDkVtWe2YWpWK3NFYqq)

{% api-method method="get" host="https://hub.snapshot.page/api/voters?from=1608500000&to=1609500000&spaces=balancer,yam.eth" path="" %}
{% api-method-summary %}
List of voters
{% endapi-method-summary %}

{% api-method-description %}
Get a list of all voters from specific spaces for a specific period.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="from" type="number" required=false %}
Timestamp from
{% endapi-method-parameter %}

{% api-method-parameter name="to" type="number" required=false %}
Timestamp to
{% endapi-method-parameter %}

{% api-method-parameter name="spaces" type="string" required=false %}
Spaces ids separated with commas
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
[
  {
    "address": "0xaaAb28818F71C96E13518025Cc063A1CA6F4Fd58",
    "timestamp": 1609109064,
    "space": "yam.eth"
  },
  {
    "address": "0xFdbE95Ec43ca5C77929a1c30E9Ee588c28c5C9B4",
    "timestamp": 1609102537,
    "space": "yam.eth"
  },
  ...
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Testnet hub

To see content from [https://demo.snapshot.page](https://demo.snapshot.page/#/) you need to query the testnet hub at this url: [https://testnet.snapshot.page](https://testnet.snapshot.page/)

