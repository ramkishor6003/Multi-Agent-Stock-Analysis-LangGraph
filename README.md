# Multi-Agent Stock Analysis with Bilingual Voice (English + Hindi)

A production‑ready **LangGraph**‑powered multi‑agent system that analyzes any stock (e.g., AAPL, MSFT, RELIANCE.NS) using four specialized agents — **Technical**, **Sentiment**, **Risk** and **Volume** — and delivers a final **BUY/SELL/HOLD** recommendation with a **bilingual audio output** (English + Hindi).


Project Live Demo

Project live screen recording:

https://github.com/user-attachments/assets/2439e830-279c-4f01-9ef8-e88bc2e743ed

## Sample of voice output files (English & Hindi)

1. [final_voice.mp3](https://github.com/user-attachments/files/27990013/final_voice.mp3)

2. [final_voice (1).mp3](https://github.com/user-attachments/files/27990178/final_voice.1.mp3)

##  Features

-  **Technical Agent** – Stochastic %K, Williams %R, SMAs, composite score
-  **Sentiment Agent** – Polarity from mock news headlines (extendable to real APIs)
-  **Risk Agent** – VaR (95%), CVaR, annual volatility, max drawdown, Sortino & Calmar ratios
-  **Volume Agent** – Volume ratio, OBV momentum, price‑volume correlation
-  **Supervisor Node** – Dynamic weighting, conflict detection, final verdict & confidence band
-  **Bilingual Voice** – gTTS generates `final_voice.mp3` with both English and Hindi commentary
-  **Gradio UI** – Simple web interface for any stock symbol and time period
-  **Custom Serializer** – Handles pandas `DataFrame` in LangGraph checkpointing

---

## Architecture

The system is built as a **LangGraph state machine** with four parallel agents and a supervisor:


START → data_fetcher → technical → sentiment → risk → volume → supervisor → END



- `data_fetcher` downloads historical data via `yfinance`
- All four agents run asynchronously (LangGraph `async` nodes)
- The **supervisor** calculates a weighted composite score and resolves conflicts
- Checkpointing is enabled with an **in‑memory saver** using the custom `CustomSerializer`

---

## Tech Stack

| Category         | Libraries                                                                 |
|------------------|---------------------------------------------------------------------------|
| Core framework   | `langgraph`, `langgraph-checkpoint`                                       |
| Data & analysis  | `pandas`, `numpy`, `yfinance`, `ta` (technical indicators)               |
| NLP & sentiment  | `textblob`                                                                |
| Serialization    | `pickle` + custom serializer for `DataFrame`                             |
| Audio            | `gTTS`                                                                    |
| Web UI           | `gradio`                                                                  |
| Utilities        | `asyncio`, `datetime`, `warnings`, `typing`, `enum`, `pydantic`           |

---




