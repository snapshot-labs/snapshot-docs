# Troubleshooting Voting Issues

If you're encountering a "Something went wrong, please try again later" error when voting on Snapshot, it’s usually due to a signing issue or wallet configuration.

## Common Fixes

### 1. Update MetaMask (Crucial)
If you are using MetaMask, ensure you are running **version 12.15.2 or higher**. Older versions contain a known bug that interferes with signing Snapshot votes.
- **How to check:** In MetaMask, go to **Settings > About**.
- **How to update:** Go to `chrome://extensions` in your browser and click "Update".

### 2. Activate the Sign Button
When the MetaMask signature popup appears, the "Sign" button may appear greyed out if you haven't scrolled through the entire message.
- **Action:** Scroll to the bottom of the signature request and click the **down arrow** (if applicable) until the **Sign** button becomes active.

### 3. Voting Power Latency
If your voting power is not reflecting correctly, it might be due to the time required to collect it from Ethereum.
- **Action:** If you see a message about "waiting for voting power to be collected," please wait 15 minutes and try again.

### 4. Eligibility Check
- **Action:** Open the proposal page and check your **Voting Power** display. If it shows 0, it means you did not hold the required token balance at the time the proposal snapshot was taken.
