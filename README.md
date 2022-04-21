# Email Marketing Causal Analysis
Causal analysis of email marketing campaign. Used OLS regression, DoWhy & CausalML to calculate treatment effects.

## Problem Overview
In the area of marketing, email is a go-to method for promoting products. It is cheap, fast, and effective. Most marketers run an experiment to see whether or not their email-marketing works or not. In this domain, I analyzed whether or not emailing would affect our revenue (by observing the spending by each customer). We'll be looking at factors that can predict spending (in the next few weeks). During a period of two weeks following the e-mail campaign, results were tracked.  job is to tell the world if the Mens or Womens e-mail campaign was successful.

This dataset contains 64,000 customers who last purchased within twelve months. The customers were involved in an e-mail test.
- 1/3 were randomly chosen to receive an e-mail campaign featuring Mens merchandise
- 1/3 were randomly chosen to receive an e-mail campaign featuring Womens merchandise
- 1/3 were randomly chosen to not receive an e-mail campaign

![Marketing Experiment Overview](/emailmarketing_overview.jpg)
## Methodology
A number of techniques were tried to esimate the effect of marketing in Control vs other groups (**Average Treatment Effect**):

### Regression Analysis (using Propensity Estimates)
![Regression Summary](/ols_summary.png)

### DoWhy & Causal ML (XLearner, TLearner, SLearner, RLearner)
![CATE](/cate_estimate.png)

#### Feature Importances (Shapley) to predict customer spending
![Regression Summary](/featureimportance.png)
![Regression Summary](/interaction_featureimportance.png)

Also tried:
- Refutation of Estimate (Random Subset, Random Common Cause, Placebo Variable)
- Conditional & Individual Treatment Effects

## Conclusion
We run randomized experiments and do not observe any significant heterogeneity effects across the observed groups. This is validated by simple balancedness checks, heterogeneity checks, and uplift-modelling giving estimates that are close to the Average Treatment Effect.

**Results from Hypothesis Test:** Our initial findings showed that the available email-campaign data is close to a Randomized Controlled Trial, where there are no biases observed amongst the treatment and control groups. We find that there was a significant increase in average spending of the group who were sent emails regarding products for men compared to customers who were not sent emails. The conditional treatment effect is non-existent here. This is observed by using various Regressors (CausalML & DoWhy), where the treatment effect (after accounting for confounders) is close to the Average Treatment Effect.
