# Receivable Hedging – Technical Specification

**Created by:** Michael Ballesteros  
**Updated by:** Michael Ballesteros  
**Date Created:** 4/21/26    
**Date Updated:** 4/21/26      
**Version:** 2.0    
**LLM Used:** Gemini  

**To:** Chief Financial Officer  
**From:** Financial Risk Management   

**Purpose:** Provide a detailed specification outlining a replicable model for evaluating FX hedging alternatives.

---

## 1. Problem Statement

This document outlines a model used to evaluate FX risk management strategies for our Euro-denominated receivable, valued at a $20,000,000 USD baseline, due in one year. Because our functional currency is the US Dollar, this unhedged cash flow exposes our projected revenue to volatility in the EUR/USD exchange rate. To manage this risk, we will be analyzing forward and money market hedges for the receivable, modeling such strategies under various spot rates, and classifying what stragies are the most sensible relative to varying sensitivity levels and other criteria. 

---

## 2. Inputs

Known variables that serve as the model's foundation:

| Variable | Description | Unit | Example | Source |
|-----------|-------------|------|----------|--------|
| `FC_AMT` | Foreign-currency receivable | EUR | 16,999,575.01 | Company data |
| `S₀` | Current EUR/USD spot rate | USD/EUR | [Look up] | Market data (Bloomberg) |
| `F₀` | 1-year EUR/USD forward rate | USD/EUR | 1.0935 | Provided |
| `r_USD` | USD 1-year interest rate | % | [Look up] | Market data (Secured Overnight Financing Rate) |
| `r_EUR` | EUR 1-year interest rate | % | [Look up] | Market data (Euro Interbank Offered Rate) |
| `t` | Time to maturity | Years | 1 | Derived |

---

## 3. Assumptions & Constraints

The hedging model assumes the following:  

  1. Interest rates are quoted on a simple annual basis, obtained from the aforementioned sources on 4/17/26 at 5:00 PM EDT.  
  2. Forward rate provided represents a 1-year maturity.
  3. Exchange rates expressed as USD per EUR. 
  4. The model assumes zero broker fees, bank commissions, or execution costs.			  
  5. The model assumes the firm can transact exactly at the quoted spot (1.1781) and forward (1.0935) rates with no bid-ask spread.			  
  6. The model applies a single foreign interest rate (3.691%) and domestic interest rate (3.670%) with no spread.			  
  7. The model calculates gross cash flows and ignores any tax implications regarding FX gains/losses, interest expenses on the Euro loan, or interest income on the USD deposit.  
  
---

## 4. Calculation Flow  


  1. Calculate USD proceeds under the forward hedge using the provided forward rate.  
  2. Calculate USD proceeds under a synthetic forward hedge using money market rates.  
  3. Compare results across hedges at the base case and across various sensitivities of EUR appreciation/depreciation.  
  4. Summarize hedging trade-offs regarding certainty, credit requirements, upside potential, and other criteria.  

---

## 5. Outputs

Expected results from the model:  

| Output | Description | Format | Purpose |
|---------|--------------|---------|----------|
| `USD_forward` | USD proceeds from forward hedge | Numeric | Certainty benchmark |
| `USD_mm` | USD proceeds from money market hedge | Numeric | Cross-check against forward |
| `Table` | Hedge outcomes vs. EUR/USD sensitivity | Heatmap | Visual comparison |
| `Summary` | Written conclusion | 1-2 paragraphs | Executive-ready takeaway |

---

## 6. Sensitivity Plan

To test our strategies against FX fluctuations, the table of hedging outcomes is organized under various EUR/USD spot rates. These rates are separated by incruments of $0.01, and each hedging strategy's proceeds are computed under all levels. The table lists the results as raw returns and raw profit/loss versus an unhedged scenario. For each level of sensitivity, the more profitable strategy is deemed a "winner". The table's organization allows the firm to analyze what strategies would be the most sensible under scenarios where our receivable's foreign denomination appreciates or depreciates.  

---

## 7. Limitations & Next Steps

The model's complete accuracy is limited by the following:   

  1. The money market hedge assumes the firm has immediate, unrestricted access to a €16.37M line of credit at the stated interest rate.
  2. The model assumes the 1-year forward rate 0f 1.0935 is a fixed market quote. However, based on the spot rate (1.1770) and the narrow interest rate differential (3.670% U.S. vs. 3.691% E.U.), this forward rate violates Covered Interest Rate Parity and creates an arbitrage opportunity.			    

  The next phase of our decision-making process will involve constructing an Excel model implementing this logic to quantify results under each hedge structure. The model will be built off the specifications in this document, as well as direct prompting that can be replicated across various AI large language models. The finished framework can be applied to foreign receivables the firm collects in the future.

---
