---
description: project ideas for Qala development course
---

# Projects

## General

* Projects can be built as a front-end application, back end application or a command line tool.
* If you choose a project from the list you can choose a bitcoin or a lightning project.
* You may also have your own project or idea that you'd like to build out -- great! Please run your own projects past the instructors first so we can check it is suitable and determine which skills it will exercise.
* Your first project will probably leverage a bitcoin or lightning library in order to facilitate fast iteration on end results.
* In your second/third project you should be considering not using a library to do as much of the heavy lifting, so that you can become more comfortable with how bitcoin and lightning are working under the hood.

## Bitcoin projects 

Topics to cover: transactions, scripting, reorgs, HD wallets

### Tier 1

1. Re-skin Kevin's wallet-building workshop
1. [Satoshi dice/game](#Satoshi-dice)
1. [Fork monitor](#Fork-monitor)
1. [Block explorer](#Block-explorer)
1. [Mempool/fee analysis](#Mempool-fee-analysis)
1. P2P network analysis
1. Transaction propagation
1. Build your own signet
1. Bitcoin paywall
1. [Bitkinship](#Bitkinship)

### Tier 2

1. Simulate "push payments" using Bitcoin
1. Improve bitcoin wallet "contact" lists
1. Graph your bitcoin wallet's UTXOs (+ chain analysis)
1. Exchange / remittance service
1. Bitcoin “bank” (hot, warm, cold wallet backend)
1. Chain analysis tool/UI/library
1. [Timelock refresher](#Timelock-refresher)
1. Multi-sig collaborative custody provider

### To be sorted

* Joinmarket UI

### Satoshi dice
**Outline:** A provably fair gambling application, where payments to and from the casino are made on-chain or in Lightning. See [bitcoin.it/wiki/Satoshi_Dice](https://en.bitcoin.it/wiki/Satoshi_Dice) for more background information, and [this Stack Exchange question](https://bitcoin.stackexchange.com/questions/7369/how-to-implement-a-game-like-satoshidice) for a high-level on-chain implementation.
**Format:** Casino server back-end (required); Client application (optional, GUI or CLI)
**BTC/LN topics:** creating and parsing Bitcoin transactions, 0-conf protocols, provable fairness

### Fork monitor
**Outline:** Monitor blockchain and send an alert when a fork (exceeding n blocks) occurs, and another one when it is "resolved" (m blocks ahead)
**Format:** Server back-end; simple front-end or API to subscribe (email, pub/sub, webhooks, ...)
**BTC/LN topics:** chain reorgs, block propagation

### Block explorer
**Outline:** given a block hash, visualize block header and transaction information. Given a transaction hash, visualize input and output information. See e.g. https://blockstream.info/
**Format:** Client application (GUI or CLI)
**BTC/LN topics:** parsing blocks, parsing transactions

### Mempool fee analysis
**Outline:** Create a service which monitors the current state of the mempool with respect to fees. Provide APIs or a GUI which users (and optionally services) can connect to in order to retrieve relevant information. Include facility for users to _upload_ their own transactions via the service.
**Format:** Backend with APIs or front end with GUI
**BTC/LN topics:** transactions, fees, mempool, p2p

### Bitkinship
**Outline:** Given two UTXOs, calculate how related they are
**Format:** Library and CLI
**Bonus:** Given an xpub, calculate relatedness between all UTXOs belonging to xpub.

### Timelock refresher
**Outline:** To ensure your heirs can access your bitcoin after you pass away, all of your P2WSH addresses contain a second spending clause that after 1 year, a second key (held by your heir) can spend all of your outputs. With this program/script, you want to be able to quickly "refresh" all outputs that are coming close to being unlocked, e.g. within 3 months of the second spending path becoming viable. See https://bitcointalk.org/index.php?topic=5185907.0 for an example of the original setup.
**Format:** Client application, short lived.
**BTC/LN topics:** creating transaction, advanced scripting, timelocks
**Bonus:** multisig instead of single sig; use taproot

## Lightning projects

1. [Lightning web store](#Lightning-web-store) e.g. [starblocks.acinq.co](https://starblocks.acinq.co/)
1. Satoshi dice/game
1. Satoshi's place
1. getAlby hacking
1. Messaging app
1. Something related to social networking
1. Paywall
1. LND -> Core Lightning (CLN) database migration tool
1. Exchange / remittance service
    Look around Galoy for more ideas
    Ask Galoy
1. [Build your own lightning node](#Build-your-own-lightning-node) with LDK and accompanying crates (Rust)

### Lightning web store
**Outline:** Create a web store like [starblocks.acinq.co](https://starblocks.acinq.co/) that accepts signet lightning payments. You can sell any virtual products you want!
**Format:** Web front-end and a backend that communicates with LND

### Build your own lightning node
**Outline:** Build your own lightning node with the Lightning Development Kit (LDK) following the outline [here](https://lightningdevkit.org/tutorials/build_a_node_in_rust/). Use your `bitcoind` node (on signet) as a block source and wallet. Additionally, create a CLI tool that can interact with the node via RPCs, like `lncli` does for `lnd`. Your CLI should have commands to:
* Generate an address to fund your on-chain wallet
* Connect to a peer
* List all peers
* Open a channel with any other lightning node
* List all channels
* Create an invoice
* Pay an invoice

**Format:** Lightning node with CLI
    