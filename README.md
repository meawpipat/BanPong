# BanPong

KUB wallet dashboard for Bitkub Chain (mainnet, chain id 96).

Single self-contained `index.html` — no build step, no backend. All data is
read directly from the browser via public JSON-RPC endpoints
(`https://rpc.bitkubchain.io`, fallback `https://96.rpc.thirdweb.com`).

## Tabs

- **Balance** — KUB balance for a fixed list of 25 wallets, auto-refreshes every 5s.
- **Tx Count** — outgoing tx count (nonce) per wallet via `eth_getTransactionCount`,
  auto-refreshes every 5s, plus a manual "Refresh now" button.

## Run locally

Just open `index.html` in a browser — no server required.

## Deploy

Any static host works (GitHub Pages, Cloudflare Pages, Netlify, etc.) since
this is a single static HTML file with inline CSS/JS.
