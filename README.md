
## Setup
1. Copy `.env.template` to `.env` and add your **Testnet** API credentials.
   ```bash
   cp .env.template .env
   # Edit .env and fill BINANCE_API_KEY and BINANCE_API_SECRET
   ```
2. Create virtual env and install dependencies:
   ```bash
   python -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

## How to run (examples)
- Market order (simulation if no python-binance credentials present):
  ```bash
  python src/market_orders.py BTCUSDT BUY 0.001 --testnet
  ```
- Limit order:
  ```bash
  python src/limit_orders.py BTCUSDT SELL 0.001 65000 --testnet
  ```
- Stop-Limit:
  ```bash
  python src/advanced/stop_limit.py BTCUSDT SELL 0.001 64000 63900 --testnet
  ```
- OCO:
  ```bash
  python src/advanced/oco.py BTCUSDT BUY 0.001 70000 64000 --testnet
  ```
- TWAP:
  ```bash
  python src/advanced/twap.py BTCUSDT SELL 0.01 --slices 4 --interval 15 --testnet
  ```
- Grid:
  ```bash
  python src/advanced/grid.py BTCUSDT BUY 0.01 60000 70000 --levels 6 --testnet
  ```

## Notes and assignment compliance
- All calls default to **Testnet** when `--testnet` is used or when `.env` points to the testnet REST URL.
- Logs are written to `bot.log` with timestamps and error traces.
- Advanced order modules provide example implementations; production-ready bots require websockets/account monitoring to reliably implement OCO and cancel-on-fill behaviours.
