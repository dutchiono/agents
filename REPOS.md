# ionoi-inc Repository Inventory

**Last Updated**: 2026-02-11  
**Total Repositories**: 30  
**Organization**: [ionoi-inc](https://github.com/ionoi-inc)

---

## Purpose

This document serves as the **single source of truth** for all repositories in the ionoi-inc organization. It helps agents quickly understand:
- What repos exist and their purpose
- Which repos are relevant for specific tasks
- How repos relate to each other
- Where to document new work

**Update this file whenever:**
- A new repository is created
- A repository is archived or deleted
- A repository's purpose changes significantly
- You need to reference repos for planning or research

---

## Core Platform Repositories

### [headless-markets](https://github.com/ionoi-inc/headless-markets)
**Purpose**: Main platform - YC for AI agents  
**Tech Stack**: Next.js, React, TailwindCSS, Vendure  
**Status**: 🏗️ Active development  
**Key Features**: Agent marketplace, quorum governance, token launches, Uniswap V2 graduation  
**Payment Needs**: Token bonding curves, marketplace transactions, 10% protocol fee collection, treasury management

### [headless-markets-workers](https://github.com/ionoi-inc/headless-markets-workers)
**Purpose**: Cloudflare Workers backend for Headless Markets  
**Tech Stack**: Cloudflare Workers, serverless architecture  
**Relation**: Backend infrastructure for headless-markets frontend

### [vendure](https://github.com/ionoi-inc/vendure)
**Purpose**: Headless e-commerce backend (fork/config of Vendure framework)  
**Tech Stack**: Vendure, GraphQL  
**Relation**: E-commerce engine for Headless Markets

---

## Smart Contract Repositories

### [nullpriest-treasury-contracts](https://github.com/ionoi-inc/nullpriest-treasury-contracts)
**Purpose**: Treasury management smart contracts for NullPriest.xyz integration  
**Tech Stack**: Solidity, Hardhat  
**Relation**: Handles 10% protocol fees from token launches

### [bonding-curve-market](https://github.com/ionoi-inc/bonding-curve-market)
**Purpose**: Linear bonding curve implementation for token launches  
**Tech Stack**: Solidity  
**Relation**: Core token launch mechanism

### [marketfactory](https://github.com/ionoi-inc/marketfactory)
**Purpose**: Factory contract for deploying new agent markets  
**Tech Stack**: Solidity  
**Relation**: Deploys market instances on-chain

### [quorum-governance](https://github.com/ionoi-inc/quorum-governance)
**Purpose**: On-chain voting and unanimous consensus for agent quorums  
**Tech Stack**: Solidity  
**Relation**: Enables 3-5 agents to vote on partnerships

### [uniswap-graduation-manager](https://github.com/ionoi-inc/uniswap-graduation-manager)
**Purpose**: Auto-deployment to Uniswap V2 at 10 ETH market cap  
**Tech Stack**: Solidity  
**Relation**: Graduation mechanism from bonding curve to DEX

### [hardhat-test-suite-framework](https://github.com/ionoi-inc/hardhat-test-suite-framework)
**Purpose**: Testing framework for smart contracts  
**Tech Stack**: Hardhat, TypeScript, Mocha  
**Relation**: Shared test infrastructure

### [logistico](https://github.com/ionoi-inc/logistico)
**Purpose**: [Description TBD - appears to be Solidity-based]  
**Tech Stack**: Solidity  
**Status**: Recently updated (19 minutes ago as of 2026-02-11 16:20 EST)

---

## Agent & Infrastructure Repositories

### [agents](https://github.com/ionoi-inc/agents)
**Purpose**: Central coordination hub - onboarding docs, agent roster, communication protocols  
**Contents**: README.md (mission), ORG.md (principles), AGENTS.md (team roster), REPOS.md (this file)  
**Status**: ✅ Active documentation  
**Critical Role**: This is where agents learn how to work together

### [nullpriest](https://github.com/ionoi-inc/nullpriest)
**Purpose**: NullPriest agent infrastructure and operations  
**Relation**: Autonomous agent operations and treasury management

### [fathom](https://github.com/ionoi-inc/fathom)
**Purpose**: Fathom agent infrastructure  
**Relation**: Related to autonomous agent operations

---

## System Architect Repositories

These repos contain architecture documentation and patterns for building specialized systems:

### [finance-system-architect](https://github.com/ionoi-inc/finance-system-architect)
**Purpose**: Financial system design patterns and architecture

### [support-system-architect](https://github.com/ionoi-inc/support-system-architect)
**Purpose**: Customer support system design patterns

### [sales-system-architect](https://github.com/ionoi-inc/sales-system-architect)
**Purpose**: Sales system design patterns

### [marketing-system-architect](https://github.com/ionoi-inc/marketing-system-architect)
**Purpose**: Marketing system design patterns

---

## Application Repositories

### [sshappy](https://github.com/ionoi-inc/sshappy)
**Purpose**: React Native SSH/SFTP mobile app for server management  
**Tech Stack**: React Native, SSH/SFTP libraries  
**Status**: Active development  
**Monetization Potential**: SaaS subscription model, crypto payments for privacy-focused users

### [server-manager](https://github.com/ionoi-inc/server-manager)
**Purpose**: Server management tooling (may be related to SSHappy)  
**Tech Stack**: TBD

### [icp-server-experiments](https://github.com/ionoi-inc/icp-server-experiments)
**Purpose**: Internet Computer Protocol (ICP) server experiments  
**Tech Stack**: ICP/Dfinity

### [nft-portfolio-app](https://github.com/ionoi-inc/nft-portfolio-app)
**Purpose**: NFT portfolio tracking application

### [polymarket-edge-monitor](https://github.com/ionoi-inc/polymarket-edge-monitor)
**Purpose**: Polymarket prediction market edge detection and monitoring  
**Relation**: Trading signal generation for crypto markets

---

## Business & Service Examples

These appear to be reference implementations or client projects:

### [restaurant-pos-system](https://github.com/ionoi-inc/restaurant-pos-system)
**Purpose**: Restaurant POS system architecture and implementation  
**Payment Needs**: POS terminal integration, split checks, tip handling, EMV compliance

### [hvac-ai-secretary](https://github.com/ionoi-inc/hvac-ai-secretary)
**Purpose**: AI secretary for HVAC businesses  
**Use Case**: Appointment scheduling, customer service automation

### [smiths-lawn-care](https://github.com/ionoi-inc/smiths-lawn-care)
**Purpose**: Lawn care business example implementation

### [marras-barrels](https://github.com/ionoi-inc/marras-barrels)
**Purpose**: [Client project or reference implementation - TBD]

---

## Development & Testing

### [demoScanners](https://github.com/ionoi-inc/demoScanners)
**Purpose**: Demo scanner implementations (possibly for testing/examples)

### [vibe-starter](https://github.com/ionoi-inc/vibe-starter)
**Purpose**: Starter template or boilerplate project

### [TavernKeeper](https://github.com/ionoi-inc/TavernKeeper)
**Purpose**: [Description TBD]

### [daemon_protocol](https://github.com/ionoi-inc/daemon_protocol)
**Purpose**: Daemon/background process protocol implementation

---

## Repository Categories

### By Purpose
- **Core Platform** (3): headless-markets, headless-markets-workers, vendure
- **Smart Contracts** (8): nullpriest-treasury-contracts, bonding-curve-market, marketfactory, quorum-governance, uniswap-graduation-manager, hardhat-test-suite-framework, logistico, daemon_protocol
- **Infrastructure** (3): agents, nullpriest, fathom
- **System Architecture** (4): finance/support/sales/marketing-system-architect repos
- **Applications** (5): sshappy, server-manager, icp-server-experiments, nft-portfolio-app, polymarket-edge-monitor
- **Business Examples** (4): restaurant-pos-system, hvac-ai-secretary, smiths-lawn-care, marras-barrels
- **Dev/Testing** (3): demoScanners, vibe-starter, TavernKeeper

### By Payment Infrastructure Relevance

**CRITICAL (Immediate Need)**:
- `headless-markets` - Core platform needs payment rails, fee collection, treasury integration
- `nullpriest-treasury-contracts` - 10% protocol fee management
- `bonding-curve-market` - Token purchase payment handling

**HIGH (Strong Use Case)**:
- `restaurant-pos-system` - Full payment terminal integration, POS processing
- `sshappy` - Potential SaaS monetization with subscriptions
- `marketfactory` - Market deployment fees
- `headless-markets-workers` - Payment processing backend

**MEDIUM (Documentation/Reference)**:
- `agents` - Should document payment best practices and patterns
- `finance-system-architect` - Financial infrastructure patterns
- Business example repos (HVAC, lawn care, Marra's Barrels)

**CRYPTO-NATIVE**:
- All smart contract repos (Base L2 blockchain payments built-in)
- `nullpriest-treasury-contracts` (on-chain treasury management)

---

## Payment Infrastructure Applications

### Headless Markets Integration Points

1. **Token Launch Fees**
   - Bonding curve purchases (crypto payments on Base L2)
   - 30% to quorum, 60% to bonding curve, 10% to protocol treasury
   - Gas fee optimization

2. **Marketplace Transactions**
   - Agent service fees
   - Discovery/listing fees
   - Verification badges (premium features)

3. **Treasury Management**
   - NullPriest.xyz integration (10% protocol allocation)
   - Multi-sig wallet setup
   - Automated distribution to agent quorums

4. **Fiat On-Ramps** (Future consideration)
   - Credit card → crypto conversion for non-crypto users
   - Stripe → Coinbase Commerce bridge
   - Compliance: FinCEN MSB registration, state licensing

### SSHappy Monetization Options

1. **Subscription Model**
   - Free tier: 3 servers
   - Pro tier ($9.99/mo): Unlimited servers
   - Team tier ($49.99/mo): Shared access, audit logs

2. **Payment Methods**
   - Stripe (credit card, ACH)
   - Crypto option (privacy-focused users expect this)
   - Apple/Google In-App Purchase (30% fee)

3. **Compliance**
   - EU VAT handling
   - US sales tax (state-by-state)
   - Privacy: GDPR, CCPA

### Restaurant POS System

Research document covers:
- Square vs Clover vs Toast comparison
- EMV terminal integration
- PCI-DSS compliance
- Offline-first architecture
- Split check handling
- Tip calculation and distribution

---

## Communication Protocol

When working across these repos, follow the guidelines in ORG.md:

**Issue Tags for Cross-Repo Coordination**:
- `nebula` - Cloud agent needed
- `seafloor` - Strategic decision needed
- `scrawl` - NullPriest/Fathom operations
- `claude` - Server/deployment work
- `cursor` - Active development
- `urgent` - Immediate attention
- `handoff` - Passing work between agents

**Standard Workflow**:
1. Create issue in relevant repo
2. Tag appropriately for agent coordination
3. Reference related repos/issues
4. Update documentation when complete

---

## Maintenance Guidelines

### When Creating a New Repo

1. Add entry to this document under appropriate category
2. Include: name, purpose, tech stack, status, relation to other repos
3. Update "Total Repositories" count at top
4. Commit with message: `docs: add [repo-name] to REPOS.md inventory`

### When Archiving a Repo

1. Move entry to "Archived Repositories" section (create if needed)
2. Add archive date and reason
3. Update "Total Repositories" count
4. Update any cross-references in other sections

### When Significant Changes Occur

Update the "Last Updated" date and relevant sections whenever:
- Repository purpose changes
- Tech stack undergoes major refactor
- Payment integration is added/removed
- Cross-repo dependencies change

---

## Quick Reference: Finding the Right Repo

**I need to...**
- Document agent coordination → `agents`
- Build smart contracts → `hardhat-test-suite-framework`, contract-specific repos
- Deploy Headless Markets → `headless-markets`, `headless-markets-workers`, `vendure`
- Handle token launches → `bonding-curve-market`, `marketfactory`
- Manage treasury → `nullpriest-treasury-contracts`
- Build mobile apps → `sshappy` (React Native reference)
- Design system architecture → system-architect repos
- Set up payment processing → See "Payment Infrastructure Applications" section above

---

## Related Documents

- [README.md](./README.md) - Organization mission and core project overview
- [ORG.md](./ORG.md) - Organization principles and communication protocols  
- [AGENTS.md](./AGENTS.md) - Agent team roster and delegation guidelines
- [Payment Infrastructure Report](../docs/ionoi_small_business_payment_infrastructure_report.md) - Comprehensive payment setup research

---

**Questions about this inventory?** Tag issues with `nebula` for cloud agent coordination or `seafloor` for strategic decisions.
