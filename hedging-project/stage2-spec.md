# Receivable Hedging – Technical Specification

**Created by:** Michael Ballesteros  
**Updated by:** Michael Ballesteros  
**Date Created:** 4/21/26    
**Date Updated:** 4/21/26      
**Version:** 2.0    
**LLM Used:** Gemini  

**Role:** Financial Analyst  
**Audience:** Chief Financial Officer  

**Purpose:** Provide a professional, quantitative specification outlining the analytical structure for evaluating FX hedging alternatives.

---

## 1. Problem Statement

This document outlines a risk management methodology for our Euro-denominated receivable, valued at a $20,000,000 USD baseline, due in one year. Because our functional currency is the US Dollar, this unhedged cash flow exposes our projected revenue to volatility in the EUR/USD exchange rate. To manage this risk, we will be analyzing various hedging strategies for the receivable, modeling such strategies under various levels of volatility, and using AI to reconstruct our model and provide recommendations for the firm.

Include:
- Exposure type (receivable or payable)  
- Foreign currency amount and time horizon  
- Objective (e.g., protect USD value, preserve upside)  
- Decision context (corporate treasury or business unit)

> *A strong statement demonstrates clear understanding of both financial context and business implications.*

---

## 2. Inputs (Known Variables)

Create a clean, professional input table. This will become the foundation for your spreadsheet and future AI prompts.

| Variable | Description | Unit | Example | Source |
|-----------|-------------|------|----------|--------|
| `FC_AMT` | Foreign-currency receivable | EUR | 1,200,000 | Company data |
| `S₀` | Current EURUSD spot rate | USD/EUR | [Look up] | Market data |
| `F₀` | 1-year EURUSD forward rate | USD/EUR | 1.0890 | Provided |
| `r_USD` | USD 1-year interest rate | % | [Look up] | Market data |
| `r_EUR` | EUR 1-year interest rate | % | [Look up] | Market data |
| `t` | Time to maturity | Years | 1 | Derived |
| `K_put` | EUR Put strike | USD/EUR | [Set at spot] | Analyst choice |
| `K_call` | EUR Call strike | USD/EUR | [Set at spot] | Analyst choice |
| `Premium_put` | Put premium | USD per contract | 0.017 | Scenario |
| `Premium_call` | Call premium | USD per contract | 0.022 | Scenario |

> *Tip:* Keep labels short and standardized. Think like a financial modeler — these names should become variable names, spreadsheet inputs, or prompt parameters later.

---

## 3. Assumptions & Constraints

The hedging model accounts for the following:  

  1. The model assumes zero broker fees, bank commissions, or execution costs.			  
  2. The model assumes the firm can transact exactly at the quoted spot (1.1781) and forward (1.0935) rates with no bid-ask spread.			  
  3. The model applies a single foreign interest rate (3.691%) and domestic interest rate (3.670%) with no spread.			  
  4. The Money Market hedge assumes the firm has immediate, unrestricted access to a €16.37M line of credit at the stated interest rate.			  
  5. The model calculates gross cash flows and ignores any tax implications regarding foreign exchange gains/losses, interest expenses on the Euro loan, or interest income on the USD deposit.  
  6. The model assumes the 1-Year Forward Rate 0f 1.0935 is a fixed market quote. However, based on the spot rate (1.1770) and the narrow interest rate differential (3.670% U.S. vs. 3.691% E.U.), this forward rate violates Covered Interest Rate Parity and creates an arbitrage opportunity.			  

---

## 4. Calculation Flow

Forward Hedging: This strategy locks in the future domestic value of the receivable using a forward contract.  
  1. q

Money Market Hedging: This strategy uses current spot markets and money markets to synthetically lock in a future exchange rate.  
  1. q

---

## 5. Outputs

List expected results from the model. These become your **spreadsheet outputs**, **AI prompt targets**, and **Stage 5 discussion points**.

| Output | Description | Format | Purpose |
|---------|--------------|---------|----------|
| `USD_forward` | USD proceeds from forward hedge | Numeric | Certainty benchmark |
| `USD_mm` | USD proceeds from money market hedge | Numeric | Cross-check against forward |
| `USD_put` | USD proceeds from EUR put hedge | Table | Sensitivity & protection |
| `USD_call` | USD proceeds from EUR call hedge | Table | Optional upside case |
| `Chart_1` | Hedge outcomes vs. S_T | Line chart | Visual comparison |
| `Summary` | Written conclusion | 1–2 paragraphs | Executive-ready takeaway |

> *Outputs should read like a professional financial dashboard — clear, repeatable, and decision-focused.*

---

## 6. Sensitivity Plan

Define how you will test and visualize FX outcomes.

Example:
> Vary EURUSD spot at maturity \(S_T\) from 0.95×S₀ to 1.05×S₀ in increments of 0.01.  
> For each value, compute USD proceeds under all hedge strategies.  
> Present results as a comparison table and line chart.

---

## 7. Limitations & Next Steps

Briefly note any analytical limits (e.g., volatility ignored, credit risk excluded) and outline your immediate next step (e.g., model build in Stage 3).

Example phrasing:
> This specification does not incorporate implied volatility or transaction costs. The next phase will involve constructing an Excel model implementing this logic to quantify results under each hedge structure.

---

# 🧭 Writing a Strong Specification

**Your spec should:**
- **Communicate like a professional:** clear, structured, and jargon-free.  
- **Think one stage ahead:** your spec should feed directly into your Excel build or AI prompt.  
- **Be internally consistent:** variables, labels, and steps must align.  
- **Be reproducible:** a new analyst should be able to implement your plan without your help.  
- **Be executive-relevant:** the CFO should understand *what you’re doing* and *why it matters*.

---

## 🔗 How This Sets You Up for Later Stages

| Stage | What This Spec Enables |
|-------|------------------------|
| **Stage 2** | Each “Input” and “Output” becomes a spreadsheet cell or named range. |
| **Stage 3** | Your spec documents what you built and articulates an improved design. |
| **Stage 4** | Your “Calculation Flow” becomes an AI prompt instruction block; your “Outputs” drive the interpretation and recommendation. |

> *Treat your specification as the bridge between business insight and technical execution — the CFO should be confident your plan is sound even before seeing the numbers.*
