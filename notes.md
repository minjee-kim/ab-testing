## 1. What is A/B testing?

A/B testing is a randomized experiment used to compare two versions of a treatment, product, or experience.

- **A** usually represents the control or current version.
- **B** usually represents the treatment or new version.

A/B testing describes how the experiment is designed. Statistical methods such as proportion tests, t-tests, regression, or Bayesian methods can then be used to analyze the experimental results.

------------------------------------------------------------------------

## 2. Experimental unit

The **experimental unit** is the unit that is randomly assigned to a treatment.

Examples of experimental units can include users, accounts, devices, stores, or patients.

The unit of analysis should match the experimental design.

------------------------------------------------------------------------

## 3. Randomization

Randomization assigns experimental units to treatment groups by chance.

Its purpose is to make the treatment and control groups comparable on average and reduce confounding.

Randomization is what allows differences in outcomes between the groups to be interpreted causally.

------------------------------------------------------------------------

## 4. Treatment and control groups

The **control group** receives the current or standard condition.

The **treatment group** receives the new condition being evaluated.

The goal is to compare the outcomes of the two groups.

------------------------------------------------------------------------

## 5. Experiment metrics

A metric is an outcome used to evaluate the effect of the treatment.

### Primary metric

The main outcome used to evaluate whether the treatment was successful.

### Secondary metrics

Additional outcomes used to understand other effects of the treatment.

### Guardrail metrics

Outcomes used to make sure the treatment does not negatively affect another important aspect of the product or system.

------------------------------------------------------------------------

## 6. Treatment effect

The treatment effect measures the difference in outcomes between treatment and control.

In general,

$$\Delta = \text{Outcome}_B - \text{Outcome}_A$$

where $B$ is the treatment group and $A$ is the control group.

- $\Delta > 0$: the outcome is higher under treatment.
- $\Delta < 0$: the outcome is lower under treatment.
- $\Delta = 0$: there is no difference in the outcome.

------------------------------------------------------------------------

## 7. Binary outcomes

For a binary outcome, let

$$p_A = P(Y=1 \mid A)$$

and

$$p_B = P(Y=1 \mid B).$$

The treatment effect is

$$\Delta = p_B - p_A.$$

The estimated treatment effect is

$$\hat{\Delta} = \hat{p}_B - \hat{p}_A.$$

------------------------------------------------------------------------

## 8. Continuous outcomes

For a continuous outcome, let

$$\mu_A = E(Y \mid A)$$

and

$$\mu_B = E(Y \mid B).$$

The treatment effect is

$$\Delta = \mu_B - \mu_A.$$

The estimated treatment effect is

$$\hat{\Delta} = \bar{Y}_B - \bar{Y}_A.$$

------------------------------------------------------------------------

## 9. Absolute and relative effects

The **absolute effect** is the direct difference between the treatment and control outcomes:

$$\Delta = p_B - p_A.$$

The **relative effect** compares the difference with the control outcome:

$$\frac{p_B-p_A}{p_A}.$$

For proportions, the absolute effect is usually reported in **percentage points**, while the relative effect is usually reported as a **percent change**.

------------------------------------------------------------------------

## 10. Sampling variability

The observed treatment effect will vary from sample to sample because of random variation.

A **standard error** measures the expected sampling variability of an estimator.

For a difference between two independent proportions,

```math
SE(\hat{p}_B-\hat{p}_A)
=
\sqrt{
\frac{\hat{p}_A(1-\hat{p}_A)}{n_A}
+
\frac{\hat{p}_B(1-\hat{p}_B)}{n_B}
}
```

Larger sample sizes generally produce smaller standard errors.

------------------------------------------------------------------------

## 11. Confidence intervals

A confidence interval describes the uncertainty around an estimated treatment effect.

An approximate 95% confidence interval is

$$\hat{\Delta} \pm 1.96\,SE(\hat{\Delta}).$$

A confidence interval provides information about both the direction and plausible magnitude of the treatment effect.

------------------------------------------------------------------------

## 12. Hypothesis testing

A common null hypothesis in an A/B test is

$$H_0: \Delta = 0.$$

The alternative hypothesis is

$$H_A: \Delta \neq 0.$$

For a binary outcome,

$$H_0: p_B-p_A=0.$$

For a continuous outcome,

$$H_0: \mu_B-\mu_A=0.$$

------------------------------------------------------------------------

## 13. Test statistic

A test statistic compares the observed effect with the amount of variation expected under the null hypothesis.

In general,

``` math
\text{Test statistic}
=
\frac{\text{Observed effect} - \text{Effect under }H_0}
{\text{Standard error}}
```

A treatment effect that is large relative to its standard error provides stronger evidence against the null hypothesis.

------------------------------------------------------------------------

## 14. p-value

The p-value is the probability of observing a result at least as extreme as the observed result, assuming the null hypothesis is true.

A small p-value indicates that the observed result would be unusual under the null hypothesis.

A p-value is **not** the probability that the null hypothesis is true.

------------------------------------------------------------------------

## 15. Significance level

The significance level, denoted by $\alpha$, is the threshold chosen for rejecting the null hypothesis.

A common choice is

$$\alpha = 0.05.$$

If the p-value is less than $\alpha$, the result is called statistically significant.

------------------------------------------------------------------------

## 16. Two-sample proportion test

A two-sample proportion test is used when the outcome is binary and the goal is to compare two proportions.

The hypotheses are

$$H_0: p_A=p_B$$

versus

$$H_A: p_A\neq p_B.$$

This is commonly used for A/B test outcomes such as conversion or retention.

------------------------------------------------------------------------

## 17. Two-sample t-test

A two-sample t-test can be used to compare the means of a continuous outcome between treatment and control groups.

The hypotheses are

$$H_0: \mu_A=\mu_B$$

versus

$$H_A: \mu_A\neq\mu_B.$$

The Welch t-test does not require the two groups to have equal population variances.

------------------------------------------------------------------------

## 18. Type I and Type II errors

A **Type I error** occurs when the null hypothesis is rejected even though it is true.

$$P(\text{Type I error}) = \alpha.$$

A **Type II error** occurs when the null hypothesis is not rejected even though a real effect exists.

$$P(\text{Type II error}) = \beta.$$

------------------------------------------------------------------------

## 19. Statistical power

Power is the probability of detecting an effect when that effect truly exists.

$$\text{Power} = 1-\beta.$$

Power depends on:

- sample size
- effect size
- outcome variability
- significance level

------------------------------------------------------------------------

## 20. Minimum Detectable Effect

The **minimum detectable effect (MDE)** is the smallest treatment effect that an experiment is designed to detect with a specified level of power.

The MDE should reflect an effect size that is meaningful enough to matter.

------------------------------------------------------------------------

## 21. Sample size

Sample size should ideally be determined before running the experiment.

It depends on quantities such as:

- baseline outcome rate
- minimum detectable effect
- desired power
- significance level
- outcome variability

Larger samples allow smaller effects to be estimated more precisely.

------------------------------------------------------------------------

## 22. Statistical vs. practical significance

**Statistical significance** asks whether there is sufficient statistical evidence of a difference.

**Practical significance** asks whether the size of the difference is large enough to matter.

A statistically significant effect is not automatically an important effect.

------------------------------------------------------------------------

## 23. Experiment diagnostics

The experiment should be checked before interpreting the treatment effect.

Important checks include:

- correct treatment assignment
- missing observations
- duplicate experimental units
- expected treatment allocation
- data collection or logging problems

------------------------------------------------------------------------

## 24. Sample Ratio Mismatch

A **sample ratio mismatch (SRM)** occurs when the observed treatment allocation differs substantially from the allocation that was planned.

For example, an experiment designed for a 50/50 split should produce approximately equal treatment-group sizes.

A strong mismatch can indicate problems with randomization, eligibility, or data collection.

------------------------------------------------------------------------

## 25. Multiple testing

Testing many outcomes or subgroups increases the probability of finding a statistically significant result by chance.

Primary outcomes should therefore be defined before examining the results, and multiple-comparison procedures may be needed when many hypotheses are tested.

------------------------------------------------------------------------

## 26. Peeking and sequential testing

Repeatedly checking results and stopping an ordinary fixed-sample experiment when statistical significance is reached can increase the Type I error rate.

If results are monitored continuously, a statistical method designed for sequential testing should be used.

------------------------------------------------------------------------

## 27. Subgroup effects

The average treatment effect may differ across groups of experimental units.

Subgroup analyses can be used to investigate heterogeneous treatment effects, but they should be interpreted carefully because testing many subgroups increases the risk of false-positive findings.

------------------------------------------------------------------------

## 28. A/B testing workflow

A basic A/B testing workflow is:

1.  Define the research question.
2.  Define the experimental unit.
3.  Define treatment and control.
4.  Choose the primary and secondary metrics.
5.  Define the treatment effect.
6.  Choose the significance level, power, and minimum detectable effect.
7.  Determine the required sample size.
8.  Randomize experimental units.
9.  Collect and check the data.
10. Estimate the treatment effect.
11. Calculate uncertainty using a standard error and confidence interval.
12. Conduct the statistical test.
13. Interpret statistical and practical significance.
14. Make a decision based on the experimental evidence.
