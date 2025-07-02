# Analytics_Position_Case_Study
**Loyalty Points System Evaluation and Redesign Report**

**Submitted by:** Ridham
**Context:** Analytics Case Study for Real-Money Gaming Platform
**Goal:** Evaluate and improve the current loyalty point system to ensure fairness, engagement, and alignment with business goals.

---

### **1. Introduction**

This report presents a detailed evaluation and redesign of the loyalty points system used in a real-money gaming platform. The platform rewards users based on their activity and transaction behavior. The assignment required a data-driven analysis of the existing loyalty point formula, followed by a proposal for a fairer and more effective version. It also included the challenge of designing a suitable bonus distribution method for the top 50 players.

---

### **2. Existing Loyalty Points Formula**

The current loyalty point calculation is defined as:

```
Loyalty Points =
    0.01 × TotalDeposit +
    0.005 × TotalWithdrawal +
    0.2 × GamesPlayed +
    0.001 × (Number of Deposits − Number of Withdrawals)
```

**Observation:** This formula heavily favors users with high deposits and even rewards withdrawals, which can negatively affect the platform’s financial health. It undervalues gameplay and completely ignores user consistency or streaks.

---

### **3. Identified Issues and Difficulties Faced**

During the analysis and implementation, the following issues and challenges were encountered:

* **Unfair Advantage to High Depositors:** Users who deposited large amounts but barely played were still topping the leaderboard.
* **Withdrawals being rewarded:** Giving points for withdrawing money contradicted business interests.
* **Missing Consistency Measurement:** No part of the formula measured loyalty in terms of daily activity or sustained engagement.
* **Overwriting gameplay data:** While merging dataframes, the "Games Played" column was often overwritten or duplicated, leading to 0 values.
* **Bias Detection:** It was difficult to see bias until bonus distribution comparisons were done using Excel.
* **Crash during merge:** Filling NaN after merging deposit/withdrawal data led to data corruption or loss.
* **Manual creation of time slots (S1/S2):** Required transforming datetime into daily time segments manually.
* **Top 50 player bonus fairness:** Needed to design a scalable and fair bonus system that rewards effort, not just money.

---

### **4. Revised Loyalty Formula**

To address the limitations of the original approach, a new loyalty formula is proposed:

```
Loyalty Points =
    0.01 × TotalDeposit +
    0.2 × GamesPlayed +
    0.1 × Consecutive Active Days +
    0.001 × (Number of Deposits − Number of Withdrawals)
```

**Explanation of Components:**

* **TotalDeposit:** Still valued, but balanced with other metrics.
* **GamesPlayed:** Weight increased to properly reward active users.
* **Consecutive Active Days:** New addition to reward consistency and daily commitment.
* **Removed Withdrawal Points:** Withdrawals no longer give positive loyalty points.

---

### **5. Bonus Pool Distribution Strategy**

Instead of a flat or tiered manual bonus model, a **weighted proportional model** was used. Each top 50 player receives a bonus based on their loyalty points after applying the new formula.

This ensures:

* Top performers are fairly rewarded.
* Users with no deposit or minimal gameplay are filtered out.
* Bonus distribution aligns with platform revenue and engagement.

---

### **6. Outcome and Impact**

After applying the new formula and running comparison datasets:

* **Bias dropped significantly.** Players who previously benefited unfairly from withdrawals no longer appeared in the top 10.
* **Engaged players rose in rank.** Users with high game counts and consistent logins moved up.
* **Withdrawals stopped influencing rankings.**

A detailed Excel file was created showing bonus distributions from all three formulas:

* Original formula
* Previous suggested formula (with caps)
* Final balanced formula (with streaks)

Top 10 lists were compared and revealed **completely different players** ranking high across each formula, proving that formula design has massive impact.

---

### **7. Conclusion**

The redesigned loyalty formula solves key problems in the original model and creates a sustainable, scalable rewards system. It fairly acknowledges deposit contributions, encourages real gameplay, and rewards ongoing engagement through daily activity.

This formula aligns well with the business model of a real-money gaming platform. It filters out freeloaders, discourages manipulative deposit-withdraw cycles, and promotes long-term retention. In conclusion, this version of the formula provides a fair, profitable, and engagement-oriented loyalty system.
