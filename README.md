# 🧠 Cognitive Twin — Automated Trading Psychology Engine

### **AI-powered personal trading assistant that learns your behavior, your patterns, and helps you avoid emotional mistakes.**

## 🚀 Overview

Cognitive Twin is a **browser extension + backend AI system** that automatically:

- Captures all your trades from platforms like **TradingView, Robinhood, Webull, Alpaca, TDAmeritrade**
- Screenshots your chart at entry/exit
- Logs your behavior automatically (no journaling needed)
- Analyzes patterns in your wins and losses using embeddings + clustering
- Generates **daily personalized trading psychology reports**
- Detects bias, revenge trading, overtrading, FOMO and hidden weaknesses

This is **NOT** a trading bot.
It is a **psychological mirror** designed to help retail traders act like professionals.

## 🏗 Architecture Overview

### **1. Browser Extension**

Runs in Chrome/Firefox and automatically extracts:

- Order events
- Fills and P&L
- Chart screenshots
- Emotional context signals
- User patterns

Each platform has a scraper module:

```bash
extension/src/sites/*.js
```

### **2. Backend API (Fly.io / FastAPI)**

Receives data from extension:

- `/ingest/trade`
- `/ingest/screenshot`
- `/sync`
- `/report`
- `/patterns`

Runs:

- Embedding generation
- Pattern clustering
- Behavioral drift analysis
- Daily cognitive summary

### **3. Database (Fly.io Postgres + pgvector)**

Tables:

- users
- trades
- screenshots
- embeddings
- pattern_clusters

## 📦 Running the Extension (Dev Mode)

### 1. Go to:

**Chrome → Extensions → Developer Mode → Load Unpacked**

### 2. Load folder:

```bash
cognitive-twin/extension/
```

### 3. Start backend first so API calls connect.

## 🚀 Running Backend on Fly.io

### 1. Install Fly CLI:

```bash
curl -L https://fly.io/install.sh | sh
```

### 2. Deploy:

```bash
flyctl launch
flyctl deploy
```

### 3. Create Postgres:

```bash
flyctl postgres create
flyctl postgres attach --app cognitive-twin
```

## 🛠 Development (Backend)

```bash
cd backend
pip install -r requirements.txt
uvicorn app.main:app --reload
```

## 🧪 Database Schema (Simplified)

Located at:

```bash
backend/app/db/schema.sql
```

Tables include:

- trades
- screenshots
- trade_embeddings
- pattern_clusters

## 🧠 Features (v1.0)

- Auto trade detection
- Auto screenshots
- Auto journaling
- Zero manual input
- Bias detection
- Pattern recognition
- Cognitive drift alerts
- Daily psychology report

## 💡 Roadmap (Future)

- Mobile Safari support
- Real-time trade coaching
- Telegram notifications
- Pattern heatmaps
- Strategy consistency scoring

## 🤝 Contributing

PRs welcome.
This system is intended to remain open-source for independent traders.
