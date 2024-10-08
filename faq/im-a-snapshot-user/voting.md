# 🗳️ Voting

<details>

<summary><strong>I delegated my voting power but would like to take it back. How can I do it?</strong></summary>

You can remove your delegations by going to [https://testnet.snapshot.org/#/delegate](https://testnet.snapshot.org/#/delegate) and clicking the ❌ for the delegations you wish to remove.

![](<../../.gitbook/assets/image (40).png>)

Moreover, if you want to override your delegate’s vote on a proposal using [the delegation strategy](https://snapshot.org/#/strategy/delegation) you can simply cast your own vote and it will override the delegate’s vote. If the delegation happened on-chain, then head to the delegation portal of the project you’re looking for and redelegate there.

</details>

<details>

<summary><strong>Can I explain the reason for my vote somewhere?</strong></summary>

Yes, apart from the proposals using shielded voting.

You can add a short explanation when casting a vote:

![](<../../.gitbook/assets/image (29).png>)

</details>

<details>

<summary><strong>I get “Your voting power could not be calculated due to misconfigured strategy or unresponsive RPC node”. What should I do?</strong></summary>

This issue is related to either space settings or the failure of the external infrastructure that Snapshot relies on. We recommend to wait 15 minutes before trying again. If the error persists, please contact our support on [Help Center](https://help.snapshot.org/en/) with the following details:

* URL of the proposal you were trying to vote on
* The error message you received (in this case: “Your voting power could not be calculated due to misconfigured strategy or unresponsive RPC node”)
* Did you wait for 15 minutes before trying to cast the vote again

</details>

<details>

<summary>How can I export the complete voting to excel?</summary>

Go to the proposals page and click the download icon to get a CSV file. You can open it directly in excel or import it in the Google Sheets.

![](<../../.gitbook/assets/image (74).png>)

</details>

<details>

<summary>Can I vote with a Safe/Multisig?</summary>

Yes. You can find more details in our documentation here: [using-safe-multi-sig.md](../../user-guides/using-safe-multi-sig.md "mention")

</details>

<details>

<summary>I'm having issues when voting with Safe. What's wrong?</summary>

Make sure that your wallet is on the same network as the Space. Go to Space page > Settings > Strategies to check what is the Space's network.

</details>

<details>

<summary>There is a proposal that's open until tomorrow and I have a new token that was minted today, after the proposal’s creation. Can that token be used to vote?</summary>

No. Snapshot calculates the voting power on the basis of proposal creation time. If the token has not been stored in the wallet before the proposal was created it will not be taken into account.

</details>

<details>

<summary>I get “Oops, failed to check voting power”. What should I do?</summary>

This issue is related to either space settings or the failure of the external infrastructure that Snapshot relies on. We recommend to wait 15 minutes before trying again. If the error persists, contact our support on [Help Center](https://help.snapshot.org/en/) with the following details:

* URL of the proposal you were trying to vote on
* The error message you received (in this case: “Oops, failed to check voting power”)
* Did you wait for 15 minutes before trying to cast the vote again

</details>

<details>

<summary><strong>Can I vote on any proposal?</strong></summary>

No. Your eligibility to vote depends on the voting strategies defined by the space and usually requires holding the organization’s token. Some spaces allow anyone to vote, however this is a rare case.&#x20;

You can read more about the voting strategies in our documentation: [voting-strategies.md](../../user-guides/strategies/voting-strategies.md "mention")

</details>

<details>

<summary>Can I change my vote?</summary>

Yes, you can change your vote as long as the voting period is still active. Simply cast a new vote on the same proposal, and it will overwrite your previous vote.

</details>
