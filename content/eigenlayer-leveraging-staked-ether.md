---
title: "Launching an AVS with EigenLayer – A New Frontier in Decentralized Trust"
description: "Learn how to design and launch an Actively Validated Service (AVS) using EigenLayer’s ETH restaking model. Tap into Ethereum’s security for oracles, zk-provers, bridges, and more."
keywords:
  - EigenLayer
  - AVS
  - Actively Validated Service
  - Ethereum
  - Restaking
  - Blockchain Infrastructure
  - zk-proofs
  - Bridges
  - Oracles
  - Validator Networks
author: "Rashid McMoodoo"
url: "https://www.blog.mcmoodoo.com/eigenlayer-avs-launch"
canonical_url: "https://www.blog.mcmoodoo.com/eigenlayer-avs-launch"
twitter_card: "summary_large_image"
twitter_title: "Launching an AVS with EigenLayer – A New Frontier in Decentralized Trust"
twitter_description: "Use Ethereum restaking to build decentralized services like oracles, zk-provers, and DA layers—without creating your own validator network."
twitter_site: "@mcmoodoo"
og_title: "Launching an AVS with EigenLayer – A New Frontier in Decentralized Trust"
og_description: "Design and launch your own EigenLayer-secured AVS, leveraging Ethereum's validator set for off-chain decentralized services."
og_url: "https://www.blog.mcmoodoo.com/eigenlayer-avs-launch"
og_type: "article"
---

## Key Takeaways
* **EigenLayer enables ETH restaking** – Ethereum stakers can opt in to validate new modules by accepting additional slashing conditions.
* **Extends Ethereum security** – Restakers lend Ethereum’s economic security to external modules like oracles, bridges, VMs, and DA layers.
* **Security aggregation** – Instead of fragmenting trust, EigenLayer unifies ETH security across multiple services.
* **New earning opportunities** – Restakers can earn fees from participating in various validation tasks beyond Ethereum's consensus.
* **Innovation sandbox** – EigenLayer acts as a testing ground for Ethereum upgrades (e.g., Danksharding), allowing experimentation before core integration.
* **Enables permissionless innovation** – Developers can deploy new trust-based systems without building their own validator networks.

## What I Thought EigenLayer Was—And What It Actually Is

I kept hearing about **EigenLayer** in conversations around Ethereum scaling and decentralization, but I hadn’t really dug into it—just another protocol on the pile, I figured.

Then I realized it’s doing something deeper than I expected.

At first, I thought it was just a staking protocol, but it turns out EigenLayer is reshaping how we think about trust in decentralized systems. It’s not just about consensus anymore—it’s about **coordination**.

EigenLayer introduces something called **Actively Validated Services** (AVSs). These let developers build off-chain services that still inherit Ethereum’s battle-tested security—without touching Ethereum itself. That blew my mind a bit. You’re basically reusing Ethereum’s validator set through restaking, plugging new ideas into a system that already works.

This opens a new frontier where services like oracles, data availability layers, zero-knowledge provers, and bridging protocols can be **decentralized, economically secure, and composable**.

So instead of launching a whole new chain to run a novel service, you can just **build on EigenLayer** and inherit Ethereum-grade trust.

Once I saw that, I realized it’s not just another protocol. It’s a whole new layer of composability.

## How Restaking Actually Works

EigenLayer introduces the concept of _restaking_, where staked ETH (or LSTs like stETH) is reused to secure other services beyond Ethereum itself.

Here’s how it works:

1. **ETH is staked** as usual on Ethereum to help secure the network.
2. Instead of sitting idle, that same stake is **opted in to EigenLayer**, where it can also secure **Actively Validated Services (AVSs)**.
3. Validators opt in to validate these AVSs in exchange for **additional rewards**, but also take on additional **slashing risks** if they misbehave.

This allows Ethereum’s security to be **pooled and reused**, enabling smaller services to bootstrap trust without needing their own validator set.
```mermaid
flowchart TD
  A[ETH Holder stakes ETH] --> B[Staked ETH on Ethereum]
  B --> C[Opt-in to EigenLayer Restaking]
  C --> D[Validators extend services to AVSs]
  D --> E[AVSs secured by Ethereum's validator set]
  E --> F[Validators earn extra rewards]
  D --> G[Slashing risk if AVS rules are violated]
```
## **What You Can Build with EigenLayer**

Once you understand that AVSs inherit Ethereum-grade security through restaking, it opens up a powerful design space.

You can build services that:

- Require trust but don’t need their own blockchain
- Need fast or frequent validation
- Would benefit from shared security but want custom logic
### Some potential AVSs:

- **Decentralized Oracles** – secured by Ethereum’s validator set instead of their own.
- **Data Availability Layers** – provide off-chain data with strong crypto-economic guarantees.
- **Zero-Knowledge Proving Networks** – outsource zk-proof validation to a decentralized validator set.
- **Cross-chain Bridges** – inherit Ethereum security for verifying cross-chain messages.
### AVSs built on EigenLayer
```mermaid
graph LR
  A[EigenLayer Restaking System] --> B[Oracle AVS]
  A --> C[Data Availability AVS]
  A --> D[ZK Proving AVS]
  A --> E[Bridge AVS]
  B --> F[Developers Use Oracle]
  C --> G[Rollup Posts Data]
  D --> H[Apps Submit Proofs]
  E --> I[Bridge Transfers Tokens]

```
## 🔧 Designing the Service

The first step in launching an AVS is defining the **core work** your validator set will perform. For example:

- Generating ZK proofs
- Aggregating off-chain data
- Validating cross-chain messages
- Providing data availability for L2s

The work must be:

- ✅ **Verifiable**
- 🔁 **Repeatable**
- 🔌 **Composable**

### AVS Architecture (Conceptual)

```mermaid
flowchart TD
    subgraph Ethereum Mainnet
        SmartContract[AVS Smart Contract]
    end

    subgraph Off-Chain
        User[User / dApp]
        JobDispatcher[Job Dispatcher / Coordinator]
        Validator1[Validator / Prover 1]
        Validator2[Validator / Prover 2]
    end

    User --> SmartContract
    SmartContract --> JobDispatcher
    JobDispatcher --> Validator1
    JobDispatcher --> Validator2
    Validator1 -->|Proof| SmartContract
    SmartContract -->|Result| User
```


### 🛡️ Building the Validator Set

Thanks to EigenLayer, you don’t have to bootstrap your own validator network. Instead, you tap into Ethereum’s validators who have restaked ETH and opted in to your AVS.
Validator Roles

Validators can be assigned one or more responsibilities:

* ✍️ Provers: Generate ZKPs or other proofs
* 📜 Attesters: Sign or validate submitted results
* 🔍 Disputers: Challenge incorrect proofs


```mermaid
sequenceDiagram
    participant Validator
    participant AVSContract
    participant EigenLayer

    Validator->>EigenLayer: Restake ETH
    Validator->>AVSContract: Opt into AVS
    AVSContract->>Validator: Assign job
    Validator->>AVSContract: Submit result
    AVSContract->>EigenLayer: Slash or reward
```

### 🧱 Smart Contract Architecture

You’ll typically write a set of contracts that:

* Handle job submissions from users
* Track validator opt-ins
* Distribute rewards and enforce slashing
* Coordinate with EigenLayer's AVS registry
* Example: Minimal Job Submission Contract (Solidity)

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

interface IAVSValidator {
    function submitProof(uint jobId, bytes calldata proof) external;
}

contract JobSubmission {
    address public owner;
    uint public jobCounter;

    struct Job {
        address submitter;
        string inputData;
        bool fulfilled;
    }

    mapping(uint => Job) public jobs;

    constructor() {
        owner = msg.sender;
    }

    function submitJob(string calldata inputData) external returns (uint) {
        jobCounter++;
        jobs[jobCounter] = Job(msg.sender, inputData, false);
        return jobCounter;
    }

    function markFulfilled(uint jobId) external {
        require(msg.sender == owner, "Only coordinator can fulfill");
        jobs[jobId].fulfilled = true;
    }
}
```

### 🚀 Bootstrapping the Network

At launch, your primary goals are to:
* Attract validators to opt in
* Onboard developers to submit jobs
* Demonstrate provable correctness

Strategies include:
* Starting with a whitelisted validator set
* Running a testnet with rewards
* Publishing clear SDKs & APIs for integration

### ✅ Security and Verification

Your AVS must be verifiable—anyone should be able to check validator output. This often involves:
* Zero-Knowledge Proofs
* Merkle inclusion proofs
* Signature threshold schemes

If results can't be easily verified, your AVS must include dispute resolution mechanisms or watchdogs.
High-Level Verification Pipeline

```mermaid
graph TD
    Job[Job Submitted]
    Work[Validator Performs Work]
    Result[Result + Proof]
    Verify[Smart Contract Verifies]
    Output[Output Finalized]

    Job --> Work --> Result --> Verify --> Output
```

### 🧠 Conclusion: Ethereum-Secured Utility Layers

Launching an AVS on EigenLayer is about composing trust into new domains. By tapping into Ethereum’s economic security, developers can create powerful off-chain services without spinning up siloed validator sets.

As the AVS ecosystem matures, we’ll see a proliferation of services that mirror Ethereum’s openness and trust—but go far beyond what consensus alone can secure.
