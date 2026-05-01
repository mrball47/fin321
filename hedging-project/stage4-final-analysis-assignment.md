# Final Analysis, Prompt Engineering & Recommendation

---

### A. Exposure Summary

The firm is anticipating a Euro-denominated receivable, due in one year at a baseline value of $20,000,000 USD. Because our functional currency is the US dollar, this unhedged cash flow exposes our projected revenue to volatility in the EUR/USD exchange rate. To manage this risk, we created an AI-replicable model to analyze various hedging strategies for the receivable, modeling such strategies under various levels of volatility, and provide recommendations for the firm.

Over a 1-year horizon, the EUR/USD exchange rate is susceptible to macroeconomic volatility driven by changes in central bank interest rates, shifting inflation data, and geopolitical uncertainty. If the Euro weakens before the settlement date, the converted USD equivalent of our revenue will decline. 

Securing such risk will accomplish the following:
  * Protect the receivable's USD value against adverse currency movements. 
  * Balance downside protection with hedging costs (minimizing upfront cash requirements and premiums, or avoiding unnecessary strain the firm's balance sheets and credit lines).
  * Establish a framework for evaluating future international receivables and mitigating currency risk.

---

### B. Summary of Hedge Outcomes

Our key findings are summarized in the following table:

| Strategy | Methodology | Insight | Results |
|----------|------------------|-----------------|-------|
| **Forward Hedge** | Provides complete certainty for future USD proceeds at a given forward rate. | Requires no upfront premium, but eliminates any upside profit potential if the Euro appreciates. | Won 0/13 scenarios |
| **Money Market Hedge** | Borrows against the expected Euro receivable today, converts to USD at the current spot rate, and uses the incoming Euro payment to retire the debt next year. | Eliminates upside potential, and consumes the firm's credit capacity needed to borrow. | Won 6/13 scenarios |
| **No Hedge** | Continue without any safeguards against FX volatility. | Preserves credit with unlimited upside potential, but risks full exposure to downside risk. | Won 7/13 scenarios |

---

### C. Sensitivity Interpretation

Our findings were organized across various sensitivities, which spanned +/-5% from the current EUR/USD spot rate ($1.18). These sensitivies allow us to evaluate which hedging strategies are best if the EUR depreciates or appreciates within the model's parameters.

The no hedge strategy proved to be the most profibable from the current spot rate upwards, which represent scenarios where the EUR appreciates. The money market hedge won in the sensitivities below the current spot rate, which represent scenarios where the EUR depreciates. The forward hedge implicitly wins at any scenarios below the quoted forward rate (1.0935); however, these sensitivities are below the model's given range of uncertainty.

The no hedge strategy captures full upside from the baseline rate, but also is exposed to downside risk. The money market hedge eliminates any such risk, but consumes credit capacity needed to execute the hedge. The forward rate may be beneficial for its aforementioned sensitivities, but such levels represent a relatively large downside move from current levels.

| EUR/USD Spot Exchange Rate | Winner |
|----------|------------------|
| **$1.12** | Money Market Hedge |
| **$1.13** | Money Market Hedge |
| **$1.14** | Money Market Hedge |
| **$1.15** | Money Market Hedge |
| **$1.16** | Money Market Hedge |
| **$1.17** | Money Market Hedge |
| **$1.18** | No Hedge |
| **$1.19** | No Hedge |
| **$1.20** | No Hedge |
| **$1.21** | No Hedge |
| **$1.22** | No Hedge |
| **$1.23** | No Hedge |
| **$1.24** | No Hedge |

---

### D. Strategic Recommendation

The model 

---

### E. Executive Justification

Use management-level reasoning:
- Cash flow stability
- Budget certainty
- Liquidity impact
- Optionality value
- Premium costs
- Accounting implications (optional)

---

### F. Structured AI Prompt (Required Component)

Write a **1–2 page structured prompt** (as a separate section or appendix) that could instruct an AI to generate your complete FX hedging spreadsheet. Your prompt must include:

1. **Scenario-Specific Variables** — All values explicitly stated: FC_AMT, spot rate, forward rate, interest rates, option strikes, premiums, T_DAYS. AI does not infer missing data.

2. **Named Range Conventions** — Use standardized names matching your Stage 3 spec (e.g., `FC_AMT`, `S0_in`, `F0_in`, `R_USD`, `R_FC`, `K_PUT`, `K_CALL`, `PREM_PUT`, `PREM_CALL`, `T_DAYS`).

3. **Spreadsheet Requirements** — Instruct the AI to produce:
   - Input section with named ranges
   - Color coding: **Yellow** = Inputs, **Blue** = Assumptions, **Green** = Formulas, **Gray** = Outputs
   - Forward hedge, Money Market hedge (3-step), Option hedges (put and call)
   - Sensitivity table (±5% range)
   - Verification checks (forward vs. MM parity, formula consistency)

4. **Hierarchical Structure** — Use clear section headers (e.g., `# GOAL`, `# INPUT VARIABLES`, `# MODEL LOGIC`, `# VERIFICATION`, `# EXPORT`).

---

## Prompt Engineering Best Practices

### 1. Avoid Vague Prompts

Example of a bad prompt:
> "Make me an FX hedging spreadsheet."

Example of a good prompt:
> "Create an Excel workbook modeling forward, money market, and option hedges for a EUR 4,500,000 receivable using the following market data. Use named ranges matching the convention FC_AMT, S0_in, F0_in..."

### 2. Provide All Variable Values

AI does not infer values. Include every scenario variable explicitly.

### 3. Use Named Ranges Consistently

Never allow the AI to invent its own naming system. Define names in your prompt.

### 4. Specify Formatting Explicitly

Color codes, sections, layout — be explicit.

### 5. Include Context Files from GitHub

This is the most efficient way to use AI for models.

**Options for providing context:**
1. **Best:** GitHub links to your spec and template files
2. **Medium:** Upload `.md` or `.xlsx` files directly
3. **Least:** Copy/paste text manually

---

## Note on AI Access

If you do not have access to an AI tool capable of generating Excel files, you may:
1. Submit your structured prompt (Section F) as written.
2. Submit your Stage 2 model as the primary spreadsheet artifact with a brief note explaining that you would use the prompt to regenerate it.

The prompt itself is the primary deliverable — it demonstrates your ability to convert domain knowledge into machine-readable instructions.

---

## Areas for Further Study & Improvement

In 1–2 paragraphs each, discuss **2–3** of the following topics and how they connect to your project:

1. **AI Skills & Automation** — How could AI tools (e.g., Claude Skills, Code Interpreter) pull live market data, regenerate your model on demand, or run Monte Carlo simulations?
2. **Multi-File Reasoning** — How could AI read your spec, model, and prompt together to maintain consistency, automate rebuilds, or create dashboards?
3. **GitHub & Version Control** — How does committing specs, models, and prompts to GitHub enable auditable, reproducible model regeneration? Tie this to your Stages 1–3.
4. **Accounting & Audit Integration** — How do hedge accounting flows (OCI vs. P&L), documentation requirements, and reproducibility connect to this project? How could GitHub serve as audit evidence?

---
