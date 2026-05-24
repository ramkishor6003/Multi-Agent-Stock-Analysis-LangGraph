# Multi-Agent Stock Analysis with Bilingual Voice (English + Hindi)

A production‑ready **LangGraph**‑powered multi‑agent system that analyzes any stock (e.g., AAPL, MSFT, RELIANCE.NS) using four specialized agents — **Technical**, **Sentiment**, **Risk** and **Volume** — and delivers a final **BUY/SELL/HOLD** recommendation with a **bilingual audio output** (English + Hindi).


Project Live Demo

Project live screen recording:

https://github.com/user-attachments/assets/2439e830-279c-4f01-9ef8-e88bc2e743ed

## Sample of voice output files (English & Hindi)

1. [final_voice.mp3](https://github.com/user-attachments/files/27990013/final_voice.mp3)

2. [final_voice (1).mp3](https://github.com/user-attachments/files/27990178/final_voice.1.mp3)

## Architecture

The system uses a LangGraph state graph where a **Supervisor Agent** coordinates four independent analysis agents:

| Agent | Input Data | Output |
|-------|------------|--------|
| **Technical** | OHLCV prices | Score (-1 to +1) & signal (NEUTRAL/BULLISH/BEARISH) based on Stochastic K, Williams %R, RSI, MACD, moving averages |
| **Sentiment** | News headlines / social media (via TextBlob) | Polarity score, buzz level, confidence level (0‑1) |
| **Risk** | Historical returns, options IV (if available) | Risk grade (LOW/MEDIUM/HIGH), Value‑at‑Risk (VaR), maximum drawdown, volatility |
| **Volume** | Volume & price data | Volume ratio (vs. average), price‑volume correlation, volume signal |

The **Supervisor Agent** aggregates these outputs, computes a risk‑adjusted rating and a confidence band, and issues the **final verdict** with a short‑term horizon (typically 1‑5 trading days).





