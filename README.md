# 🧠 Training the Perfect Trader: A Reinforcement Learning Approach

This project explores the application of **Reinforcement Learning (RL)** for stock trading, comparing three key algorithms: **PPO**, **Recurrent PPO**, and **A2C**. Our goal is to identify robust, adaptive strategies capable of outperforming traditional methods under varying market conditions.

📍 **GitHub**: [https://github.com/rogerhsiehh/DMU](https://github.com/rogerhsiehh/DMU)  
🎥 **Video Demo**: [Watch here](https://drive.google.com/file/d/1gxMLyhWfYKoPDn30XYiu1wuriji-6G2B/view)

---

## 📈 Overview

Traditional trading systems often fail to adapt to dynamic stock markets. In this project, we:
- Built a custom Gym-based trading environment
- Applied advanced RL agents to learn buy/sell strategies
- Evaluated their performance using financial metrics across four stocks: **NVDA**, **AMD**, **ARM**, and **TEM**

---

## 🧪 Algorithms Compared

| Algorithm       | Description |
|----------------|-------------|
| **PPO**         | Policy-gradient method with clipped objective for stability |
| **Recurrent PPO** | PPO + LSTM layers for better sequence modeling |
| **A2C**         | Actor-Critic method optimized for synchronous training |

Implemented using **Stable-Baselines3**.

---

## 🏗 Environment

We modified the [Gym-AnyTrading](https://github.com/AminHP/gym-anytrading) environment:
- Custom reward functions based on profit with transaction costs
- Scaled features using `StandardScaler`
- Action space: `Buy`, `Sell`
- Observations: price, volume, 10+ technical indicators (e.g., SMA, EMA, RSI, MACD)

---

## 📊 Datasets

- **Source**: Yahoo Finance via `yfinance` API
- **Stocks**: NVIDIA (NVDA), AMD, ARM, TEM
- **Period**: Jan 2020 – Present
- **Split**:
  - Train: Jan 2020 – Sep 2023  
  - Val: Oct 2023 – Sep 2024  
  - Test: Oct 2024 onward

---

## ⚙️ Hyperparameter Tuning

- **Tool**: [Optuna](https://optuna.org/)
- **Method**: Bayesian Optimization
- **Trials**: 200 per model
- **Evaluation**: Validation reward over 20 episodes, every 500 timesteps

---

## 🏁 Results Summary

| Model         | Total Reward (NVDA) | Total Profit | Notes |
|---------------|----------------------|--------------|-------|
| PPO           | -2.49                | 0.89         | Poor learning stability |
| **Recurrent PPO** | **39.39**              | **1.38**       | Best performer overall |
| A2C           | 14.70                | 0.97         | Good risk-adjusted returns |

### 📉 On Other Stocks

| Stock | Best Model         | Sharpe Ratio | Total Profit |
|-------|--------------------|--------------|--------------|
| AMD   | PPO                | 0.03         | 0.99         |
| ARM   | Recurrent PPO      | 2.45         | 2.28         |
| TEM   | A2C                | 1.63         | 1.80         |

---

## 🔁 Baselines for Comparison

| Strategy            | Description |
|---------------------|-------------|
| **Buy & Hold**       | Passive strategy, buy at start and hold |
| **Moving Avg Crossover** | Technical rule-based strategy using SMA/EMA |

> RL agents (especially Recurrent PPO) consistently outperformed Moving Average strategies, and often beat Buy & Hold under volatile conditions.

---

## 📌 Key Observations

- Recurrent PPO shows superior temporal modeling → best for volatile stocks.
- A2C is most robust for **drawdown control**.
- PPO needs tuning to avoid overfitting or unstable learning.
- Moving Average strategies underperformed in all tests.

---
