# 🔍 DeFi Credit Scoring using Aave V2 Wallet Transactions

## 📌 Problem Statement

You are given 100,000 raw transaction-level records from the Aave V2 protocol, involving user wallet actions like:
- `deposit`, `borrow`, `repay`, `redeemunderlying`, and `liquidationcall`

Your goal is to:
- Build a **machine learning model** that assigns a **credit score between 0 and 1000** to each wallet
- Base this score **solely on historical transaction behavior**
- Write a one-step script that:
  - Takes the input JSON file
  - Produces credit scores in a CSV format
  - Generates a distribution plot

---

## ✅ Method Chosen

Since no ground truth scores were provided, we used a **self-supervised machine learning approach**:

- **Step 1**: Engineer behavior-based features for each wallet
- **Step 2**: Use **PCA** on feature matrix to generate a **behavioral complexity signal** (as synthetic labels)
- **Step 3**: Train an actual machine learning model (**XGBoost Regressor**) on those features
- **Step 4**: Predict scores and normalize them to a 0–1000 scale

PCA is used only to generate the temporary training signal. The final model is fully ML-driven and learns true behavior patterns.

---

## ✅ Architecture

| Step | Description |
|------|-------------|
| 1️⃣ | Parse the 100K records from `user-wallet-transactions.json` |
| 2️⃣ | Extract features per wallet: action counts, amount stats, token diversity, active days |
| 3️⃣ | Use PCA to produce a label signal capturing behavioral richness |
| 4️⃣ | Train `XGBRegressor` on the behavior features |
| 5️⃣ | Predict scores and normalize them to 0–1000 |
| 6️⃣ | Save output to `output.csv` and plot as `plot.png` |

---

## ✅ Files

| File                        | Description                             |
|-----------------------------|-----------------------------------------|
| `main.ipynb`                | Full pipeline: load → process → model → output |
| `user-wallet-transactions.json` | Raw data input                    |
| `output/output.csv`         | Final credit scores for each wallet     |
| `output/plot.png`           | Distribution plot of credit scores      |
| `analysis.md`               | Score range analysis and behavior insight |

---

## ✅ How to Run

1. Place `user-wallet-transactions.json` inside the `data/` folder
2. Run `main.ipynb` in Google Colab
3. It will:
   - Extract features
   - Train the model
   - Predict scores
   - Output `output.csv` and `plot.png`

---

## ✅ Output Sample

| userWallet        | creditScore |
|------------------|--------------|
| 0x3F...           | 998.24       |
| 0x15...           | 934.11       |
| 0x98...           | 785.67       |

---

## ✅ Model Used

- **XGBoost Regressor**: A robust, high-performance gradient boosting model
- Used **MinMaxScaler** to normalize predictions to 0–1000
- No rule-based scoring or manual thresholds

---

## ✅ Licensing

This solution is built for the ZeruFinance DeFi Credit Scoring challenge and is intended for research and evaluation purposes only.