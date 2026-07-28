# CashLag: Risk Analysis of Delayed Payments

## Project Background

This project is built on an accounts receivable dataset containing 2,466 invoices across 100 different customers. Out of those 2,466 invoices, 877 payments arrived after their due date — that's 35.6% of all payments coming in late, and it's putting real pressure on the company's cash flow.

This analysis was built to answer one core question: what is actually driving these late payments, and what can the company do to bring that number down.

---

[cover page photo]

---

The analysis is structured across two dashboard pages:

- **Risk Overview** — What is happening?
- **Root Cause & Recommendation** — Why is it happening, and what should we do about it?

| Resource | Link |
|---|---|
| Interactive Power BI Dashboard | [Download here] |
| SQL Analysis Report | [Download here] |
| Dataset (Dirty & Cleaned) | [Download here] |

[power bi dashboard gif]

---

## Data Structure & Initial Checks

The dataset includes fields like `DaysLate`, `Disputed`, `Region`, `InvoiceAmount`, and several others, spread across 2,466 invoices and multiple customers. Before any analysis began, the data was checked for formatting inconsistencies — the `Region` column in particular needed cleaning, since the same region was showing up under several different spellings and formats.

[data structure picture]

Both the dirty and cleaned versions of the dataset are available for download [here].

---

## Executive Summary

### Risk Overview — What Happened?

Out of 2,466 invoices, 877 came in late — that's 35.6% of all payments missing their due date, and it's a big enough share to genuinely affect the company's cash flow.

Region C turned out to be the slowest, with an average delay of 4.82 days, followed closely by Region B at just under 4 days. On the other end, Region A was the fastest by a clear margin.

In dollar terms, those 877 late invoices add up to $53.96K currently sitting overdue — money the company should already have in hand but doesn't.

Breaking the delays down by how long they dragged on: 28.5% of invoices were 1-15 days late, 6.7% were 16-30 days late, and only 0.3% (just 8 invoices) crossed 30+ days late. The remaining 64% of invoices were paid on time.

[risk overview page photo]

**Key Insights:**

- More than 1 in 3 payments miss their due date, and the majority of that delay is concentrated in the 1-15 day range rather than extreme, long-term delays — most of the problem is short-term slippage, not chronic non-payment
- Region C and Region B account for the bulk of the delay, while Region A performs more than twice as well as the slowest region
- $53.96K currently overdue represents real, avoidable pressure on working capital, not a one-time anomaly

---

### Root Cause & Recommendation

The most disputed bucket by far is the 30+ days late group — 87.50% of those invoices (7 out of 8) were tied to a dispute. The 16-30 day bucket followed the same pattern at 71.69% disputed. Looking at the chart, the trend is unmistakable: the longer a payment takes to settle, the higher the chance a dispute is behind it. In other words, if an invoice is running 16+ days late, dispute is very likely the main reason why.

The second factor worth calling out is billing method. Out of 2,466 invoices, Paper billing accounted for 1,263 and Electronic accounted for 1,203 — a nearly even split, which makes them directly comparable. Paper invoices were late 43.23% of the time, versus just 27.51% for Electronic. That gap makes sense — electronic invoices typically come with automatic reminders and notifications that keep the due date top of mind, while paper invoices don't have that safety net.

[root cause & recommendation page photo]

**Recommendation:**

If the company migrates its remaining paper-billed customers to electronic invoicing, and the late-payment rate for those invoices drops to match the electronic average, roughly **$12K** in currently overdue payments could be prevented going forward.

**Action Plan:**

- Fast-track dispute resolution — flag any invoice overdue by 15+ days immediately, since this is the point where dispute risk sharply increases
- Migrate remaining Paper-billing customers to Electronic invoicing
- Set up automated due-date reminders for all Electronic invoices
- Create a separate, priority collections queue specifically for disputed cases, since these are the ones most likely to turn into long-term delays

---

*Prepared by Yash Kumar*
