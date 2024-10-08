---
description: Learn what the space roles are and how you can assign them to users.
---

# Space roles

## What is a role?

Role is a set of permissions related to managing your space and its proposals which an account (wallet address) can be granted.

## Role permissions

### Controller

Controller of space has a **full control over the space settings** including managing the list of admins.

### Admin

Admin can **edit space settings** with the exception of the list of admin users and **archive proposals.**

### Moderator

Moderator can manage proposals within the Space and create new ones.

### Author

Author can **create proposals** regardless of their voting power and the proposal validation strategy.

## Assign a role to the user

### Controller

The controller is first assigned during the process of space creation. By default, it is the ENS domain controller. To learn more about this step, head to [#2.-set-the-space-controller-ens-text-record](create/#2.-set-the-space-controller-ens-text-record "mention").

There can be only **one controller** per space and can be updated **only by the current controller.**

To update the controller role head to the space settings on Snapshot and the **Advanced** tab. At the bottom of the page you'll find the **Danger zone** where you can change the controller:

<figure><img src="../../.gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>

Paste the address of the account you want to set as space controller in the pop-up window and click `Set`. It will trigger your wallet browser extension and ask you to sign a **transaction with a gas fee.**&#x20;

### **Admins, moderators, and authors**

To update the admins and authors lists head to the space settings on Snapshot and the **Members** tab.

You can add addresses one by one and choose their applicable role:

<figure><img src="../../.gitbook/assets/image (141).png" alt=""><figcaption></figcaption></figure>

