# Hub API

### Get all spaces

{% api-method method="get" host="https://hub.snapshot.page/api/spaces" path="" %}
{% api-method-summary %}
Get all spaces
{% endapi-method-summary %}

{% api-method-description %}
Gets all snapshot spaces
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "space-key": {},
  "space-key": {},
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% embed url="https://hub.snapshot.page/api/spaces" %}

### Get a single space

{% embed url="https://hub.snapshot.page/api/spaces/yam" %}

### Get all proposals for a space

{% embed url="https://hub.snapshot.page/api/balancer/proposals" %}

### Get all votes for a proposal

{% embed url="https://hub.snapshot.page/api/balancer/proposal/QmQpKL29E6ydTvC6p9NoEbTda9ddDkVtWe2YWpWK3NFYqq" %}

### Filter proposals

\(Will be standardised\)

{% embed url="https://github.com/balancer-labs/snapshot/blob/develop/src/views/Proposals.vue\#L97-L135" %}

### Get a proposal

You can get a proposal content from IPFS directly using the proposal id:[ https://ipfs.io/ipfs/QmQpKL29E6ydTvC6p9NoEbTda9ddDkVtWe2YWpWK3NFYqq](https://ipfs.io/ipfs/QmQpKL29E6ydTvC6p9NoEbTda9ddDkVtWe2YWpWK3NFYqq)

### Testnet hub

To see content from [https://demo.snapshot.page](https://demo.snapshot.page/#/) you need to query the testnet hub at this url: [https://testnet.snapshot.page](https://testnet.snapshot.page/)

