# ⚙️ Space settings

<details>

<summary>It is possible to create a space with a multi-sig account?</summary>

Yes. In order to do so navigate to [https://app.safe.global](https://app.safe.global) and select Snapshot in the `Apps` tab. Your multi-sig address will connect to Snapshot and allow you to create spaces, proposals and vote.

</details>

<details>

<summary>I lost access to my ENS domain which was used to register a space on Snapshot. What should I do?</summary>

If you are still a controller of the space you can apply to delete your space or migrate the current space to another one with different ENS. Have a look at our documentation for more details: [migrate-or-delete.md](../../user-guides/spaces/migrate-or-delete.md "mention")

</details>

<details>

<summary>How can I differentiate settings for proposals and voting?</summary>

You can use sub-spaces on Snapshot. This solution allows you to link multiple spaces and set different settings for each of them depending on your needs. Have a look at our documentation to learn more: [sub-spaces.md](../../user-guides/spaces/sub-spaces.md "mention")

</details>

<details>

<summary>Can I change the name of my space?</summary>

Yes. You can do it in the space settings.&#x20;

Do not confuse it with changing the `ID` or the ENS domain for your space. To do that, you need to migrate the space. You can read more about changing the ENS domain in our documentation: [migrate-or-delete.md](../../user-guides/spaces/migrate-or-delete.md "mention")

</details>

<details>

<summary>How can I verify my space?</summary>

There is a list of requirements you have to meet. Have a look at our documentation to learn more: [get-verified.md](../../user-guides/spaces/get-verified.md "mention")

</details>

<details>

<summary>How long does it take to verify a space?</summary>

The process can take up to 72 hours.

</details>

<details>

<summary>I made a mistake with my space settings and I want to cancel existing votes. How can I do it?</summary>

You cannot invalidate existing votes. However you can delete the proposal.

If you are an admin of the space or proposal’s creator you can delete the current proposal by clicking `Delete` on the proposal’s page:

![](<../../.gitbook/assets/image (46).png>)

Then change the space settings and make sure to persist the changes.

Once the settings have been updated you can recreate the proposal from scratch.

</details>

<details>

<summary>Can I customize the appearance of my Snapshot space?</summary>

Yes, you can customize the appearance of your Snapshot space to some extent by setting a custom skin, which allows you to change the colors of your space. This customization feature is available for spaces using the custom domains setting.

</details>

<details>

<summary>Your proposal cannot be submitted due to a missing Voting Validation rule required with the "ticket" strategy. What does it mean?</summary>

![](<../../.gitbook/assets/image (58).png>)

If your space is using only a [ticket](https://snapshot.org/#/strategy/ticket) Voting Strategy you are required to set a Voting Validation to minimize the risk of spam votes on your proposals. \
Without it, hackers can easily create multiple accounts (each getting 1 Voting Power) and take the voting process over.\
\
Have a read here to learn how to set it up: [#voting-validation-in-space-settings](../../user-guides/strategies/validation-strategies.md#voting-validation-in-space-settings "mention")

</details>

<details>

<summary>My space is no longer verified. Why is that?</summary>

Verification status is valid as long as the space meets all requirements. Make sure you meet all the requirements defined [here](../../user-guides/spaces/get-verified.md#how-to-get-your-space-verified) and contact our support on [Help Center](https://help.snapshot.org/en/) to regain the space verification.

</details>

<details>

<summary>My space is hibernated. Why?</summary>

Spaces are put in hibernation mode after 12 months of inactivity. To learn more head to [space-hibernation.md](../../user-guides/spaces/space-hibernation.md "mention")

</details>

<details>

<summary>How can I get my space out of hibernation?</summary>

As a space controller or an admin you can reactive the space through the space settings by clicking `Reactivate space` button. More information can be found in [space-hibernation.md](../../user-guides/spaces/space-hibernation.md "mention")

</details>

<details>

<summary>Why can't I create a new space with my previous deleted space ENS name ?</summary>

Deleting a space does not release its attached ENS name, so you can not create a new space with the same ENS name. Head [Space deletion](../../user-guides/spaces/migrate-or-delete.md) to to learn more.

If you wish to retain the same ENS domain for you new space, you could create a new space under a [subdomain](https://wagmi.tips/guides/ens-subdomain/) of your previous ENS name.

</details>
