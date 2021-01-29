# Polis Blockchain | Validator Tracker Challenge


Luis Correa & Hans Looman

Miami Blockchain Week Hackathon | January 29th 2021



## Validator Tracker

The **Olympus Protocol** is the replicated state machine (or blockchain) that uses a peer-to-peer communication layer to interact between nodes and transfer value assets over a trustless environment. **[Polis](https://coinmarketcap.com/es/currencies/polis/)** is the main asset or token used on top of this protocol.

[Ogen](https://github.com/olympus-protocol/ogen) is the main implementation in [golang](https://golang.org/) of this protocol.

**Olympus** implements the Casper Friendly Finality Gadget consensus mechanism to guarantee the immutability of the chain. **Validators** are the ones who are in charge for voting on the validity of blocks every epoch, getting proportionally rewarded on every single block they contribute on creating. They require a 100 POLIS collateral that will be locked on the owner's wallet, and a special message needs to be broadcasted onto the network to announce its creation.

However, if a validator fails to contribute to the consensus for any reason (if it votes for two blocks on the same slot, or is not online at the time of voting) it will get **slashed**. Slashing means that the balance locked for the validator, plus the rewards it may have received with start to reduce gradually and incrementally until the validator is straightened again. Hence the need of a monitoring tool for validator tracking.

To prevent getting slashed, it is recommended to **EXIT a VALIDATOR** if the owner plans to enter maintenance on a server, or whishes to withdraw his assets.

This creates the need for any sort of tool that:

* Notifies validator owners if a validator's state has changed.
* Allows to visualize validator's rewards over time.
* Allows to track multiple validators linked to an account.
* Allows to start or exit validators.

Any tool created is fair game as long as it satisfies one or more of these requirements. We were thinking of a telegram or discord bot, a dashboard website, but any idea you may have or wish to improve it is welcome!

### Validator Status

The Indexer will be updated in a few weeks to shown ENUMS instead of integer values. In the meantime here's a table that clarifies the status for a validator and its meaning.

| Value | Status                     | Description                                                     |
|-------|----------------------------|-----------------------------------------------------------------|
| 0     | StatusStarting             | Validator is created and waiting to join.                       |
| 1     | StatusActive               | Validator is currently in the queue.                            |
| 2     | StatusActivePendingExit    | Validator is queued to be removed from the active set.          |
| 3     | StatusExitedWithPenalty    | Validator is exited due to a slashing condition being violated. |
| 4     | StatusExitedWithoutPenalty | Validator is exited due to a drop below the ejection balance.   |

## Ogen Startup

```shell
ogen --rpc_wallet --rpc_proxy --rpc_keystore --dashboard
```
This will expose the RPC console commands for the wallet, keystore over https, as well as exposing a dashboard on port 8080.
For more information on commands and flags do

```shell
ogen help
```
## Resources

You can find useful documentation and information on Olympus through these links.

* [Olympus Docs](https://doc.oly.tech/documentation/first-steps/features)

* [Ogen (Golang Implementation)](https://github.com/olympus-protocol/ogen): In case you want to run your own node and validators. Supports Docker containerization.

* [Olympus Block Explorer](https://explorer.oly.tech)
* [Olympus Indexer](https://indexer.oly.tech/): A GraphQL block indexer from where you will be able to query data.
* To request coins from our faucet please consider joining our [Discord Community](https://discord.gg/aNjrKhp), the faucet bot is on the #olympus-request-coins channel.


## Social Media
* [Discord](https://discord.gg/aNjrKhp)
* [Twitter](https://twitter.com/polisblockchain?lang=en)

