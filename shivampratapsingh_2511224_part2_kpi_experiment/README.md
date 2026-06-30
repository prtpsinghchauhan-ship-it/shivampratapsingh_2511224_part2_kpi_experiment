# Business Experiment: Onboarding & Activation Campaign Analysis

## 1. Business Context
The company tested a new onboarding and activation campaign to improve user conversion. This project analyzes whether the treatment group (new experience) outperforms the control group (existing experience) based on conversion rates, engagement metrics, and risk-monitoring guardrails.

## 2. Dataset Description
The analysis utilizes `campaign_experiment_data.xlsx`, containing user-level data including sign-up dates, group assignments, demographic segments (Region, Device, Traffic Source), and key behavioral metrics.

## 3. North Star Metric
**Paid Conversion Rate**
* **Why:** This metric represents the transition from a free user to a paying customer, directly mapping to the primary business objective of increasing subscription revenue.
* **Why others are secondary:** Metrics like "Onboarding Completion" are necessary steps, but "Conversion" is the realized outcome.
* **Blind Optimization Risk:** Optimizing for conversion alone without guardrails can lead to aggressive/misleading onboarding flows, resulting in a spike in support tickets and refunds.

## 4. KPI Tree Summary

* **North Star:** Paid Conversion Rate
* **Primary Drivers:** User Interest (Landing Page visits, Trial starts), Activation (Onboarding Completion), Revenue Quality (ARPU).
* **Guardrail Metrics:** Refund Rate, Support Ticket Rate.

## 5. Experiment Analysis Approach
Data was processed in `experiment_analysis.xlsx`:
* **Validation:** Cleaned for missing values, duplicates, and invalid binary flags.
* **Summary:** Aggregated results using Pivot Tables, comparing Control vs. Treatment performance.
* **Segments:** Analyzed performance across Device Type, Region, and Traffic Source to identify performance variances.

## 6. Hypothesis Test Summary
* **Null Hypothesis ($H_0$):** $p_{treatment} \le p_{control}$
* **Alternate Hypothesis ($H_1$):** $p_{treatment} > p_{control}$
* **Statistical Test:** One-tailed Two-Proportion Z-Test ($\alpha = 0.05$).
* **Results:** P-value = **0.000573**.
* **Interpretation:** We reject the null hypothesis; the conversion lift is statistically significant.

## 7. Guardrail Metrics Considered
* **Refund Rate:** Monitored to identify user frustration or "bait-and-switch" experiences.
* **Support Ticket Rate:** Monitored to identify UI/UX friction points in the new onboarding flow.


## 8. Final Recommendation
**Recommendation: Launch only for the Desktop segment.**
While the Treatment group achieved statistically significant conversion lift globally, the **Mobile** segment showed severe degradation in guardrail metrics (Refund and Support Ticket rates). We recommend rolling out the treatment to 100% of **Desktop** users while rolling back to the Control experience for **Mobile** users to conduct further UX audits.

## 9. Assumptions and Limitations
* Assumes randomized user assignment.
* Analysis window is restricted to 30 days, which may not capture long-term retention effects.

## 10. Screenshots
* **Summary Metrics:** `screenshots/summary_metrics.png`
* **Hypothesis Output:** `screenshots/hypothesis_test_output.png`
* **KPI Tree Preview:** `screenshots/kpi_tree_preview.png`