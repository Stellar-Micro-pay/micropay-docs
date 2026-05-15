# Setup

## 1) Contracts

```bash
cd micropay-contracts
cargo build --target wasm32-unknown-unknown --release
```

Deploy contract to Soroban and run `init(backend, treasury)`.

## 2) Backend

```bash
cd micropay-backend
cp .env.example .env
npm install
npm run dev
```

Set:

- `CONTRACT_ADDRESS`
- `TREASURY_CONTRACT_ADDRESS`
- backend wallet keys
- RPC + passphrase

## 3) Frontend

```bash
cd micropay-frontend
npm install
npm run dev
```

Update backend base URL in `src/api.ts` if needed.
