# Polymer 🧪

A comprehensive trading and DeFi toolkit for Polymarket interactions and automated trading strategies.

## Overview

Polymer is a monorepo containing:
- **rs-clob-client**: A Rust client library for interacting with CLOB (Central Limit Order Book) APIs
- **simple-bot**: An automated trading bot built on top of the CLOB client with multiple trading strategies
- **site**: Web interface and utilities for visualization and management

## Projects

### rs-clob-client 📚

A feature-rich Rust client library for CLOB API interactions.

**Features:**
- WebSocket support for real-time market data
- Authentication with private keys
- Order management (place, cancel, update orders)
- Market data streaming
- RFQ (Request for Quote) support
- Bridge operations
- CTF (Conditional Token Framework) interactions
- Gamma module for risk assessment

**Location:** `./rs-clob-client`

**Quick Start:**
```rust
use rs_clob_client::ClobClient;

let client = ClobClient::new(base_url);
let markets = client.get_markets().await?;
```

See `rs-clob-client/README.md` and `rs-clob-client/examples/` for detailed usage.

### simple-bot 🤖

An automated trading bot with multiple strategy implementations for trading on Polymarket.

**Features:**
- Multiple trading strategies:
  - **Arbitrage**: Capitalize on price differences
  - **Bayesian**: Probabilistic price prediction
  - **Frontload**: Early position taking
  - **Sniper**: Rapid execution for time-sensitive opportunities
- Real-time orderbook monitoring
- Trade history tracking
- Backtesting capabilities
- CLI interface for configuration and control
- Approvals and token management

**Location:** `./simple-bot`

**Requirements:**
- Set `POLYMARKET_PRIVATE_KEY` in `.env`
- Funded wallet for trading

**Quick Start:**
```bash
cd simple-bot
cargo build --release
cargo run -- --strategy arbitrage
```

See `simple-bot/README.md` for detailed documentation.

### site 🌐

Web interface and utilities for visualization and data management.

**Features:**
- Dashboard visualization
- Market data display
- Strategy configuration interface
- Performance metrics tracking
- Image generation utilities

**Location:** `./site`

## Setup

### Prerequisites
- Rust 1.70+ (for Rust projects)
- Python 3.8+ (for site utilities)
- Git

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Shubham-Rasal/polymer.git
cd polymer
```

2. Create `.env` file in `simple-bot/` with your configuration:
```bash
cd simple-bot
cp .env.example .env  # if available
# Edit .env with your POLYMARKET_PRIVATE_KEY
```

3. Build the projects:
```bash
# Build CLOB client library
cd rs-clob-client
cargo build --release

# Build trading bot
cd ../simple-bot
cargo build --release
```

## Usage

### Running the Trading Bot

```bash
cd simple-bot

# Display help
cargo run -- --help

# Run arbitrage strategy
cargo run --release -- --strategy arbitrage

# Run backtesting
cargo run --release -- --backtest
```

### Using the CLOB Client Library

Add to your `Cargo.toml`:
```toml
[dependencies]
rs-clob-client = { path = "../rs-clob-client" }
```

Then use in your code:
```rust
use rs_clob_client::ClobClient;
```

## Security

⚠️ **Important:** Never commit `.env` files or private keys to version control.

- `.env` files are gitignored
- Private keys should only be stored locally
- Use environment variables for sensitive data
- Review all transactions before execution

## Project Structure

```
polymer/
├── rs-clob-client/       # CLOB API client library
│   ├── src/              # Source code
│   ├── examples/         # Usage examples
│   ├── tests/            # Test suite
│   └── Cargo.toml        # Rust dependencies
├── simple-bot/           # Trading bot
│   ├── src/              # Bot implementation
│   ├── src/strategies/   # Trading strategies
│   └── Cargo.toml        # Rust dependencies
├── site/                 # Web interface
│   ├── index.html        # Main page
│   └── images/           # Generated visualizations
├── skills/               # Custom utilities
├── .gitignore            # Git configuration
└── README.md             # This file
```

## Testing

```bash
# Run tests for CLOB client
cd rs-clob-client
cargo test

# Run tests for trading bot
cd ../simple-bot
cargo test
```

## Documentation

- [rs-clob-client Documentation](./rs-clob-client/README.md)
- [simple-bot Documentation](./simple-bot/README.md)
- [Examples](./rs-clob-client/examples/)

## Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see LICENSE files in individual projects for details.

## Disclaimer

This software is provided for educational and research purposes. Trading involves risk. Always test strategies in paper trading mode before using real funds.

## Support

For issues, questions, or suggestions:
- Open an [issue](https://github.com/Shubham-Rasal/polymer/issues)
- Check existing documentation
- Review example code

---

Built with ❤️ for the Polymarket ecosystem
