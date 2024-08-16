# DEX-Hec-Layer2
A decentralized exchange platform built on BNB Chain with Layer 2 integration using opBNB.

## Project Structure

- `smart-contracts/`: Solidity smart contracts
- `backend/`: Node.js Express backend
- `frontend/`: React.js web frontend
- `mobile/`: React Native mobile app
- `order-matching-engine/`: C++ order matching engine
- `deployment/`: Deployment configurations
- `scripts/`: Utility scripts

- This structure organizes the code into distinct modules:

Smart Contracts: Handles on-chain logic for the DEX.
Backend: Provides API endpoints and integrates with the order matching engine.
Frontend: Web interface for users to interact with the DEX.
Mobile: Cross-platform mobile app for on-the-go trading.
Order Matching Engine: High-performance C++ engine for order matching.

These modules interact as follows:

The frontend and mobile app communicate with the backend via RESTful API calls and WebSocket connections.
The backend interacts with the smart contracts through ethers.js to place on-chain orders.
The backend uses the C++ order matching engine as a native addon for high-performance order matching.
The smart contracts emit events that the backend listens to for order execution and other on-chain activities.

This structure allows for separation of concerns, making the codebase modular and easier to maintain. Each component can be developed, tested, and scaled independently while still working together as a cohesive system.

## Prerequisites

- Node.js (v14+)
- Yarn
- Docker and Docker Compose
- Truffle
- C++ compiler (GCC or Clang)
- CMake

## Setup

1. Clone the repository:
git clone https://github.com/HectorTa1989/DEX-Hec-Layer2.git
cd DEX-Hec-Layer2

2. Install dependencies:
./scripts/setup_environment.sh

3. Compile and deploy smart contracts:
cd smart-contracts
truffle compile
truffle migrate --network bscTestnet

4. Build the order matching engine:
cd order-matching-engine
mkdir build && cd build
cmake ..
make

5. Start the backend, frontend, and related services:
docker-compose up -d

## Usage

- Web interface: http://localhost:3000
- API endpoint: http://localhost:3001
- Grafana dashboard: http://localhost:3000 (admin/admin)

## Testing

Run unit tests for each component:
cd smart-contracts && truffle test
cd ../backend && yarn test
cd ../frontend && yarn test
cd ../mobile && yarn test

## Deployment

1. Set up your production environment (e.g., AWS, Google Cloud).
2. Update the `deployment/docker-compose.yml` with production settings.
3. Deploy using Docker Swarm:
docker stack deploy -c deployment/docker-compose.yml dex-platform

## Contributing

Please read CONTRIBUTING.md for details on our code of conduct and the process for submitting pull requests.

## License

This project is licensed under the GNU 3.0 License - see the LICENSE.md file for details. You need my permission for commercial use.
