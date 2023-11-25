# Migrate or delete or a space

{% hint style="info" %}
Currently, migrating spaces still requires some manual effort.&#x20;
{% endhint %}

## Delete a space

If you are a space controller you can delete the space through Snapshot's interface directly.

{% hint style="danger" %}
Deleting a space **cannot be reversed** and you will **not be able to create a new space** with the same ENS domain name.
{% endhint %}

Head to your space settings and click **Advanced** tab in the sidebar on the left:

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

Scroll down to the bottom to the Danger Zone and click **Delete space:**

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-05 at 10.05.05.png" alt=""><figcaption></figcaption></figure>

Confirm the space deletion with the **space ID** and sign a message in your wallet.

That's it!&#x20;

## Migrate a space

Create a proposal on the source space as well as on the target space with the title "Migrate this space" from the respective controllers of the spaces (the Ethereum address that is registered in the `snapshot` ENS text record.

### One last step

Create a ticket on our [Discord server](https://discord.com/channels/707079246388133940/1090290400943677440/1102898691947376691).\
Please allow a couple of days for the workflow to be processed.
