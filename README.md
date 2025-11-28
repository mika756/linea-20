# linea-20

Send multiple ERC20 token transfers on Linea.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fsavioruz%2Flinea-20&env=PRIVATE_KEY,API_KEY,PORT&envDefaults=%7B%22PRIVATE_KEY%22%3A%220xYOUR_PRIVATE_KEY%22%2C%22API_KEY%22%3A%22YOUR_API_KEY%22%2C%22PORT%22%3A%223000%22%7D&project-name=linea-20&repository-name=linea-20)

## Setup

```bash
bun install
```

Setup `.env`:
```bash
cp .env.example .env
```

## Usage

### CLI

```bash
bun start \
  --rpc https://rpc.linea.build \
  --token 0xTOKEN_ADDRESS \
  --to 0xDESTINATION_WALLET \
  --count 20 \
  --min 0.01 \
  --max 0.5
```

or

```
node cmd/index.js \
  --rpc https://rpc.linea.build \
  --token 0xTOKEN_ADDRESS \
  --to 0xDESTINATION_WALLET \
  --count 20 \
  --min 0.01 \
  --max 0.5
```

**Options:**
- `--count` - Number of transactions (default: 20)
- `--min` / `--max` - Random amount range per tx
- `--delay` - Seconds between txs (default: 1.0)
- `--dry-run` - Preview without sending
- `--yes` - Skip confirmation prompt

### API Server

Start the server:
```bash
bun server
```

**Endpoints:**

Start a batch:
```bash
curl -X POST http://localhost:3000/batch \
  -H "Content-Type: application/json" \
  -H "x-api-key: YOUR_SECRET_KEY" \
  -d '{
    "rpc": "https://rpc.linea.build",
    "token": "0xTOKEN_ADDRESS",
    "to": "0xDESTINATION_WALLET",
    "count": 20,
    "min": "0.01",
    "max": "0.5"
  }'
```

Check status:
```bash
curl http://localhost:3000/batch/{jobId}
```

List all jobs:
```bash
curl http://localhost:3000/batch
```
