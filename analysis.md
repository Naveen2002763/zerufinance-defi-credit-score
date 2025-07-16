# 📊 Analysis – Wallet Credit Score Distribution

After training and scoring all 3,497 unique wallets using the XGBoost model, we analyzed the distribution of scores to understand wallet behavior across different levels of creditworthiness.

---

## 🔹 Score Distribution Plot

![Credit Score Distribution](plot.png)

The distribution is **right-skewed**, showing:
- Most wallets are in the **low credit range**
- A small elite group scores above 800

---

## 🔹 Credit Score Ranges Breakdown

| Score Range  | Wallet Count | Behavior Summary |
|--------------|--------------|------------------|
| **0–100**    | 2089         | Inactive or single-use wallets; low interaction |
| **100–200**  | 392          | Minimal borrowers or redeemers; risky profiles |
| **200–400**  | 515          | Mild usage, no repayments, or low diversity |
| **400–600**  | 317          | Moderately engaged, balanced wallets |
| **600–800**  | 162          | Responsible wallets with repayment & diversity |
| **800–1000** | 21           | Top 1% – long-term active, reliable users |

---

## 🔹 Interpretation

### 🔻 Lower Scored Wallets (0–200):
- Often have only 1–2 transactions
- Usually borrowed or redeemed, but no repayment
- Limited token interaction and time range

### 🔺 Higher Scored Wallets (600–1000):
- Display consistent deposit and repay activity
- Engage with multiple asset tokens
- Active over long durations
- Never liquidated

---

## ✅ Conclusion

- The score distribution is realistic for a DeFi protocol where:
  - Many wallets are temporary or bot-based
  - Fewer wallets are deeply involved in lending/repaying
- The model successfully differentiates wallet creditworthiness from behavior

These insights can be used for:
- Risk flagging
- Trust scoring
- Protocol governance participation