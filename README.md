# -Wallet-Risk-Scoring-From-Scratch

## Zeru Round 2: Wallet Risk Scoring (Compound Protocol)

###  Data Collection:
- Simulated sample transaction data for 3 wallets based on expected Compound V2 behavior (supply, borrow, repay, liquidation, activity).
- In actual implementation, data can be fetched from Covalent, Flipside Crypto, or via on-chain Web3.py calls.

###  Feature Selection:
- **Repayment Ratio** = total_repaid / total_borrowed
- **Collateral Ratio** = total_supplied / total_borrowed
- **Liquidation Count** = indicator of high risk
- **Last Active Days Ago** = recent activity is lower risk
- **Total Borrowed** = large positions increase risk

### Scoring Method:
- Used MinMax normalization on selected features
- Weighted scoring model:
  - +30% repayment ratio
  - +25% collateral ratio
  - +15% total borrowed (positive shows activity)
  - -20% liquidation count
  - -10% inactivity
- Final score scaled to range 0–1000

###  Deliverables:
- `wallet_risk_scores.csv` with risk scores for 3 wallets
- Full code included in repo for scoring logic
