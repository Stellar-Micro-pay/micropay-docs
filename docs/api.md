# API

Base URL: `http://localhost:8080`

## Endpoints

### `POST /api-key`

Issue API key for a user/service identity.

Request:

```json
{
  "userAddress": "G...",
  "source": "treasury"
}
```

### `GET /usage`

Requires `x-api-key` header.  
Returns request count and total charged.

### `GET /balance`

Requires `x-api-key` header.  
Returns funding source and on-chain balance.

### `POST /top-up`

Trigger top-up flow with source:

- `treasury` (allocation-driven)
- `user` (self-funded)

### `GET /premium-data`

Protected endpoint that charges `REQUEST_COST_STROOPS` per request.

Example:

```bash
curl -H "x-api-key: KEY" http://localhost:8080/premium-data
```
