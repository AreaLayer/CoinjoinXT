# CoinjoinXT ⚡⚛️🔄

Architecture on Firebolt using CoinjoinXT

## CoinJoinXT implementation

CoinJoinXT is non-custodial privacy technique which is closely related to CoinJoin. It allows for any number of entities to between them create a so-called proposed transaction graph (PTG) which is a list of connected transactions. In the PTG the bitcoins belonging to the entities are sent to and fro in all the transactions, but at the end of the PTG they are all returned to their rightful owners. The system is set up so that the process of the PTG being mined is atomic, so either the entire PTG is confirmed on the blockchain or none of it is, this means none of the participating entities can steal from each other.

Source: [CoinjoinXT](https://en.bitcoin.it/wiki/CoinJoinXT)

**Current Status - PUBLIC ALPHA**

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
 - LNVortex

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

- **LNVortex**

   - Alice and Bob can open collaborative channels via Lighnting Network.
   - With L1, they can make collaboration during mixing coins
  

-  **Lightning Network Channel**:
   - Alice and Bob open a Lightning Network payment channel between them.
   - This channel is funded with a certain amount of Bitcoin from both parties.
   - The channel allows them to conduct multiple off-chain transactions without congesting the main Bitcoin network.

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


  ## CoinjoinXT VS other implementations

  | Feature                   | Firebolt           | Joinstr            | Joinmarket         | Whirlpool          | Wasabi Wallet      |
|---------------------------|--------------------|--------------------|--------------------|--------------------|--------------------|
| CoinJoin Type             | CoinJoinXT  | CoinJoin (Schnorr) | CoinJoin (Schnorr) | CoinJoin (Chaumian) | CoinJoin (Chaumian) |
| Privacy Model             | Central Coordinator | Peer-to-Peer       | Peer-to-Peer       | Central Coordinator | Central Coordinator |
| CoinJoin Fee               | Variable           | Variable           | Variable           | Variable           | Variable           |
| Coin Selection Options    | Limited            | Customizable       | Customizable       | Customizable       | Customizable       |
| Mixing Depth              | Fixed              | Customizable       | Customizable       | Fixed              | Fixed              |
| Anonymity Set             | Limited            | High               | High               | Limited            | Limited            |
| Confidential Transactions | Yes                | Yes                | Yes                | Yes                | Yes                |
| User Interface            | CLI                | CLI                | CLI/GUI            | GUI                | GUI                |
| Open Source               | No                 | Yes                | Yes                | Yes                | Yes                |
| Platform Support          | Windows, Linux     | Linux              | Linux, macOS, Windows | Linux, macOS, Windows | Linux, macOS, Windows |


In this example, Alice and Bob use CoinJoinXT with Taproot and the Lightning Network to exchange Bitcoin privately and efficiently. They leverage the privacy benefits of CoinJoinXT and Taproot's script flexibility, while also taking advantage of Lightning Network's off-chain capabilities for instant and cost-effective transactions. This combination provides them with a secure, private, and scalable way to conduct their Bitcoin exchanges.

