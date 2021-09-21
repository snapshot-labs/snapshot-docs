# Delegation

## **When I added delegation, it appears to not allow anyone to vote.**

Delegation strategy syntax example:

```text
{
  "symbol": "Shark",
  "strategies": [
    {
      "name": "erc20-balance-of",
      "params": {
        "address": "0x232a...",
        "symbol": "Shark",
        "decimals": 18
      }
    }
  ]
}
```

if you pass something like this, it will calculate balance of this token 0x232a... that delegated to an address

## 



