# Contracts

## Micropay Contract Functions

- `deposit_from_treasury(address, amount)`
- `deposit_from_user(address, amount)`
- `charge(address, amount)`
- `get_balance(address)`

Additional helper:

- `get_balance_breakdown(address)` for treasury vs user split visibility

## Rules

- Overdraft blocked with `insufficient_balance`
- `charge` callable only by authorized backend signer
- `deposit_from_treasury` callable only by configured treasury signer
- `deposit_from_user` requires user auth
- Events emitted:
  - `deposit`
  - `charge`

## Funding Priority

Charges consume treasury-funded balance first, then user-funded balance. This keeps DAO allocations visible and measurable.
