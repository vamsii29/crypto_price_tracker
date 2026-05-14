# 🪙 Crypto Price Tracker

A command-line tool that fetches live cryptocurrency prices using the [CoinGecko API](https://www.coingecko.com/en/api). Track Bitcoin, Ethereum, and more — with optional price history saved to a local JSON file.

---

## Features

- Fetch live prices for one or more cryptocurrencies in USD
- Choose which coins to track via command-line arguments
- Save timestamped price history to a local JSON file
- Clean, readable terminal output

---

## Requirements

- Python 3.8+
- requests` library (see Installation)

---

## Installation

```bash
# 1. Clone the repository
git clone https://github.com/vamsii29/crypto-price-tracker.git
cd crypto-price-tracker

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate        # macOS/Linux
venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt
```

---

## Usage

### Fetch default coins (Bitcoin + Ethereum)

```bash
python tracker.py
```

### Fetch specific coins

```bash
python tracker.py --coins bitcoin ethereum solana cardano
```

### Save price history to a JSON file

```bash
python tracker.py --coins bitcoin ethereum --save
```

This appends a timestamped entry to `price_history.json` in the project root.

### Full argument reference

| Argument | Type | Default | Description |
|----------|------|---------|-------------|
| `--coins` | list | `bitcoin ethereum` | CoinGecko coin IDs to track |
| `--save` | flag | off | Save results to `price_history.json` |

---

## Example Output

```
=== Crypto Prices (2026-05-07 14:32:01) ===
  bitcoin   : $62,345.00
  ethereum  : $3,120.50
  solana    : $148.22
```

---

## Project Structure

```
crypto-price-tracker/
├── tracker.py          # Main CLI script
├── requirements.txt    # Python dependencies
├── price_history.json  # Auto-generated price log (git-ignored)
├── .gitignore
└── README.md
```

---

## API

Prices are fetched from the free [CoinGecko Simple Price endpoint](https://api.coingecko.com/api/v3/simple/price):

```
GET https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum&vs_currencies=usd
```

No API key required for basic usage.

---

## Roadmap

- [ ] Support multiple fiat currencies (`--currency eur`)
- [ ] Percentage change over 24h
- [ ] CSV export option
- [ ] Colored terminal output with `rich`

---

## License

MIT
