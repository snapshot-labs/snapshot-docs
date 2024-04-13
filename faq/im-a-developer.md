# 👩‍💻 I'm a developer

##

<details>

<summary>Which networks are currently supported for voting with Gnosis Safe? </summary>

You can find the networks’ IDs here: [https://github.com/snapshot-labs/snapshot-relayer/blob/master/src/check.ts#L9](https://github.com/snapshot-labs/snapshot-relayer/blob/master/src/check.ts#L9)

</details>

<details>

<summary>Do we need to deploy an ENS contract on our custom network to be able to support Snapshot? </summary>

No, it’s not needed.

</details>

<details>

<summary>I think I found a vulnerability on Snapshot. Do you have a bug bounty?</summary>

Yes, we do. Please create report on the respective repository as showed below:

![](<../.gitbook/assets/image (64).png>)

</details>

<details>

<summary>Is it possible to test Snapshot without creating ENS on mainnet?</summary>

Yes. You can use [https://testnet.snapshot.org](https://testnet.snapshot.org) with an ENS domain on Goerli Testnet.

</details>

<details>

<summary>How does Snapshot use IPFS?</summary>

We use IPFS to pin the receipts of the votes. You can have a more detailed look at the [IPFS article](https://blog.ipfs.tech/2022-08-25-snapshot-ipfs-case-study/).

</details>

<details>

<summary>How to add a webhook? </summary>

Have a look at our documentation: [webhooks.md](../tools/webhooks.md "mention")

</details>

<details>

<summary>Can I use the Hub API without an API Key?</summary>

Yes you can, however we encourage everyone to apply for a key to ensure a continuous access to the service as the limits for the keyless access are much lower than with an API Key.

Learn more here: [api-keys.md](../tools/api/api-keys.md "mention")

</details>

<details>

<summary>Where can I generate an API Key for Hub GraphQL or Score API?</summary>

Head to [api-keys.md](../tools/api/api-keys.md "mention") to apply for a key and generate it for your own usage.

</details>

<details>

<summary>I'm trying to generate an API Key but I get an error that my address in not whitelisted. What should I do?</summary>

If you have filled in the [API Request Key Form](../tools/api/api-keys.md#api-key-request-form) please have some patience and wait for our direct response to the contact you provided in it.

If you haven't filled in the form yet then please do so and we will reach out to you shortly.

You can find more details about the process here: [api-keys.md](../tools/api/api-keys.md "mention")

</details>

<details>

<summary>Are there any limits for using the Hub GraphQL API?</summary>

Yes. Currently you can send 120 requests per every 20 seconds.

After September 12th the limits will be updated:

**🔓 No API Key:** 100 requests per minute.

**🔑 With the API Key:** 2 million requests per month.\


Learn how to apply and generate your API Key here: [api-keys.md](../tools/api/api-keys.md "mention")

</details>

<details>

<summary>Are there any limits for using snapshot.js or Score API?</summary>

Yes, same as for Hub API. When it comes to snapshot.js, refer to [#utils](../tools/snapshot.js.md#utils "mention")in Snapshot.js documentation.\
\
Make sure to generate your API Key to get higher usage limits. One key can be used for all API services and limits are counted individually per service.

</details>

### Snaphot.js&#x20;

<details>

<summary>I tried to submit a proposal with <code>snapshot.js</code>, but I get a “Wrong proposal format” error. What should I do?</summary>

There is a high chance that something is missing in the proposal’s payload. Make sure you are following the proposal schema defined here → [https://github.com/snapshot-labs/snapshot.js/blob/master/src/schemas/proposal.json](https://github.com/snapshot-labs/snapshot.js/blob/master/src/schemas/proposal.json)

</details>

<details>

<summary>I tried to submit a vote with <code>snapshot.js</code>, but I get the “Wrong vote format” error. What should I do?</summary>

Make sure that you’re following the vote schema defined here → [https://github.com/snapshot-labs/snapshot.js/blob/master/src/schemas/vote.json](https://github.com/snapshot-labs/snapshot.js/blob/master/src/schemas/vote.json).

A common mistake is using a wrong type (string instead of object) or extending a limit of a value (i.e. `reason` ).

</details>

<details>

<summary>Is there an alternative to <code>snapshot.js</code> in python?</summary>

No. If you are interested in building it, reach out to the team on the [#developer](https://discord.com/channels/707079246388133940/747050056422785055) channel!

</details>

<details>

<summary>How to use <code>snapshot.js</code> to create a space or update space settings?</summary>

Have a look at our documentation here: [#create-or-edit-a-space](../tools/snapshot.js.md#create-or-edit-a-space "mention")

</details>

### Adding a network

<details>

<summary>How can I add our network to Snapshot?</summary>

Follow our documentation to learn all the steps to add a new network to Snapshot: [#add-a-new-network](../developer-guides/networks.md#add-a-new-network "mention")

</details>

<details>

<summary>How can I check if the RPC node is a Full Archive Node?</summary>

You can send a request to the node and try to fetch the genesis block:

```
$ curl -H "content-type: application/json" -X POST --data '{"id":0,"jsonrpc":"2.0","method":"eth_getBalance","params":["<CONTRACT_HASH>","0x1"]}' <RPC_URL>
```

If you get a correct response without any errors, the Node is a Full Archive.

</details>

### Creating voting strategies

<details>

<summary>How to use our staking contract for voting? </summary>

You can browse through the existing staking strategies →[https://snapshot.org/#/?type=strategies\&q=stake](https://snapshot.org/#/?type=strategies\&q=stake).

If none of them work for you, have a look at the options below.

* In order to use the staking contract it has to have a `balanceOf` method which allows reading the balance of the staked tokens. You can use the[https://snapshot.org/#/strategy/erc20-balance-of](https://snapshot.org/#/strategy/erc20-balance-of) strategy with it.
* If your contract has a method getting the balance named differently, you can also use the[https://snapshot.org/#/strategy/contract-call](https://snapshot.org/#/strategy/contract-call) strategy.

</details>

<details>

<summary>How long will it take to merge my PR?</summary>

It usually takes around 72 hours so please have some patience. Once the PR is merged, you will also have to wait for a new release of the repository which can take another couple of days.

</details>

<details>

<summary>Is it possible to support delegation on our network?</summary>

Yes. If it’s not supported yet you can create a custom voting strategy to enable delegation on your network. You can see an example here →[https://snapshot.org/#/strategy/orbs-network-delegation](https://snapshot.org/#/strategy/orbs-network-delegation)



To learn more have a look at our documentation: [voting-strategy.md](../developer-guides/create-a-strategy/voting-strategy.md "mention")

</details>

<details>

<summary>I get <code>0</code> voting power in the delegation strategy playground but I can vote on real proposals.</summary>

Most probably you are missing the `delegationSpace` parameter. Make sure to provide the ENS domain of the space you are testing.

</details>

<details>

<summary>How to use our token from our network for voting?</summary>

If it doesn’t exist yet, you can create a new voting strategy. Have a look at our documentation to learn more: [voting-strategy.md](../developer-guides/create-a-strategy/voting-strategy.md "mention")

</details>
