# NexusVault Gaming Protocol

[![Stacks](https://img.shields.io/badge/Stacks-Blockchain-purple)](https://www.stacks.co/)
[![Clarity](https://img.shields.io/badge/Clarity-Smart%20Contract-blue)](https://clarity-lang.org/)
[![License](https://img.shields.io/badge/License-ISC-green)](LICENSE)
[![Tests](https://img.shields.io/badge/Tests-Vitest-yellow)](https://vitest.dev/)

A revolutionary decentralized gaming ecosystem that transforms how players interact with digital assets, enabling seamless cross-platform gameplay with verifiable ownership and economic sovereignty.

## 🚀 Overview

NexusVault pioneers the next generation of blockchain gaming by establishing a unified protocol for asset portability, player progression, and economic interaction across multiple gaming environments. The protocol leverages Bitcoin's immutable security foundation through Stacks integration to deliver:

- **True Asset Ownership**: NFT-based game assets with cross-platform compatibility
- **Player Progression System**: Experience-based leveling with persistent character development
- **Virtual World Management**: Decentralized world creation and access control
- **Competitive Leaderboards**: Transparent ranking system with Bitcoin-based rewards
- **Economic Sovereignty**: Player-controlled asset trading and reward distribution

## 📋 Table of Contents

- [Features](#-features)
- [Architecture](#️-architecture)
- [Installation](#-installation)
- [Usage](#-usage)
- [Smart Contract Functions](#-smart-contract-functions)
- [Testing](#-testing)
- [Contributing](#-contributing)
- [License](#-license)

## ✨ Features

### 🎮 Core Gaming Features

- **Asset Management**: Mint, transfer, and manage NFT-based gaming assets
- **Avatar System**: Create persistent player characters with progression tracking
- **Experience System**: Level-based progression with configurable experience requirements
- **World Creation**: Deploy custom gaming environments with entry requirements
- **Leaderboard Integration**: Competitive ranking with automated reward distribution

### 🔒 Security & Ownership

- **Decentralized Asset Storage**: All assets stored on Bitcoin-secured Stacks blockchain
- **Permission Management**: Role-based access control for protocol administration
- **Validation Framework**: Comprehensive input validation and error handling
- **Transfer Security**: Safe asset transfers with ownership verification

### 💰 Economic Features

- **Bitcoin Rewards**: Native Bitcoin reward distribution for top players
- **Protocol Fees**: Configurable fee structure for sustainable operations
- **Asset Rarity System**: Multi-tier rarity classification for game assets
- **Prize Pool Management**: Automated prize pool accumulation and distribution

## 🏗️ Architecture

### Smart Contract Structure

```
nexus-vault.clar
├── Constants & Configuration
│   ├── Error Constants (24 error types)
│   ├── Game Mechanics Constants
│   └── Protocol Configuration
├── Data Storage
│   ├── NFT Definitions (Assets & Avatars)
│   ├── Metadata Maps
│   ├── Avatar System
│   ├── Virtual Worlds
│   └── Leaderboard
├── Core Functions
│   ├── Asset Management
│   ├── Avatar Operations
│   ├── World Management
│   ├── Experience System
│   └── Reward Distribution
└── Utility Functions
    ├── Validation Logic
    ├── Access Control
    └── Helper Functions
```

### Key Data Structures

- **nexusvault-asset**: NFT representing game assets with metadata
- **nexusvault-avatar**: NFT representing player avatars
- **asset-metadata**: Asset properties including rarity, power level, and experience
- **avatar-metadata**: Avatar stats, achievements, and equipped assets
- **game-worlds**: Virtual world configurations and statistics
- **leaderboard**: Player rankings and competitive statistics

## 🛠 Installation

### Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) - Stacks development environment
- [Node.js](https://nodejs.org/) (v16 or higher)
- [Git](https://git-scm.com/)

### Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/precious-edioh/nexus-vault.git
   cd nexus-vault
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Verify installation**

   ```bash
   clarinet check
   ```

## 🎯 Usage

### Development Environment

1. **Start Clarinet console**

   ```bash
   clarinet console
   ```

2. **Deploy contract locally**

   ```clarity
   ::deploy_contracts
   ```

3. **Run basic commands**

   ```clarity
   ;; Initialize protocol
   (contract-call? .nexus-vault initialize-protocol u50 u100)
   
   ;; Create avatar
   (contract-call? .nexus-vault create-avatar "PlayerOne" (list u1))
   
   ;; Create game world
   (contract-call? .nexus-vault create-game-world "Fantasy Realm" "Epic adventure world" u100)
   ```

### Testing

```bash
# Run all tests
npm test

# Run tests with coverage
npm run test:report

# Watch mode for development
npm run test:watch
```

### Contract Verification

```bash
# Check contract syntax and logic
clarinet check

# Run contract analysis
clarinet analyze
```

## 📚 Smart Contract Functions

### 🎮 Asset Management

#### `mint-nexusvault-asset`

Creates new game assets with specified properties.

```clarity
(mint-nexusvault-asset 
  "Legendary Sword" 
  "A powerful weapon forged in ancient times" 
  "legendary" 
  u950 
  u1 
  (list "weapon" "melee" "fire-damage"))
```

**Parameters:**

- `name`: Asset name (max 50 characters)
- `description`: Asset description (max 200 characters)
- `rarity`: Asset rarity tier (common, uncommon, rare, epic, legendary)
- `power-level`: Numeric power rating (1-1000)
- `world-id`: Associated world identifier
- `attributes`: List of asset attributes (max 10)

#### `transfer-game-asset`

Transfers asset ownership between players.

```clarity
(transfer-game-asset u1 'SP2J6ZY48GV1EZ5V2V5RB9MP66SW86PYKKNRV9EJ7)
```

### 👤 Avatar System

#### `create-avatar`

Creates player avatar with world access permissions.

```clarity
(create-avatar "DragonSlayer" (list u1 u2 u3))
```

**Parameters:**

- `name`: Avatar name (max 50 characters)
- `world-access`: List of accessible world IDs (max 10)

#### `update-avatar-experience`

Updates avatar experience and handles level progression.

```clarity
(update-avatar-experience u1 u250)
```

### 🌍 World Management

#### `create-game-world`

Deploys new virtual gaming environment.

```clarity
(create-game-world 
  "Cyber Nexus" 
  "Futuristic cyberpunk world" 
  u500)
```

**Parameters:**

- `name`: World name (max 50 characters)
- `description`: World description (max 200 characters)
- `entry-requirement`: Minimum level requirement

### 🏆 Leaderboard & Rewards

#### `update-player-score`

Updates player competitive statistics.

```clarity
(update-player-score 'SP2J6ZY48GV1EZ5V2V5RB9MP66SW86PYKKNRV9EJ7 u1500)
```

#### `distribute-bitcoin-rewards`

Executes automated reward distribution to top players.

```clarity
(distribute-bitcoin-rewards)
```

### 📖 Read-Only Functions

#### `get-world-details`

Retrieves world configuration and statistics.

```clarity
(get-world-details u1)
```

#### `get-avatar-details`

Fetches avatar metadata and progression.

```clarity
(get-avatar-details u1)
```

#### `get-next-level-requirement`

Calculates experience needed for next level.

```clarity
(get-next-level-requirement u1)
```

## 🧪 Testing

The project includes comprehensive test coverage using Vitest and Clarinet SDK.

### Test Structure

```
tests/
└── nexus-vault.test.ts    # Main contract tests
```

### Running Tests

```bash
# Execute all test suites
npm test

# Generate detailed coverage report
npm run test:report

# Development mode with file watching
npm run test:watch
```

### Example Test Cases

- Protocol initialization and configuration
- Asset minting with various parameters
- Avatar creation and progression
- World deployment and management
- Leaderboard operations and rewards
- Error handling and edge cases

## 🤝 Contributing

We welcome contributions to the NexusVault Gaming Protocol! Please follow these guidelines:

### Development Process

1. **Fork the repository**
2. **Create feature branch**

   ```bash
   git checkout -b feature/amazing-feature
   ```

3. **Implement changes**
4. **Add comprehensive tests**
5. **Run test suite**

   ```bash
   npm test
   clarinet check
   ```

6. **Submit pull request**

### Code Standards

- Follow Clarity best practices and conventions
- Include comprehensive error handling
- Add detailed function documentation
- Maintain test coverage above 90%
- Use descriptive variable and function names

### Security Considerations

- All public functions must include proper authorization checks
- Input validation required for all user-provided data
- Follow principle of least privilege for access control
- Consider potential attack vectors and implement safeguards

## 📄 License

This project is licensed under the ISC License - see the [LICENSE](LICENSE) file for details.

## 🔗 Links

- **Stacks Blockchain**: [https://www.stacks.co/](https://www.stacks.co/)
- **Clarity Language**: [https://clarity-lang.org/](https://clarity-lang.org/)
- **Clarinet Documentation**: [https://docs.hiro.so/clarinet](https://docs.hiro.so/clarinet)
- **Vitest Testing Framework**: [https://vitest.dev/](https://vitest.dev/)

---

### Built with ❤️ on Stacks Blockchain

*Empowering the future of decentralized gaming through Bitcoin's security and Clarity's precision.*
