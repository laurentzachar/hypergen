# HyperGen — AI Image Studio on HyperCycle

A minimal frontend that lets users pay $1 USDC on Base to generate images via a HyperCycle AI node.

## Stack
- Vanilla HTML/CSS/JS (no build step required)
- ethers.js v6 (CDN)
- USDC on Base mainnet
- HyperCycle Node Manager API

## Flow
1. User connects wallet (Base network)
2. User writes a prompt
3. $1 USDC is transferred on Base to your treasury
4. Request is EIP-191 signed and sent to your HyperCycle node
5. Node Manager verifies signature, routes to AIM
6. Image is returned and displayed

## Quick Start

### Option A — Open directly
Just open `public/index.html` in a browser. No build needed.

### Option B — Serve locally
```bash
npx serve public
# or
python3 -m http.server 3000 --directory public
```

### Option C — Deploy to Vercel
```bash
npm i -g vercel
vercel --prod
```

## Configuration

Copy `.env.example` to `.env` and fill in your values, **or** edit the defaults directly in `public/index.html`:

| Field | Description |
|-------|-------------|
| Node URL | Your HyperCycle node base URL, e.g. `http://1.2.3.4:8080` |
| AIM Path | The image-gen AIM endpoint, e.g. `/aim/image-gen/generate` |
| Treasury | Your wallet address that receives USDC on Base |

## AIM Response Format

Your image AIM should return one of:

```json
{ "image_base64": "<base64>", "mime_type": "image/png" }
```
```json
{ "image_url": "https://..." }
```
Or raw image bytes with `Content-Type: image/png`.

## HyperCycle Docs
https://hypercycle-cbno.gitbook.io/hypercycle-developer-build-guide

## Base Network
- Chain ID: 8453
- USDC: `0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`
- Explorer: https://basescan.org
