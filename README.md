# CoinjoinXT ⚡🌀

Architecture on Firebolt using CoinjoinXT

**Archive study use case**

## CoinJoinXT implementation

CoinJoinXT is non-custodial privacy technique which is closely related to CoinJoin. It allows for any number of entities to between them create a so-called proposed transaction graph (PTG) which is a list of connected transactions. In the PTG the bitcoins belonging to the entities are sent to and fro in all the transactions, but at the end of the PTG they are all returned to their rightful owners. The system is set up so that the process of the PTG being mined is atomic, so either the entire PTG is confirmed on the blockchain or none of it is, this means none of the participating entities can steal from each other.

Source: [CoinjoinXT](https://en.bitcoin.it/wiki/CoinJoinXT)

**Current Status - Alpha (Version 1)**

### What makes CoinjoinXT different


**Fast**

Use small blocks per circles powered by Taproot and Segwit


**Usable**

Simple UI/UX


**Strong**

Structurally built on a  proposed transaction graph (PTG):

 - Atomic
 - DOS-resistant
 - Compatible with Coinswap
 - Use less block space thanks to the Taproot
 - More privacy between L1 and L2 using Lightning Network

## Architecture

Users initiate a CoinJoinXT transaction by combining their inputs and outputs in a way that obscures individual ownership. This CoinJoinXT transaction is designed to use the capabilities of Taproot and PTG, allowing for intricate script conditions while maintaining privacy.

Taproot comes into play when these CoinJoinXT transactions are broadcasted to the Bitcoin network. The use of Taproot addresses ensures that the complex scripts within the transactions are hidden, making them appear like regular transactions. This enhances privacy by not revealing the specific conditions or smart contract logic involved.

To further optimize and scale these transactions, Lightning Network channels can be utilized. Users can open payment channels and conduct off-chain transactions, enjoying instantaneous confirmations and reduced fees. This relieves the main Bitcoin network from congestion and benefits from the privacy-enhancing features of CoinJoinXT and Taproot.

![image](https://github.com/AreaLayer/CoinjoinXT/assets/135646455/27bc9bdb-7d38-46c7-b690-d401c3e0d019)


**Scenario: Alice and Bob want to exchange Bitcoin privately and efficiently.**

-  **Setup**:
   - Alice and Bob set up their Bitcoin wallets with support for CoinJoinXT, Taproot, and Lightning Network.
   - They both fund their Lightning Network wallets with some Bitcoin.

- **CoinJoinXT Transaction**:
   - Alice and Bob decide to use CoinJoinXT for increased privacy.
   - They create a CoinJoinXT transaction by combining their inputs and outputs.
   - The transaction includes multiple inputs from both Alice and Bob, as well as multiple outputs. These outputs include Lightning Network channels, Taproot addresses, and change addresses.

-  **Taproot Integration**:
   - The CoinJoinXT transaction uses Taproot addresses for its outputs.
   - Each Taproot output contains a complex script condition that specifies the spending conditions. These conditions can include time locks, multisig requirements, or other advanced conditions.

-  **Lightning Network Channel**:
   - Alice and Bob open a Lightning Network payment channel between them.
   - This channel is funded with a certain amount ofartie Bitcoin from both ps.
   - The channel allows them to conduct multiple off-chain transactions without congesting the main Bitcoin network.
   - Beyond before/after coinjoin round finalized the user can close/open channel, mixing still more UTXOs

-  **Off-chain Transactions**:
   - Alice and Bob can now exchange Bitcoin instantly and privately using the Lightning Network.
   - Each Lightning Network transaction is not recorded on the main blockchain but is instead managed within the Lightning Network channel.
   - They can send payments back and forth, adjusting the channel's balance as needed.

-  **Closing the Lightning Channel**:
   - Once Alice and Bob are done with their exchanges, they decide to close the Lightning Network channel.
   - The final channel balances are settled on the main Bitcoin blockchain.
   - The outcome of the Lightning transactions is reflected in the Taproot outputs of the CoinJoinXT transaction.

- **Privacy and Security**:
   - The CoinJoinXT transaction combines the inputs and outputs of Alice and Bob, making it challenging for an observer to determine who sent how much to whom.
   - The Taproot addresses used in the transaction hide the complexity of the script conditions, improving overall privacy.
   - Lightning Network transactions are conducted off-chain, reducing the exposure of transaction details to the public blockchain.

In this example, Alice and Bob use CoinJoinXT with Taproot and the Lightning Network to exchange Bitcoin privately and efficiently. They leverage the privacy benefits of CoinJoinXT and Taproot's script flexibility, while also taking advantage of Lightning Network's off-chain capabilities for instant and cost-effective transactions. This combination provides them with a secure, private, and scalable way to conduct their Bitcoin exchanges.

A combined use case involving **CoinJoin**, the **Lightning Network**, and the **Liquid Network** can create a powerful privacy-focused, scalable, and interoperable financial system. Here's a potential use case combining all three:

### **Use Case: Privacy-Preserving Cross-Chain and Off-Chain Transactions**

#### **Scenario**: 
Alice wants to conduct private, fast, and low-fee transactions between Bitcoin and Liquid assets, and later settle payments using the Lightning Network for microtransactions or instant transfers. 

### **Key Components:**
1. **CoinJoin**: Used to enhance transaction privacy.
2. **Lightning Network**: Used for fast, low-cost, off-chain payments.
3. **Liquid Network**: Used for issuing and trading pegged assets (like L-BTC) or stablecoins with increased privacy and faster settlement compared to the Bitcoin main chain.

### **Step-by-Step Workflow**:

1. **Privacy via CoinJoin**:
   - Alice wants to enhance her Bitcoin transaction privacy before interacting with Liquid assets. 
   - She participates in a **CoinJoin transaction** to mix her BTC with others, making it difficult to trace her funds' origins. This helps obscure her financial activity from chain analysis tools before converting her BTC into Liquid assets.

2. **Asset Transfer on Liquid Network**:
   - After using CoinJoin, Alice transfers her BTC to the **Liquid Network** by using a peg-in transaction (converting BTC to L-BTC, the Liquid version of Bitcoin).
   - On the Liquid Network, Alice can conduct faster, private transactions with L-BTC or other Liquid assets (like stablecoins or securities).

3. **Instant Payments via Lightning Network**:
   - To make instant, micro-level payments, Alice opens a channel on the **Lightning Network** using either her CoinJoin BTC or L-BTC.
   - She uses the Lightning Network for micropayments and low-fee transactions, settling transactions quickly and off-chain.
   - Alternatively, Alice can settle her Liquid network transactions using the Lightning Network for immediate payments, reducing the need for on-chain confirmations.

4. **Cross-Chain Transfers**:
   - If Alice needs to switch back to the Bitcoin main chain, she can peg-out her L-BTC from Liquid to BTC, still benefiting from CoinJoin’s privacy.
   - Using atomic swaps, Alice can directly swap assets between the Bitcoin and Liquid networks in a decentralized manner, without needing a centralized exchange.

5. **Final Settlement**:
   - Alice can eventually close her Lightning channels to settle funds back to the Bitcoin main chain (with CoinJoin-enhanced privacy), or continue transacting within Liquid or Lightning networks based on her needs.

### **Benefits**:
- **Enhanced Privacy**: CoinJoin obfuscates the source of funds, while Liquid Network’s confidential transactions hide transaction amounts.
- **Speed**: The Lightning Network ensures fast and scalable transactions, while Liquid reduces Bitcoin main chain congestion.
- **Interoperability**: Alice can seamlessly move between Bitcoin, Liquid assets, and Lightning Network channels without compromising on privacy or speed.
- **Low Fees**: By staying off-chain with the Lightning Network and utilizing Liquid’s fast finality, Alice avoids high Bitcoin transaction fees.

## Firebolt Evolution

Since 2023 that the project was created, we already released:

- [Firebolt](https://github.com/AreaLayer/FireBolt): First generation from wallet concept
- [Firebolt React Native](https://github.com/AreaLayer/firebolt-react-native): Second generation from wallet closer to be Real world
- [Firebolt Electrum](https://github.com/AreaLayer/firebolt-electrum): Third generation and ready to test into Electrum wallet plugin
- [Coinjoin ZK](https://github.com/AreaLayer/coinjoin-zk) - Study proposal for support zero knowledge/proof in coinjoin transactions
- [Coinjoin Liquid](https://github.com/AreaLayer/coinjoin-liquid) - Study proposal for support Liquid with Coinjoin transactions
- [Coinjoin Statechain](https://github.com/AreaLayer/coinjoin-statechain) - Study proposal for support Statechain with Coinjoin transactions
- [Firebolt React Native](https://github.com/AreaLayer/firebolt-react-native): Integration of Silent Payments/Breez SDK with Lightning Network/Liquid network
- [Firebolt React Native](https://github.com/AreaLayer/firebolt-react-native): Integration with ZK proof
- [Firebolt Electrum](https://github.com/AreaLayer/firebolt-electrum): Integration with ZK proof ready to mainnet/signet/testnet
- [Firebolt React Native](https://github.com/AreaLayer/firebolt-react-native): Integration with submarine swaps and more
- [ZK Proof Rust](https://github.com/AreaLayer/zk-proof-rust): Library for ZK Proof written in Rust and ready to 2025
- [Demo ZK Snarks Quantum](https://github.com/AreaLayer/demo-zksnarks-quantum): First research of P2P Coinjoin to post quantum world
