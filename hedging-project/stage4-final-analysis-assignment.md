<img width="230" height="24" alt="image" src="https://github.com/user-attachments/assets/1bb236dc-697d-44df-8fe4-24e92ba110ac" /># Final Analysis, Prompt Engineering & Recommendation

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

The no hedge strategy proved to be the most profibable from the current spot rate upwards, which represent scenarios where the EUR appreciates. The money market hedge won in the sensitivities below the current spot rate, which represent scenarios where the EUR depreciates. The forward hedge implicitly wins at any scenarios below the quoted forward rate ($1.0935); however, these sensitivities are below the model's given range of uncertainty.

The no hedge strategy captures full upside from the baseline rate, but also is exposed to downside risk. The money market hedge eliminates any such risk, but consumes credit capacity needed to execute the hedge. The forward rate may be beneficial for its aforementioned sensitivities, but such levels represent a relatively large downside move from current levels.

| EUR/USD Spot Exchange Rate | Winner (of Hedge/No Hedge) | (of Hedges) |
|----------|------------------|------------------|
| **$1.12** | Money Market Hedge | Money Market Hedge | 
| **$1.13** | Money Market Hedge | Money Market Hedge | 
| **$1.14** | Money Market Hedge | Money Market Hedge | 
| **$1.15** | Money Market Hedge | Money Market Hedge | 
| **$1.16** | Money Market Hedge | Money Market Hedge | 
| **$1.17** | Money Market Hedge | Money Market Hedge | 
| **$1.18** | No Hedge | Money Market Hedge | 
| **$1.19** | No Hedge | Money Market Hedge | 
| **$1.20** | No Hedge | Money Market Hedge | 
| **$1.21** | No Hedge | Money Market Hedge | 
| **$1.22** | No Hedge | Money Market Hedge | 
| **$1.23** | No Hedge | Money Market Hedge | 
| **$1.24** | No Hedge | Money Market Hedge | 

---

### D. Strategic Recommendation

The [hedging model](https://github.com/mrball47/fin-321/blob/main/hedging-project/stage2-excel/model-updated.xlsx) suggests that — relative to the baseline spot rate of $1.18 — using a no hedge strategy would be the most protifable for the firm based on the given sensitivities' win percentages. However, completely leaving the receivable exposed to adverse FX changes would be a risk if the EUR/USD were to move below the current spot rate. Even if it removes any upside potential from an appreciation in the EUR, it would be best for the firm to use a money market hedge in anticipation of the firm's receivable.

It is important to note that the model assumes no fees, commissions, and transaction costs for any hedging strategies, with its underlying data quoted on April 17, 2026 at 5:00 PM EDT. It also assumed that the ability to borrow and execute within certain parameters of a hedging strategy can be met, with and tax implications and transactional complications being ignored.

---

### E. Executive Justification

Both the money market the forward hedge lock in USD proceeds with full certainty, which are less risky than an unprotected no hedge strategy. However, the money market hedge solidifies a receivable value of $19,995,950, which is around $1.4 million more than the forward hedge at $18,589,035. The sensitivity table shows that for the comparisons between all strategies excluding the no hedge, the money market hedge was more profitable at all sensitivites until the quoted forward rate at $1.0935. 

While the money market hedge does carry some complexity in its usage of credit to execute a spot conversion, it secures more USD proceeds outright while eliminating risks in EUR depreciation. The forward hedge is mathematically inferior unless the spot rate falls to below $1.0935, which represents a move larger than +/-5%. Relative to that differential, the forward rate fails to comparatively retain profitability at levels above the forward rate. Leaving $1.4 million on the table in exchange for protection against that large of a swing doesn't seem feasible for the immmediate proceeds that can be guaranteed.

In addition to tying up credit, the firm also faces complexities in accounting for a money market hedge. Taking out a foreign loan and creating a domestic cash asset simultaneously increases assets and liabilities on the balance sheet. This temporary inflation can negatively skew certain financial ratios — like debt-to-equity or return on assets — until the receivable is collected and the loan is paid off.

---

### F. Structured AI Prompt 

Here is a comprehensive prompt you can use to instruct an AI or financial analyst to recreate this hedging model:

Your task is to recreate a specific financial model for "Hedging Foreign Currency Receivables." Please generate the step-by-step instructions, exact formulas, and structural layout required to build this model in Excel. Below are the specific requirements, hardcoded variables, formatting rules, and mathematical logic you must follow.

1. Formatting and Color Coding

Create a "Key" section at the top right of the spreadsheet to establish standard financial modeling formatting:

* Editable: Set background color to pink for editable inputs that are hardcoded given variables.
* Outcome: Set background color to yellow for final results of a hedging strategy.
* Formulas: Set text color to blue for cell used to calculate via a formula that isn't a final outcome.

2. Input Variables 

Set up the top left section of the sheet with the following exact labels and values in subsequent columns "Given" and "Variables". Ensure the values are formatted as specified in the Key. 

* 1-Year Receivable: (Baseline value in foreign denomination)
* Current EUR/USD Spot Exchange Rate: ($)
* Money Market - U.S. 1-Year Interest Rate (domestic): (%)
* Money Market - E.U. 1-Year Interest Rate (foreign): (%)
* Forwards - EUR/USD 1-Year Forward Exchange Rate: ($)

3. Hedging Strategies 

Below the inputs, create two distinct blocks for calculating the hedges. Provide the Excel formulas required to calculate each step based on the inputs above.

Block 1: Forward Hedge

* Row Label: [a] Sell EUR/USD 1-Year Forward
  * Calculation: Multiply the 1-Year Receivable by the 1-Year Forward Exchange Rate.
  * Formatting: Outcome, ($); Add the text "<-- LOCKED IN: in one year we will have this amount to the right of the result."

Block 2: Money Market Hedge (Provide the three distinct steps required to execute this hedge.)

* Step [a] Borrow the discounted present value of the foreign receivable
  * Divide the 1-Year Receivable by (1 + E.U. 1-Year Interest Rate).
  * Formatting: Formula, (foreign denomination)
  
*Step [b] Convert [a] into domestic at the current spot exchange
 * Calculation: Multiply the result of Step [a] by the Current EUR/USD Spot Exchange Rate. 
 * Formatting: Formula, ($)
 
* Step [c] Invest [b] at the prevailing domestic interest rate
  * Calculation: Multiply the result of Step [b] by (1 + U.S. 1-Year Interest Rate). Format as Yellow background (Outcome).
  * Formatting: Outcome, ($); Add the text "<-- LOCKED IN: in one year we will have this amount to the right of the result."

4. Senario Analysis

Create a large data table at the bottom of the spreadsheet to analyze how different future spot prices impact the strategies. Provide the exact logic/formulas for each column.

Row Setup:
Create a column starting at the current spot rate, and incrementally increase/decrease by $0.01 until the table is organized +/-5% from the current baseline. Add side notes outside the table decreasing from the current spot rate "<-- Worse ([foreign currency] depreciates)", at the current spot rate "Baseline", and increasing from the current spot rate "<-- Better ([foreign currency] appreciates).

Column Headers & Logic:

Apply a gradient ranging from green to red, that transitions from yielding most to leave converted proceeds, respectively.

* In one year, we receive - 0. No Hedge: Multiply the Future Spot Price in that row by the original 1-Year Receivable.
* In one year, we receive - 1. Forward Hedge: Absolute reference to the Forward Hedge Outcome. This number is static through all sensitivities.
* In one year, we receive - 2. Money Market Hedge: Absolute reference to the Money Market Hedge Outcome. This number is static all the way down.

* Hedge Profit (Loss) vs. No Hedge - 1. Forward Hedge: Subtract the "0. No Hedge" value from the "1. Forward Hedge" value for that row.
* Hedge Profit (Loss) vs. No Hedge - 2. Money Market Hedge: Subtract the "0. No Hedge" value from the "2. Money Market Hedge" value for that row. 

* Winner - of Hedge / No Hedge: Write an IF statement that compares the three "In one year, we receive" columns. It should output the text name of the column that yields the highest value (e.g., "0. No Hedge", "1. Forward Hedge", or "2. Money Market Hedge"). 
* Winner - of Hedges: Write an IF statement comparing only the Forward Hedge vs. Money Market Hedge columns. It should output the text name of the winning hedge. 

Please generate the complete guide so a user can build this from scratch.

Please reference the following for a hypothetical [scenario](https://github.com/mrball47/fin-321/blob/main/hedging-project/scenario.md) and [model](https://github.com/mrball47/fin-321/blob/main/hedging-project/stage2-excel/model-updated.xlsx) produced from the following values:

* 1-Year Receivable: €16,999,575.01
* Current EUR/USD Spot Exchange Rate: $1.1765
* Money Market - U.S. 1-Year Interest Rate (domestic): 3.670%
* Money Market - E.U. 1-Year Interest Rate (foreign): 3.691%
* Forwards - EUR/USD 1-Year Forward Exchange Rate: $1.0935

With those inputs, the model should produce the following values:

* 1[a]: $18,589,035.27
* 2[a]: €16,394,455.65
* 2[b]: $19,288,077.00
* 2[c]: $19,995,950.00

---

## Areas for Further Study & Improvement

1. AI Skills & Automation

In the current project scope, the hedging model relies on static, hardcoded variables, such as the fixed EUR/USD spot rate of $1.1765 and specific domestic/foreign interest rates. By integrating advanced AI tools with connected financial APIs, this process could be fully automated to pull live market data. Instead of manually updating the editable sections of the spreadsheet, an AI agent could fetch real-time exchange rates and yield curves, instantly recalculating the forward and money market hedge outcomes to provide more timely strategic recommendations for the firm.

Furthermore, AI-driven automation could elevate the project's static sensitivity analysis into dynamic Monte Carlo simulations. Rather than relying on a deterministic +/-5% linear sensitivity table, an AI tool could run thousands of randomized simulations based on historical EUR/USD volatility and macroeconomic indicators. This would provide a probabilistic distribution of potential outcomes for the unhedged, forward, and money market strategies. This offers the firm a much more robust and mathematically rigorous assessment of downside risk and upside potential.

2. GitHub & Version Control



3. Accounting & Audit Integration

The execution of the recommended money market hedge introduces specific financial reporting complexities, briefly noted in our executive justification. Integrating formal hedge accounting standards (mainly in compliance with International Financial Reporting Standards) is a critical step, as it dictates whether the gains and losses from the hedge are recorded immediately in our P&L or deferred. Proper alignment and documentation of the hedging instrument against the underlying receivable is required to avoid artificial earnings volatility during the 1-year horizon.

To qualify for these favorable hedge accounting treatments, strict documentation and ongoing proof of hedge effectiveness are mandatory. The structured logic of this project, combined with a version-control system like GitHub, can serve as audit evidence. Auditors can review the repository to access the exact sensitivity tables, scenario analyses, and comparative data used to justify the hedge, verifying that the strategic decision-making process was mathematically sound, compliant, and properly documented prior to the execution of any trades.

---
