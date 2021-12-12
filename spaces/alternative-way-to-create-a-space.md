# Alternative way to create a space

If you do not want to have the wallet control your settings, you can follow the steps below to create a space on Snapshot.

### **Drawbacks**

* You will not be able to change settings from the UI
* Every time you want to change the settings, you will need to broadcast a new transaction

### **How to Create Space**

* Create a JSON file for your settings on Snapshot. The format of the JSON file could be as follows: **** [https://github.com/snapshot-labs/snapshot.js/blob/master/test/examples/space.json](https://github.com/snapshot-labs/snapshot.js/blob/master/test/examples/space.json)
* Store the JSON file on IPFS
* Use the IPFS link on the ENS text record. This will make the ENS owner the only controller of the settings. ****&#x20;

![](https://lh6.googleusercontent.com/qfA-Pj7o2Fvld76V2gZIJm9U1V0uRBgNdedfxU4iKjGDfE3cHH7KLMx26eawZPD0Zl8j3H7AAfFsToDdl9ViQ5Y7WyI8FACqVlkc5JG9zwcyZg877KmnH6cf2vleHnn-icWLGTg=s0)

* You can check if your space is valid from the github link below [https://github.com/snapshot-labs/snapshot.js/blob/a0adc547aa0922aa6abd35708a4a292048bca6a2/test/schema.ts#L4](https://github.com/snapshot-labs/snapshot.js/blob/a0adc547aa0922aa6abd35708a4a292048bca6a2/test/schema.ts#L4)
*   Once the above transaction is successful, go to the below link to update the space in Snapshot:

    `https://hub.snapshot.org/api/spaces/`**`<ENS DOMAIN>`**`/poke`