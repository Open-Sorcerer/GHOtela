# GHO Nexus Protocol
## Interchain Credit System Leveraging GHO and Chainlink CCIP

Welcome to GHO Nexus Protocol – a cutting-edge DeFi lending and borrowing platform designed for the new era of cryptocurrency. Our platform facilitates efficient management of digital assets across multiple blockchain networks, offering a unique, seamless experience.

## Comprehensive Lending and Borrowing Ecosystem
GHO Nexus Protocol transcends a typical platform; it's an ecosystem enabling users to lend and borrow digital assets like GHO and Ethereum (ETH) across various blockchains. This feature enhances the liquidity and utility of your digital holdings.

- **Cross-Chain Functionality**: Facilitate lending and borrowing of GHO and ETH across numerous blockchains.
- **Diverse Borrowing Options**: Whether you want to lend ETH and borrow GHO or vice versa, our platform supports both intra-chain and cross-chain transactions to meet your financial needs.

## Accuracy Powered by Chainlink Data Feeds
For precise and reliable transaction processing, GHO Nexus Protocol integrates Chainlink Data Feeds. This integration ensures real-time USD valuations of ETH, providing you the confidence to borrow GHO against your ETH holdings on any blockchain.

## First GHO Bridge
Expanding beyond lending and borrowing, our dApp introduces an advanced bridge feature for GHO tokens, streamlining their transfer across blockchains.

- **Extended Capabilities**: Our bridge isn't limited to GHO; it also facilitates the transfer of BnM mints across different blockchains.
- **User-Centric Design**: We prioritize a frictionless user experience, covering all gas fees for token bridging to ensure smooth transactions.

## Flexible Transaction Options
Our platform caters to a wide array of users and scenarios:

- **Sender Options**:
  - Externally Owned Account (EOA) Address
  - Smart Contract
- **Receiver Options**:
  - Externally Owned Account (EOA) Address
  - Smart Contract

Join GHO Nexus Protocol and explore the vast potential of DeFi. Bridge the blockchain divide and revolutionize digital asset management!

# Smart Contract Architecture

## GHO Bridge
Users can interact with our dApp, select their desired destination blockchain, and specify the EOA or smart contract address for token transfer. Leveraging Chainlink CCIP, we facilitate the transfer of GHO and BnM tokens. Like any ERC20 token, users must approve the token, and our dApp streamlines this process.

![WhatsApp Image 2024-01-21 at 20 09 44_05c9b909](https://github.com/Open-Sorcerer/GHOtela/assets/60979345/bedbee17-1555-49d4-8f0d-b8ba07cd40e0)

![WhatsApp Image 2024-01-21 at 20 09 00_0a351bec](https://github.com/Open-Sorcerer/GHOtela/assets/60979345/a87246a1-26e7-42e8-857c-cb1e8cc33246)



## Lending and Borrowing Protocol
Our protocol involves four key smart contracts:
- "SourceContract" on Arbitrum Sepolia and Ethereum Sepolia (Source Chains)
- "Balance" Contract on Ethereum Sepolia (Destination Chain)
- "SourceGateway" Contract on Arbitrum with a _ccipReceive function for Source chain communication
- "BalanceDestination" Contract on Ethereum Sepolia (Destination Chain)

## Lend
Users deposit tokens into `SourceContract`, which, through Chainlink CCIP, transfers message data to the `Balance` contract via the `BalanceDestination` contract. We ensure users cannot borrow more than 80% of their lending amount. BnM tokens are integrated and valued in USD using Chainlink Data Feeds.

![WhatsApp Image 2024-01-21 at 20 10 22_89cf60d7](https://github.com/Open-Sorcerer/GHOtela/assets/60979345/08931c9d-c267-4a5e-a24a-18b6beab289d)



## Borrow
Users can borrow up to 80% of their lending amount in any token. The borrowing process involves the `SourceContract` and Chainlink CCIP, with the `Balance` contract verifying eligibility and instructing `SourceContract` via `SourceGateway` to disburse funds.

![WhatsApp Image 2024-01-21 at 20 11 32_e45676f4](https://github.com/Open-Sorcerer/GHOtela/assets/60979345/faedf067-0ed1-4135-b474-7d8082d9d157)



