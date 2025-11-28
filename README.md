# linea-20

Send multiple ERC20 token transfers on Linea.

## Setup

```bash
bun install
```

Setup `.env`:
```bash
cp .env.example .env
```

## Usage

```bash
bun run index.js \
  --rpc https://rpc.linea.build \
  --token 0xTOKEN_ADDRESS \
  --to 0xDESTINATION_WALLET \
  --count 20 \
  --min 0.01 \
  --max 0.5
```

### Options

- `--count` - Number of transactions (default: 20)
- `--min` / `--max` - Random amount range per tx
- `--delay` - Seconds between txs (default: 1.0)
- `--dry-run` - Preview without sending
- `--yes` - Skip confirmation prompt
