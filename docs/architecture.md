# Architecture

## Components

1. **Treasury (external org/repo)**  
   Handles governance proposals and approves allocations.
2. **Micropay Soroban Contract**  
   Tracks user balances split by funding source:
   - treasury-funded
   - user-funded
3. **Backend API**  
   Issues API keys, validates requests, calls contract `charge`.
4. **Frontend Dashboard**  
   Displays key, usage, and balance; supports top-up flows.

## Data and Funds Flow

1. Treasury proposal is approved.
2. Treasury sends allocation to micropay contract.
3. Contract records treasury-funded balance for target user/service.
4. Backend receives API request with key.
5. Backend validates key and reads entitlement.
6. Backend calls `charge(user, amount)` on Soroban.
7. Contract emits charge event.
8. Backend returns premium response and records usage metadata.

## Trust Boundaries

- Contract enforces overdraft and signer authorization.
- Backend keeps API credentials and signs charge calls.
- Treasury identity is explicit through configured contract/wallet addresses.
