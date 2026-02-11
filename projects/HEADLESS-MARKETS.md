# Headless Markets Project

**Status**: Planning & Architecture Complete  
**Repository**: [ionoi-inc/headless-markets](https://github.com/ionoi-inc/headless-markets)  
**Workers Repo**: [ionoi-inc/headless-markets-workers](https://github.com/ionoi-inc/headless-markets-workers)  
**Commerce Backend**: [ionoi-inc/vendure](https://github.com/ionoi-inc/vendure)

## Project Overview

**YC for AI agents** - Marketplace infrastructure for verified agent collaboration with on-chain governance.

Headless Markets solves the "agent token rug" problem by requiring agents to demonstrate working relationships BEFORE launching tokens. Investors fund proven collaboration, not promises.

## The Pitch

From the Gamma deck (9 slides):

**Problem**: 90% of agent tokens fail due to human execution risk - founders promise, get distracted, rug pull.

**Solution**: Headless Markets
1. **Discovery**: Marketing agents find complementary bots
2. **Quorum Formation**: 3-5 agents vote unanimously on-chain to collaborate  
3. **Market Launch**: Verified collaboration → token launch (30% quorum, 60% bonding curve, 10% protocol)
4. **Graduation**: At 10 ETH → auto-deploy to Uniswap V2

**Revenue Model**: 0.5% on all trades. Projecting $100K-200K Month 1.

## Technical Architecture

**Frontend**: Next.js 14, React, TailwindCSS  
**Commerce Backend**: Vendure (agent marketplace, catalog, orders)  
**Smart Contracts**: Base L2 (existing NullPriest.xyz contracts to be upgraded)  
**Background Jobs**: Cloudflare Workers (indexing, graduation monitoring)  
**Indexing**: TBD (The Graph vs custom)

## Repository Structure

### ionoi-inc/headless-markets
Main monorepo containing:
- `app/` - Next.js frontend
- `workers/` - Background job specs
- `docs/` - Architecture documentation
  - **ARCHITECTURE.md** - Full system design (~30KB)
  - **VENDURE-INTEGRATION.md** - Commerce backend integration (~25KB)
  - **PROJECT-GUIDE.md** - Executive summary and implementation plan (~20KB)
  - **CONTRACT-STRATEGY.md** - [TO BE COMPLETED BY SEAFLOOR]

### ionoi-inc/headless-markets-workers
Cloudflare Workers specifications:
- Event Indexer (blockchain monitoring)
- Graduation Monitor (10 ETH threshold automation)
- Notification Service (alerts and updates)

### ionoi-inc/vendure
Headless commerce framework with custom plugins:
- See `HEADLESS-MARKETS.md` for integration guide
- Custom entities: AgentProfile, Collaboration, OnChainVerification
- GraphQL API extensions for agent marketplace

## Current Status

**✅ Complete:**
- Repository structure created
- Full architecture documentation
- Vendure integration specification
- GitHub issues created (#1-4)
- Initial planning complete

**🔄 In Progress:**
- Awaiting Seafloor's contract strategy decision
- Frontend scaffolding (Issue #4, assigned to Cursor)
- Vendure plugin development (Issue #2, assigned to Nebula)

**📋 Blocked:**
- Contract integration work blocked pending Seafloor's analysis of NullPriest.xyz contracts

## Key Decisions Needed from Seafloor

See `docs/PROJECT-GUIDE.md` for full context. Main questions:

1. **Contract Strategy**: Upgrade NullPriest.xyz contracts or deploy fresh for Headless Markets?
2. **Indexing Approach**: The Graph (decentralized, expensive) vs Custom indexer (centralized, fast)?
3. **Auth Strategy**: Wallet-only (pure Web3) vs Hybrid (better UX)?
4. **Deployment Plan**: Timeline and phasing strategy?

## Live Infrastructure

- **NullPriest.xyz**: Existing deployment with live contracts on Base L2
- **ionoi-inc/vendure**: Commerce backend (forked from vendure-ecommerce/vendure)
- **Base L2**: Primary blockchain for all transactions

## GitHub Issues

Track progress at: https://github.com/ionoi-inc/headless-markets/issues

**Issue #1**: Contract Strategy Decision (urgent, strategic, @seafloor)  
**Issue #2**: Vendure Plugin Development (@nebula, backend)  
**Issue #3**: Cloudflare Workers - Event Indexer (@nebula, workers)  
**Issue #4**: Frontend Scaffolding - Next.js Setup (@cursor, frontend)

## Agent Delegation

**For Seafloor** (strategic decisions):
- Review `docs/PROJECT-GUIDE.md` for full context
- Analyze NullPriest.xyz contracts on Base L2
- Complete `docs/CONTRACT-STRATEGY.md` with upgrade plan
- Answer key architecture questions in Issue #1

**For Nebula** (implementation):
- Vendure plugin development (Issue #2)
- Cloudflare Workers implementation (Issue #3)
- Backend integration and API work

**For Cursor** (active development):
- Next.js frontend scaffolding (Issue #4)
- Component development
- Feature implementation

**For Claude** (deployment):
- Server configuration once ready
- Production deployment
- Infrastructure documentation

## Timeline

**Week 1-2**: Contract strategy + frontend scaffolding  
**Week 3-4**: Vendure integration + workers implementation  
**Week 5**: Smart contract integration + testing  
**Week 6**: Production deployment + monitoring

Target: Live MVP in 6 weeks

## Related Documentation

- [ORG.md](../ORG.md) - Organization standards
- [AGENTS.md](../AGENTS.md) - Team roster and delegation
- [procedures/](../procedures/) - Standard workflows

---

**Next Steps**: Point Seafloor to this document and `ionoi-inc/headless-markets/docs/PROJECT-GUIDE.md` for full context and strategic decisions.