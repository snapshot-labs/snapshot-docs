# Execution strategies

Execution Strategies have two key roles:

1. **Determining the status of a proposal at any time**,&#x20;
2. **Executing the payload of a proposal if it has been accepted**.&#x20;

Each proposal should have an Execution strategy set when it is created. This consists of a strategy contract address, along with an execution payload.&#x20;

This page provides more details on the Execution strategies along with the implementations that we offer.&#x20;

## Proposal status

Every execution strategy should have a public view function `getProposalStatus` with the following interface:

```solidity
function getProposalStatus(
    Proposal memory proposal,
    uint256 votesFor,
    uint256 votesAgainst,
    uint256 votesAbstain
) external view returns (ProposalStatus);
```

This function takes the proposal state as input and returns the proposal status defined by a `ProposalStatus` enum. This enum contains all of the possible states the proposal can be in: &#x20;

```solidity
enum ProposalStatus {
    VotingDelay,
    VotingPeriod,
    VotingPeriodAccepted,
    Accepted,
    Executed,
    Rejected,
    Cancelled
}
```

Note that because of having separate `minVotingDuration` and `maxVotingDuration` , we have two separate statuses for inside the voting period: `VotingPeriod` and `VotingPeriodAccepted`.&#x20;

Abstracting status functionality outside of the space contract allows far greater flexibility in governance mechanisms since users can define their own logic on exactly how the status is determined. We provide the following implementations:&#x20;

### [Simple Quorum](https://github.com/snapshot-labs/sx-evm/blob/main/src/execution-strategies/SimpleQuorumExecutionStrategy.sol)

A proposal is accepted if `FOR` votes exceed `AGAINST` votes and the total votes (`FOR` + `AGAINST` + `ABSTAIN` ) exceed the `quorum`.

Has a single parameter `quorum` which is set when the strategy is deployed.&#x20;

{% hint style="info" %}
This is the standard approach that we expect to be used most often.&#x20;
{% endhint %}

### [Optimistic Quorum](https://github.com/snapshot-labs/sx-evm/blob/main/src/execution-strategies/OptimisticQuorumExecutionStrategy.sol)

A proposal is rejected if `AGAINST` votes exceed the `quorum`, otherwise, it is accepted.&#x20;

It has a single parameter `quorum` that is set when the strategy is deployed.

{% hint style="success" %}
This approach unlocks **optimistic governance mechanisms** where proposals are assumed to be accepted unless DAO members choose otherwise by voting against. \
\
This can lead to a far higher level of governance efficiency as it reduces the number of on-chain transactions for 'non-controversial' proposals.&#x20;
{% endhint %}

### [Emergency Quorum](https://github.com/snapshot-labs/sx-evm/blob/main/src/execution-strategies/EmergencyQuorumExecutionStrategy.sol)

It has two parameters: `quorum` and `emergencyQuorum`, where `emergencyQuorum` should be set greater than `quorum`.&#x20;

If the total votes are less than `emergencyQuorum`, then the proposal status is computed in the same way as Simple Quorum with the `quorum` parameter. However if the higher `emergencyQuorum` is met, then the `minVotingDuration` is **ignored** and a proposal can be **executed early.**&#x20;

{% hint style="info" %}
This can be useful for emergency actions in response to critical events such as hacks, where one can expect much higher participation in the governance vote than during normal processes, and therefore a 'tradeoff' between proposal duration and proposal participation can be made.&#x20;
{% endhint %}

## Proposal execution

If the proposal status is `Accepted` (or `VotingPeriodAccepted`) the Execution strategy should then execute the proposal payload. We provide the following payload executor implementations:&#x20;

### [Safe module (Zodiac)](https://github.com/snapshot-labs/sx-evm/blob/main/src/execution-strategies/AvatarExecutionStrategy.sol)

An execution strategy that allows proposals to execute transactions from a specified `target` [Avatar](https://github.com/gnosis/zodiac/blob/master/contracts/interfaces/IAvatar.sol) contract, the most popular one being a Safe.&#x20;

To use this strategy in a proposal, you must whitelist the space in the strategy, this can either be done at deployment or using the `enableSpace` function. The proposal payload should consist of an ABI encoded array of type `MetaTransaction[]` with the following format:&#x20;

```solidity
struct MetaTransaction {
    address to;
    uint256 value;
    bytes data;
    Enum.Operation operation;
    uint256 salt;
}
```

### [Timelock](https://github.com/snapshot-labs/sx-evm/blob/main/src/execution-strategies/timelocks/TimelockExecutionStrategy.sol)&#x20;

An execution strategy that is itself a Timelock contract. A `timelockDelay` is specified when the Timelock is deployed. When a proposal with this strategy is executed, the proposal transactions are queued in the Timelock for `timelockDelay` seconds before they can be executed. The proposal payload should consist of an ABI encoded array of type `MetaTransaction[]` with the following format:&#x20;

```solidity
struct MetaTransaction {
    address to;
    uint256 value;
    bytes data;
    Enum.Operation operation;
    uint256 salt;
}
```



{% hint style="info" %}
There is also an optional `vetoGuardian` role that has the power **to `veto` a queued proposal.**&#x20;
{% endhint %}

### And more!

Feel free to create your own Execution strategies! The interface of a strategy can be found [here](https://github.com/snapshot-labs/sx-evm/blob/main/src/interfaces/IExecutionStrategy.sol).
