# blockchain

A small interactive website that explains blockchain basics — and actually implements one.

Live in the browser, using the real Web Crypto API (SHA-256) and a proof-of-work miner, you can:

- Watch a chain of blocks link together via hash pointers
- Edit a block's data and see the chain break from that point forward
- Re-mine a tampered block to repair the chain
- Mine new blocks and adjust mining difficulty

No build step, no dependencies — it's a single `index.html` file.

## Run it locally

Just open `index.html` in a browser, or serve it:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## View it live

Once GitHub Pages is enabled for this repo (Settings → Pages → Deploy from branch → `main` / root), the site will be available at:

```
https://debansumaji.github.io/blockchain/
```

## What's inside

- `index.html` — the full site: hero, "how it works" explainer, interactive block-editing demo, annotated code walkthrough, and a glossary of terms (hash, nonce, difficulty, consensus, etc.)

## Core concepts implemented

- **`Block`** — holds `index`, `timestamp`, `data`, `previousHash`, `nonce`, and its own `hash`
- **`calculateHash()`** — SHA-256 over the block's contents via `crypto.subtle.digest`
- **`mine(difficulty)`** — proof-of-work: increments `nonce` until the hash starts with `difficulty` leading zeros
- **`Blockchain`** — a chain of blocks, with `addBlock()` and validity checking (`isValid()` style logic) that confirms every hash matches its contents and every `previousHash` matches the block before it

## License

Add a license of your choice (e.g. MIT) if you plan to make this public/open source.
