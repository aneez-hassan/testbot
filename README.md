# Simplified Binance Futures Trading Bot (Testnet)

This repository contains a minimal Python trading bot designed to interact with the **Binance Futures Testnet (USDT-M)**. It demonstrates how to place MARKET, LIMIT, and STOP-LIMIT orders, view balance, and cancel orders using signed REST requests.

> **Warning:** This project is for educational/testing purposes only. Use **Testnet** API keys — do **not** use real funds or production API keys with this code unless you audit and harden it for production use.

---

## What's included

* `simplified_trading_bot.py` — Main Python CLI script with:

  * REST signing (HMAC-SHA256)
  * MARKET, LIMIT, STOP-LIMIT order placement
  * Balance query and order cancellation
  * Input validation and logging to `trading_bot.log`

* `trading_bot.log` — (generated at runtime) rotating log file that records requests, responses, and errors.

---

## Requirements

* Python 3.8+
* `requests` library

Install dependencies:

```bash
pip install requests
```

---

## Getting Testnet API Keys

1. Visit: `https://testnet.binancefuture.com`
2. Create an account (or log in)
3. Go to **API Management** and create an API Key
4. Copy the **API Key** and **Secret** (secret shown only once) — store them securely

---

## Usage

### CLI (local)

Run the script and pass API credentials on the command line.

Examples:

```bash
# Market buy
python simplified_trading_bot.py --api-key YOUR_KEY --api-secret YOUR_SECRET market --symbol BTCUSDT --side BUY --quantity 0.001

# Limit sell
python simplified_trading_bot.py --api-key YOUR_KEY --api-secret YOUR_SECRET limit --symbol BTCUSDT --side SELL --quantity 0.001 --price 50000

# Stop-limit (trigger stopPrice, place a limit order)
python simplified_trading_bot.py --api-key YOUR_KEY --api-secret YOUR_SECRET stop_limit --symbol BTCUSDT --side SELL --quantity 0.001 --stop-price 49500 --price 49400

# Show futures balance
python simplified_trading_bot.py --api-key YOUR_KEY --api-secret YOUR_SECRET balance

# Cancel order
python simplified_trading_bot.py --api-key YOUR_KEY --api-secret YOUR_SECRET cancel --symbol BTCUSDT --order-id 12345678
```

### Google Colab

A Colab-ready snippet is included in the conversation. To use it:

1. Open a new Colab notebook
2. Paste the Colab cell code from the conversation
3. Provide Testnet API credentials when prompted

---

## Logging

* The script writes detailed logs to `trading_bot.log` (RotatingFileHandler). Logs include request URLs (signed), responses, and exceptions.
* Keep logs for your submission when applying — the hiring task requests log files.

---

## Notes & Caveats

* Quantity means contract quantity for USDT-M futures — check symbol-specific lot size/precision on Testnet.
* This script does **not** perform advanced risk checks, rate-limit retries, or order sizing logic — add these for production.
* For production systems, never store API secrets in plain text. Use a secure secrets manager.

---

## Optional Enhancements (suggested)

* Add TWAP, Grid, or OCO order strategies
* Interactive CLI improvements (confirmation prompts, dry-run mode)
* Save logs to Google Drive automatically and collect them for submission
* Add unit tests, CI, and packaging for pip installation

---

## License

MIT License — feel free to modify for your submission.

---

## Contact

If you want, I can:

* package this into a GitHub repo with sample logs and a `requirements.txt`,
* add a small web/CLI UI, or
* implement a bonus order type (e.g., OCO or TWAP).

Tell me which next step you prefer.
