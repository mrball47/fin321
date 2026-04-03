# Memo - Hedging Decision

**Created by:** Michael Ballesteros  
**Updated by:** Michael Ballesteros  
**Date Created:** April 2, 2026  
**Date Updated:** April 3, 2026  
**Version:** 2.0  
**LLM Used:** Gemini

**TO:** Chief Financial Officer  
**FROM:** Financial Risk Management  
**DATE:** April 3, 2026  
**SUBJECT:** FX Exposure on European Receivable and Proposed Hedging Strategies  

---  
  
This memo outlines a risk management methodology for our Euro-denominated receivable, valued at a $20,000,000 USD baseline, due in one year. Because our functional currency is the US Dollar, this unhedged cash flow exposes our projected revenue to volatility in the EUR/USD exchange rate. To manage this risk, we will be analyzing various hedging strategies for the receivable, modeling such strategies under various levels of volatility, and using AI to reconstruct our model and provide recommendations for the firm.

Over a 1-year horizon, the EUR/USD exchange rate is susceptible to macroeconomic volatility driven by changes in central bank interest rates, shifting inflation data, and geopolitical uncertainty. If the Euro weakens before the settlement date, the converted USD equivalent of our revenue will decline. 

Securing such risk will accomplish the following objectives:
  * Protect the USD value of this receivable against adverse currency movements. 
  * Balance our downside protection with heding costs (minimizing upfront cash requirements in option premiums, or avoiding unnecessary strain the firm's balance sheets and credit lines).
  * Establish a framework for evaluating future international receivables and mitigating FX risk across the firm.

To mitigate this currency risk, we are evaluating three hedging strategies:

* **Forward Contracts:** Lock in a guaranteed exchange rate today (currently quoted at 1.0935).

  * **Pros:** Provides complete certainty for future USD cash flows with zero upfront cash cost. 
  * **Cons:** Eliminates any upside profit potential if the Euro appreciates.

* **Options Contracts:** Purchase a put option on the Euro, granting us the right to sell them at a fixed strike rate.

  * **Pros:** Establishes a firm floor against Euro depreciation while capturing potential upside if the Euro strengthens.
  * **Cons:** Requires an immediate premium payment ($0.019 per contract).

* **Money Market Hedge:** Borrow against the expected Euro receivable today, convert the funds to USD at the current spot rate, and use the incoming Euro payment to retire the debt next year.

  * **Pros:** Locks in a known USD value today and provides immediate liquidity for operations.
  * **Cons:** Consumes existing balance sheet capacity and ties up corporate credit lines.

To determine the optimal solution, we will execute the following sequence:

  **1. Excel Model Build:** Build a working spreadsheet computing forward, options, and money market hedge outcomes under various sensitivities in EUR/USD (±5%).

  **2. Technical Specifications:** Document the model's development, and design a framework precise enough for an another analyst of AI to reconstruct for other international receivables. 

  **3. Final Analysis & AI Prompt:** Interpret our results, and write a structured AI prompt to regenerate our model and deliver executive-ready recommendations.

---

**References**    
  Eun, C., Resnick, B., & Chuluun, T. (2024). *International Financial Management* (10th ed.). McGraw-Hill Education. 
