# 📰 Decentralized News Headline Aggregator

This is a decentralized, censorship-resistant news headline aggregator built on top of Chainlink Functions. The application retrieves the latest news stories from the Hacker News API and stores the headline along with the link to the article in a smart contract deployed on the Ethereum blockchain (Sepolia testnet). The front-end is built using [Astro](https://astro.build), providing a fast and minimal UI for viewing the aggregated headlines.

## 🔗 Features

- **Decentralized Data**: Using Chainlink Functions, the smart contract fetches news stories from the Hacker News API.
- **Smart Contract Storage**: The contract stores news URLs along with a timestamp on the Ethereum blockchain.
- **Astro Frontend**: The UI is built using Astro to retrieve and display the stored articles from the smart contract.

## 📁 Project Structure

```bash
/
├── public/                         # Static assets like images or fonts
├── ref/
│   └── newsArchive.sol             # Smart contract for reference, must be deployed separately
├── src/
│   └── lib/
│       ├── newsArchive.js          # Script to interact with the smart contract
│       └── newsArchiveABI.json     # ABI of the deployed smart contract
│   └── pages/
│       └── index.astro             # Main Astro page to display the aggregated headlines
└── package.json                    # Project dependencies and scripts
```

- **`ref/`**: Contains the reference smart contract `newsArchive.sol`. This contract needs to be deployed separately.
- **`src/lib/`**: Contains JavaScript files to interact with the deployed smart contract, including the ABI and JavaScript logic (`newsArchive.js`).
- **`src/pages/`**: Contains the Astro files responsible for rendering the frontend pages.

## ⚙️ Setup

Follow these steps to run the project locally:

1. **Clone the project**:

   ```bash
   git clone https://github.com/snehavarmak/decentralized-news
   cd decentralized-news
   ```

2. **Install dependencies**:

   ```bash
   npm install
   ```

3. **Setup environment variables**:

   - Rename the `example.env` file to `.env`.
   - In the `.env` file, fill in the required fields:
     - `CONTRACT_ADDRESS`: The deployed address of the `newsArchive.sol` smart contract.
     - `RPC_URL`: The Ethereum network's RPC URL. By default, the provided RPC is for the Sepolia testnet. If you are using another network, update the RPC URL accordingly.

4. **Deploy the Smart Contract**:

   - You will need to deploy the `newsArchive.sol` smart contract (found in `ref/newsArchive.sol`) using Hardhat or Remix.
   - Make sure to update the `.env` file with the deployed contract address.

5. **Run the Astro development server**:

   ```bash
   npm run dev
   ```

   This will start the local development server, allowing you to interact with the frontend.

6. **Interact with the Contract**:

   The Astro front-end fetches and displays the latest news headlines stored on the deployed smart contract. You can view the headlines directly on the UI.

## 📜 Smart Contract Details

The contract `newsArchive.sol` (found in the `ref/` directory) is responsible for:

- Fetching the latest news headlines from the Hacker News API using Chainlink Functions.
- Storing the fetched URLs and their corresponding timestamps on-chain.
- Providing a view function to retrieve all stored headlines.

To deploy the contract, you can use any Ethereum development framework (like Hardhat or Remix). After deployment, make sure to update the `.env` file with the correct contract address and RPC URL.

## 🛠 Tools Used

- **Chainlink Functions**: For decentralized API calls and off-chain computation.
- **Astro**: For building a fast, minimal front-end.
- **Ethereum Sepolia Testnet**: As the test network for deploying the smart contract.
- **Hardhat or Remix**: To deploy the smart contract.

## 🌐 Deployment

Once the smart contract is deployed and the environment is configured, you can deploy the frontend to any static hosting platform (e.g., Vercel, Netlify) that supports Astro.

1. **Build the project**:

   ```bash
   npm run build
   ```

2. **Deploy the `dist/` folder** to your preferred static hosting platform.

## 🚀 Future Improvements

- Add more detailed error handling for failed API requests.
- Implement pagination for older news headlines.
- Expand support for other news APIs or sources.
