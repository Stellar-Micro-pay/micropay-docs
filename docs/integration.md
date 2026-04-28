# Integration

This integration assumes treasury and micropay live in separate repositories and organizations, linked through on-chain addresses and shared wallet identity.

## External Treasury Link

Stellar Treasury repository:
https://github.com/YOUR-USERNAME/stellar-treasury

## Required Configuration

- `TREASURY_CONTRACT_ADDRESS` in micropay backend environment
- `CONTRACT_ADDRESS` for micropay Soroban contract
- Shared signer/wallet identity between governance-approved treasury actions and micropay funding transactions

## How Treasury Sends Funds

1. DAO submits proposal in treasury system.
2. Proposal approved by multisig governance.
3. Treasury executes transfer/allocation transaction toward micropay contract context.
4. Treasury (or authorized workflow) calls `deposit_from_treasury(user, amount)`.

Result: user receives treasury-funded balance bucket in micropay contract.

## How Micropay Receives Funds

Micropay contract validates treasury signer authorization and increments `treasury_funded[user]`.

Contract emits:

- `deposit` event with source `treasury`

## How API Usage Consumes Funds

1. Developer obtains API key from backend (`POST /api-key`).
2. Developer calls protected endpoint:

```bash
curl -H "x-api-key: KEY" http://localhost:8080/premium-data
```

3. Backend middleware validates API key.
4. Backend identifies user address and request price.
5. Backend signs Soroban `charge(user, amount)` call.
6. Contract deducts balance (treasury first, user second), rejects overdraft.
7. Contract emits `charge` event.
8. Backend returns response and records usage counters.
9. Treasury observers track spend through events, balances, and backend usage dashboards.

## Full Request Lifecycle

Treasury proposal approved -> allocation transfer -> `deposit_from_treasury` -> API key issued -> `/premium-data` call -> backend validates key -> on-chain `charge` -> response returned -> usage snapshot updated -> treasury monitors consumption.
