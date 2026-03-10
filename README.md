Foundry Fund Me (English README)
This is a decentralized crowdfunding smart contract project developed as part of the Cyfrin Updraft Foundry Full Stack Development course. It demonstrates how to build, test, and deploy production-ready smart contracts using the Foundry toolchain and Chainlink oracles.

📖 Overview
The FundMe contract allows users to contribute funds (ETH) to a project, ensuring a minimum USD value is met using real-time price feeds.

Key Features
Decentralized Funding: Users can send ETH to the contract.

Oracle Integration: Uses Chainlink Price Feeds to convert ETH to USD on-chain.

Owner Privileges: Only the contract owner can withdraw the collected funds.

Gas Optimized: Implements constant and immutable variables, along with custom errors to minimize gas costs.

Multi-Chain Compatibility: Dynamically selects the correct Price Feed address based on the network (Sepolia, Mainnet, or local Anvil).

🛠 Tech Stack
Solidity: Smart contract logic.

Foundry: Development framework (Forge for testing, Cast for interaction, Anvil for local node).

Chainlink: Decentralized oracles for real-world data.

Make: Task automation via Makefile.

🚀 Quick Start
Prerequisites
Ensure you have the following installed:

Git

Foundry

1. Clone the Repository
git clone https://github.com/Monster-Three/foundry-fundme-f23.git
cd foundry-fundme-f23

2. Install Dependencies
forge install

3. Build the Project
forge build

🧪 Testing
This project includes unit tests, integration tests, and staged deployments.

Run All Tests:

forge test
Test Forked Mainnet (requires an RPC URL):

forge test --fork-url $SEPOLIA_RPC_URL
Check Test Coverage:

forge coverage
Gas Snapshots:

forge snapshot

🚢 Deployment & Usage
Local Deployment (Anvil)
Start the local node:

anvil
Deploy the contract:

forge script script/DeployFundMe.s.sol --rpc-url http://127.0.0.1:8545 --broadcast --private-key <YOUR_PRIVATE_KEY>
Using Makefile (Recommended)
If you have a .env file configured, you can use the following shortcuts:

Deploy to Sepolia: make deploy ARGS="--network sepolia"

Fund the Contract: make fund

Withdraw Funds: make withdraw

📁 Project Structure
Plaintext
.
├── src/                # Core Smart Contracts (FundMe.sol, PriceConverter.sol)
├── script/             # Deployment and Interaction Scripts
├── test/               # Unit and Integration Tests
├── lib/                # External Libraries (Chainlink, etc.)
├── Makefile            # Automation Shortcuts
└── foundry.toml        # Foundry Configuration

🛡 Security & Best Practices
Custom Errors: Uses error FundMe__NotOwner() instead of long strings to save gas.

Input Validation: Strict checks for minimum funding amounts.

Mocking: Includes MockV3Aggregator for testing on local networks without live oracles.

🤝 Acknowledgments
Special thanks to Patrick Collins and the Cyfrin team for the incredible educational resources.

Foundry Fund Me (中文 README)
这是基于 Cyfrin Updraft 的 Foundry 全栈开发课程完成的众筹智能合约项目。该项目展示了如何使用 Solidity 编写去中心化资金募集合约，并利用 Foundry 工具链进行测试、部署和交互。

📖 项目简介
FundMe 是一个去中心化众筹合约，主要功能包括：

资金募集：用户可以发送 ETH，但必须满足最低美元价值（通过 Chainlink 预言机实时换算）。

价格转换：使用 Chainlink Price Feeds 获取 ETH/USD 的最新价格。

资金提取：只有合约所有者（Owner）可以提取合约中的全部资金。

高效存储：通过 constant 和 immutable 关键字以及合理的变量命名优化 Gas。

🛠 技术栈
Solidity: 智能合约语言

Foundry: 强大的以太坊开发框架（Forge, Cast, Anvil）

Chainlink: 提供去中心化预言机价格喂送

Make: 使用 Makefile 简化常用命令

🚀 快速开始
前置要求
确保你已安装以下工具：

Git

Foundry

1. 克隆仓库
git clone https://github.com/Monster-Three/foundry-fundme-f23.git
cd foundry-fundme-f23

1. 安装依赖
forge install

1. 编译项目
forge build

🧪 测试
本项目包含单元测试和集成测试，并支持在不同网络（Anvil 模拟环境或真实分叉网络）上运行。

运行本地测试:
forge test

查看测试覆盖率:
forge coverage

Gas 报告:
forge snapshot

🚢 部署与交互
本地部署 (Anvil)
启动本地节点:
anvil

运行部署脚本:
forge script script/DeployFundMe.s.sol --rpc-url http://127.0.0.1:8545 --broadcast --private-key <YOUR_PRIVATE_KEY>

Makefile 命令 (推荐)
如果你配置了 .env 文件（参考 .env.example），可以使用 Makefile 简化操作：

部署到 Sepolia: make deploy ARGS="--network sepolia"

资金注入: make fund

提取资金: make withdraw

📁 目录结构
Plaintext
.
├── src/                # 智能合约源代码 (FundMe.sol, PriceConverter.sol)
├── script/             # 部署和交互脚本
├── test/               # 测试文件 (单元测试与集成测试)
├── lib/                # 外部库依赖 (chainlink-brownie-contracts等)
├── Makefile            # 快捷命令配置
└── foundry.toml        # Foundry 配置文件

🛡 安全与优化
使用 revert 自定义错误以节省 Gas。

遵循 Solidity 样式指南进行变量命名（如 s_ 前缀表示状态变量）。

构造函数中动态配置 Chainlink Price Feed 地址，增强合约的跨链兼容性。

🤝 致谢
感谢 Patrick Collins 及其团队提供的优质课程。