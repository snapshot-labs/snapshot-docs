# Mana

Mana is a meta-transaction relayer that allows users to interact with Snapshot X without paying gas fe&#x65;**.** This service works in conjunction with signature based Snapshot X [authenticators](broken-reference). Users sign a meta transaction in the SX UI and then the relayer submits each encoded transaction along with its signature to the signature authenticator. If the signature is valid, then the transaction will be forwarded to the relevant space contract.&#x20;

The system included a mechanism that allows DAOs to fund the transactions sent by the relayer, enabling the free end user experience. However importantly, users can directly interact with Snapshot X and therefore do not rely on trusting the relayer to not censor votes. Additionally, Anyone can run a relayer if they want to take over the sponsoring of transactions.

Note that currently Mana only supports proposal creation, proposal updates, and vote casting transactions. It does not currently support proposal execution or space controller actions.&#x20;

#### GitHub

[https://github.com/snapshot-labs/sx-monorepo/tree/master/apps/mana](https://github.com/snapshot-labs/sx-monorepo/tree/master/apps/mana)

#### Public API

[https://mana.box](https://mana.box)
