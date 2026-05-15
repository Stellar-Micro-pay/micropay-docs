# Micropay Documentation Repository

Canonical technical documentation for the Stellar Micropay ecosystem, including architecture, contracts, APIs, and external treasury integration boundaries.

## Overview

`micropay-docs` centralizes project documentation used by developers, operators, and ecosystem reviewers. It defines how the micropayments platform works, how components integrate, and how treasury-funded usage is represented.

This repository is intended to be the shared source of truth for implementation and operational docs across backend, frontend, and contract repositories.

## Ecosystem Context

This docs repository describes a multi-repo ecosystem.

- DAO Treasury system is external and maintained in a separate GitHub organization/repository.
- Treasury governance/funding code is not part of this repository.
- Micropay repositories consume treasury allocations via contract-level interactions.

No shared codebase exists between Treasury and Micropay. Integration is documented through:

- smart contract interfaces
- API-level integration patterns
- known contract addresses and signer conventions

## Documentation Scope

- Product and protocol overview
- System architecture and sequence flows
- Smart contract function and event references
- Backend API specifications and examples
- Local/dev/test setup guides
- External treasury integration playbooks
- Contribution and release documentation standards

## Repository Structure

```text
.
`-- docs/
    |-- overview.md      # Purpose, value proposition, and ecosystem context
    |-- architecture.md  # Component topology and request/funding flows
    |-- contracts.md     # Soroban interfaces, auth model, and events
    |-- api.md           # HTTP endpoints, request/response contracts
    |-- setup.md         # Local environment setup and deployment prerequisites
    `-- integration.md   # Cross-system integration with external DAO Treasury
```

## Writing Standards

- Be explicit about boundary of responsibility between Treasury and Micropay.
- Favor deterministic language over marketing language.
- Keep examples executable and version-aware.
- Document breaking changes and migration implications.
- Ensure contract and API docs stay synchronized with shipped code.

## How to Use This Repository

- Start with `docs/overview.md` for context.
- Use `docs/architecture.md` for implementation planning.
- Use `docs/contracts.md` and `docs/api.md` during development.
- Use `docs/integration.md` for cross-org treasury coordination.

## Contribution Workflow

1. Create branch: `docs/<topic>` or `fix/docs-<topic>`.
2. Update relevant docs with clear rationale and impact.
3. Validate that examples and addresses are current.
4. Open PR including:
   - changed documents
   - reason for change
   - impacted repositories/services

## Related Repositories

- Micropay Backend: [github.com/Stellar-Micro-pay/micropay-backend](https://github.com/Stellar-Micro-pay/micropay-backend)
- Micropay Contracts: [github.com/Stellar-Micro-pay/micropay-contracts](https://github.com/Stellar-Micro-pay/micropay-contracts)
- Micropay Frontend: [github.com/Stellar-Micro-pay/micropay-frontend](https://github.com/Stellar-Micro-pay/micropay-frontend)
- External DAO Treasury (separate org/repo): [github.com/Stellar-Treasury/Treasury-frontend](https://github.com/Stellar-Treasury/Treasury-frontend)

## License

MIT (or project-level license policy).
