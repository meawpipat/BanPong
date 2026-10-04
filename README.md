# BanPong

KUB wallet dashboard for Bitkub Chain (mainnet, chain id 96).

Single self-contained `index.html` — no build step, no backend. All data is
read directly from the browser via public JSON-RPC endpoints
(`https://rpc.bitkubchain.io`, fallback `https://96.rpc.thirdweb.com`).

## Tabs

- **Balance** — KUB balance for a fixed list of 25 wallets, auto-refreshes every 5s.
- **Tx Count** — outgoing tx count (nonce) per wallet via `eth_getTransactionCount`,
  auto-refreshes every 5s, plus a manual "Refresh now" button.
- **EventMint** — usage of the `EventMintV1` contract
  (`0x9F1EaF1A3FBb4d238f679B1c3BAcb8B49b427441`): how much of each product has been
  minted, read straight from `products(id)` via `eth_call` — no log scanning, no indexer.
  Shows paused state, product count, and per-product `minted / maxSupply`.

  Notes: product ids are **0-based**; ERC-20 products count coins in wei (18 decimals), so
  their totals are kept separate from NFT piece counts; the 143 calls are chunked 50 per
  batch. Function selectors are hardcoded (taken from the Hardhat artifact) so the page
  needs no keccak library.

## Run locally

Just open `index.html` in a browser — no server required.

## Deploy

Any static host works (GitHub Pages, Cloudflare Pages, Netlify, etc.) since
this is a single static HTML file with inline CSS/JS.
