---
description: Combine Gnosis Safe with Snapshot using SafeSnap plugin.
---

# SafeSnap: Reality

Combining the Gnosis Safe with Snapshot, SafeSnap enables decentralized execution of crypto governance proposals, through on-chain execution of off-chain votes.\


## How does it work? <a href="#e132" id="e132"></a>

SafeSnap plugin is an oracle-based solution which works together with Gnosis Safe and Snapshot in the following way:

<figure><img src="../../.gitbook/assets/image (133).png" alt=""><figcaption></figcaption></figure>

* A Gnosis Safe module, where anyone can create a new proposal: an array of multisend transaction payloads.
* Each proposal is a `Reality.eth` question asking if (1) the linked Snapshot proposal passed, (2) did the proposal include the payload, and (3) does the payload do what the proposal describes.
* If the proposal passes on Snapshot, then `Reality.eth` should resolve to the same outcome, and after a 24 hour cooldown period, the proposal’s transactions are executable by anyone.
* Reality uses an ERC-20 token (a given DAO’s governance token) for the bond. The minimum bond can be set by way of a proposal to the DAO.
* The UI is a Snapshot plugin, in which users can enter an array of tx-payloads to be executed sequentially by the Gnosis Safe if the proposal passes. Once the proposal has passed, the Reality.eth question has resolved, and the 24 hour cooldown period is over, there is the option on the Snapshot interface to trigger each of the multisend transactions in the proposal.

## Setup

Follow the official Zodiac guide on how to setup a SafeSnap for your project.\
\
**I'm a non-dev operator (space controller or admin):**

{% embed url="https://zodiac.wiki/index.php/Reality_Module:_Operator_Tutorial" %}

**I'm a developer:**

{% embed url="https://github.com/gnosis/zodiac-module-reality/blob/main/docs/setup_guide.md" %}

**More information:**

{% embed url="https://zodiac.wiki/index.php/Category:Reality_Module" %}

## Security recommendations

In order to ensure maximal safety we recommend to define several paremeters for your setup:

* Set a **substantial bond** for an answer
* Select an **arbitrator**
* Select a **long cooldown**
* Set up a **monitoring infrastructure** for questions

## Additional resources

Learn more about SafeSnape here:

{% embed url="https://blog.gnosis.pm/introducing-safesnap-the-first-in-a-decentralized-governance-tool-suite-for-the-gnosis-safe-ea67eb95c34f" %}

{% embed url="https://www.youtube.com/watch?v=ncDeEuJfVkg" %}

