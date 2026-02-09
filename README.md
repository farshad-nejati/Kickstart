## Kickstart

Kickstart is a **decentralized crowdfunding platform** built on the **Ethereum** blockchain.  
It uses **Solidity smart contracts** for campaign logic and a **React / Next.js** frontend to let users create campaigns, contribute funds, and manage spending requests in a transparent and trust-minimized way.

### Main features

- **Create campaigns** with a minimum contribution threshold (in wei).
- **Contribute Ether** to become an approver for a campaign.
- **Spending requests**: the campaign manager creates requests to spend funds.
- **Contributor approval**: approvers vote on each request; only majority-approved requests can be finalized.
- **On-chain transparency**: all contributions and requests are stored in Ethereum smart contracts.

### Tech stack

- **Smart contracts**: Solidity (compiled with `solc`)
- **Blockchain / Web3**: Ethereum, `web3.js`, `ganache-cli` for local testing
- **Frontend**: React, Next.js, `next-routes`
- **UI**: `semantic-ui-react`, `semantic-ui-css`
- **Testing**: Mocha + Ganache

### Project structure (high level)

- `server.js` – Custom Node.js server to run Next.js with route support.
- `routes.js` – Route definitions for campaigns and request pages.
- `pages/` – Next.js pages (campaign list, create campaign, campaign details, requests).
- `components/` – Reusable UI components (layout, header, contribute form, request row).
- `ethereum/` – Smart contract sources, compilation scripts, and build artifacts (JSON ABIs).
- `test/` – Mocha tests for the `CampaignFactory` and `Campaign` contracts.
- `ADDRESS` – Notes about deployed contract addresses from different deployments.

### Prerequisites

- Node.js **12.x** (as specified in `package.json`)
- npm
- An Ethereum wallet such as MetaMask for interacting with the app in a browser

### Run the app locally

```bash
git clone https://github.com/farshad-nejati/Kickstart.git
cd Kickstart
npm install
npm run dev
```

Then open `http://localhost:3000` in your browser.

### Run the tests (smart contracts)

The smart contracts are tested using Mocha and Ganache:

```bash
npm test
```

This will:

- Start a local Ganache provider.
- Compile the `CampaignFactory` and `Campaign` contracts.
- Deploy contracts to the local test blockchain.
- Run tests that cover deployment, contributions, minimum contribution rules, request creation, and request finalization.

### Deployment notes

The app is designed to work with a deployed `CampaignFactory` contract on an Ethereum network (testnet or mainnet).  
The `ADDRESS` file contains example factory addresses from previous deployments.

To deploy to a public network you typically:

1. Configure a provider (e.g. Infura + `truffle-hdwallet-provider`).
2. Compile contracts and deploy the `CampaignFactory` contract.
3. Update your frontend configuration to point to the deployed factory address.

### License

This project is licensed under the ISC License. See `package.json` for details.
