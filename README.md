Market Pulse — Trading & Paper-Trading Platform
A lightweight web platform for live crypto + forex price tracking, TradingView-powered charting, and a paper-trading terminal with basic P&L and portfolio tracking. Built with vanilla HTML/CSS/JavaScript for fast, framework-free deployment and easy customization.

⚠ Disclaimer: This project is for education and paper-trading only. It does not provide financial advice, nor execute real trades.

Market Pulse Trading Platform
A live trading dashboard for crypto and forex pairs with paper trading support.

🚀 Live Demo: market-pulse-trading-platform.vercel.app

Table of Contents
Features
Architecture & Tech Stack
Live Data Sources
Project Structure
Getting Started
Configuration
Usage Guide
TradingView Integration
Paper-Trading Engine
Security Notes
Troubleshooting
Roadmap
Contributing
License
Acknowledgements
Features
Real-time prices

Crypto spot pairs (e.g., BTC/USDT, ETH/USDT)
Major forex pairs (e.g., EUR/USD, USD/JPY)
Auto-refreshing tickers, last price, % change, and indicative spreads (provider-dependent)
Pro-grade charts (TradingView)

Interactive candlesticks, multiple intervals (1m → 1D+)
Indicators via TradingView widget (user can customize inside the chart)
Dark/Light themes (configurable)
Paper-trading terminal

Place simulated Market / Limit orders
Portfolio view with positions, average price, P&L, equity curve
Balance & “buying power” tracked locally (persisted in localStorage)
Auth (optional)

Frontend auth scaffold (e.g., Firebase Web Auth) for Login/Signup
Simple route-guarding for dashboard pages
Responsive UI

Works on desktop and mobile
Lightweight; no heavy frameworks required
Architecture & Tech Stack
Frontend: HTML5, CSS3, JavaScript (ES6+)
Charts: TradingView Embedded Widget (tv.js)
Data Providers (configurable):
Crypto: CoinGecko (no key) or Twelve Data / Alpha Vantage (API key)
Forex: ExchangeRate.host (no key) or Twelve Data / Alpha Vantage (API key)
Storage: Browser localStorage (for session, preferences, paper-trading state)
Auth (optional): Firebase Web SDK (Email/Password)
This repo is intentionally front-end first: you can add a small proxy/edge worker later if you need to hide API keys or aggregate data server-side.

Live Data Sources
You can choose one or mix:

Asset Class	Provider	Key Needed	Notes
Crypto	CoinGecko	No	Free; rate limits; great for spot prices
Crypto/FX	Twelve Data	Yes	REST/WebSocket; generous free tier
Crypto/FX	Alpha Vantage	Yes	Free tier; 5 req/min limit
FX	ExchangeRate.host	No	Free; suitable for lightweight quotes
You can switch providers in /js/config.js without touching UI code.

Project Structure
Market-Pulse-Trading-Platform/ ├─ index.html ├─ dashboard.html ├─ auth.html # login/signup screen (if combined) ├─ /assets/ │ ├─ css/ │ │ ├─ reset.css │ │ └─ styles.css │ └─ img/ │ └─ (logos, icons, screenshots) ├─ /js/ │ ├─ config.sample.js # copy -> config.js and fill keys/options │ ├─ auth.js # login/signup; guards; session │ ├─ dashboard.js # charts, tickers, watchlist │ ├─ data.js # price fetching, normalizers │ ├─ papertrading.js # order engine, portfolio, P&L │ ├─ ui.js # DOM utils, toasts, modals │ └─ vendor/ │ └─ tv.js # TradingView loader (via CDN in HTML) ├─ /docs/ │ └─ screenshots/ # add UI screenshots for README └─ README.md

Getting Started
1) Clone
git clone https://github.com/Shashwat189/Market-Pulse-Trading-Platform.git
cd Market-Pulse-Trading-Platform
                                       
2) Create config
cp js/config.sample.js js/config.js

Usage Guide
Login / Signup (optional)

Enable auth via CONFIG.auth.enabled = true.

On first run, create an account. Session is cached in localStorage.

Route guards prevent access to dashboard.html unless authenticated.

Dashboard

Watchlist: add/remove symbols (BTCUSDT, ETHUSDT, EURUSD, etc.)

Prices: live updates based on selected provider; click a symbol to focus chart

Chart: powered by TradingView (see below)

Terminal: place Market or Limit orders into the paper engine

Settings

Switch providers, theme, base currency, and default chart symbol.

Reset paper-trading account (resets balances and positions).


  Acknowledgements

TradingView for the embedded charting widget

CoinGecko / Alpha Vantage / Twelve Data / ExchangeRate.host for price data

Icons & UI inspiration from open web design systems

Author: Shashwat Kaul
Email- shashwatkaul092005@gmail.com
