
# Experiment Design
## Metric Choice
*List which metrics you will use as invariant metrics and evaluation metrics here. (These should be the same metrics you chose in the "Choosing Invariant Metrics" and "Choosing Evaluation Metrics" quizzes.)*

- **Invariant metrics**:
  - Number of cookies
  - Number of clicks
  - Click-through-probability

- **Evaluation metrics**:
  - Gross conversion
  - Retention
  - Net conversion

*For each metric, explain both why you did or did not use it as an invariant metric and why you did or did not use it as an evaluation metric. Also, state what results you will look for in your evaluation metrics in order to launch the experiment.*

#### Invariant Metrics

* **Number of cookies**: The number of cookies is a invariant metric, as it will happen before the user see the experiment due to page loading. This metric is a strong invariant metric and a weak evaluation metric because it measures how many cookies get to the course overview page before the experiment is presented to them. It is expected to be equally distributed between control and experiment groups and not have an effect on the experiment itself.

* **Number of user-ids**: The number of user-ids is neither a strong invariant metric nor a strong strong evaluation metric. This has todo with its dependence on the experiment itself, as well as an inability to control the amount between the control and experiment groups. This inability to control the amount between the two groups may skew results.

* **Number of clicks**: The number of clicks is the number of users that click the “Start Free-Trial” button, which happens before the experiment window is shown to the user. Since this metric is tracked before the experiment actually occurs, so it should not be used as an evaluation metric. The expectation is that the experiment and control groups will be equally distributed and should not affect the experiment itself.

* **Click-through-probability**: Click through probability is defined by dividing the number of unique cookies that click “Start Free-Trial” page by the number of unique cookies that view the course overview page. This is a good invariant metric because it is defined when the experience should be the same for all users and not affect the experiment. The expectation is that the experiment and control groups will be equally distributed and should not affect the experiment itself.

#### Evaluation Metrics


* **Gross conversion**: Gross conversion is not a good invariant metric, as the number of users who enroll in the free trial is dependent on the experiment. This metric is defined by the number of user-ids that checkout and enroll in the free trial divided by the number of unique cookies that click the “Start Free-Trial” button. Since this metric is measured after users have seen the experiment, it is directly affected by it, which makes it a strong evaluation metric and vice versa as an invariant metric. I would not expect the control and experiment groups for this metric to be evenly distributed.

* **Retention**: Retention is not a good invariant metric because the number of users who enroll in the free trial is again, dependent on the experiment. This metric is defined as the number of user-ids that stay enrolled passed the free-trial period divided by the number of cookies that clicked on the "Start Free-Trial" button. It is a strong evaluation metric, however based on the experiment duration needed for this metric, it was decided not to use it.

I calculated that the experiment would need to run for 119 days to match the amount of pageviews required for this metric (4,741,213 pageviews), which is very lengthy for this experiment and not the best option.

* **Net conversion**: Net conversion is not a good invariant metric because the number of users who enroll in the free trial is again, dependent on the experiment. This metric is defined by the number of user-ids that remained enrolled after the 14-day free-trial period divided by the number of cookies that click the “Start Free-Trial” button. Since this metric is correlated to the impact of the experiment being run, it is a strong evaluation metric.

In order to justify launching this experiment both gross conversion and net conversion will need to be satisfied. Gross conversion will need to decrease and net conversion will need to, at a minimum, stay level or increase. This will show that the number of users signing up for the free-trial is decreasing, but overall revenue is not negatively impacted by the experiment.

## Measuring Standard Deviation
*List the standard deviation of each of your evaluation metrics. (These should be the answers from the "Calculating standard deviation" quiz.)

For each of your evaluation metrics, indicate whether you think the analytic estimate would be comparable to the the empirical variability, or whether you expect them to be different (in which case it might be worth doing an empirical estimate if there is time). Briefly give your reasoning in each case.*

**Gross conversion** | 0.0202
**Net conversion** | 0.0156

Gross conversion and net conversion both have the number of cookies as their denominator, which is also our unit of diversion. We can therefore proceed using an analytical estimate of the variance.

I expect the analytic and empirical variability to be similar for both of the evaluation metrics selected. This is because analytical and empirical variability tend to be similar when the unit of diversion is the same as the unit of analysis. Both evaluation metrics I used have unique cookies as their unit of diversion and unit of analysis, thus their empirical and analytical variability should be similar.

## Sizing

### Number of Samples vs. Power
*Indicate whether you will use the Bonferroni correction during your analysis phase, and give the number of pageviews you will need to power you experiment appropriately. (These should be the answers from the "Calculating Number of Pageviews" quiz.)*

The Bonferroni correction was not used in this experiment. The evaluation metrics selected to proceed with are Gross conversion and Net conversion. As such, 685,324 page-views will be needed to power the experiment with the given metrics. This is double (control + experiment groups) the sample size required for the more demanding of the two metrics, Net conversion.


### Duration vs. Exposure
*Indicate what fraction of traffic you would divert to this experiment and, given this, how many days you would need to run the experiment. (These should be the answers from the "Choosing Duration and Exposure" quiz.)

Give your reasoning for the fraction you chose to divert. How risky do you think this experiment would be for Udacity?*

None of the participants could suffer physical harm as a result of the experiment, nor is sensitive data being collected, therefore a 100% exposure is a safe. Dividing total pageviews by the number of pageviews per day in the baseline (40,000), gives us a duration of 119 days were Udacity to divert it’s entire traffic. This is too long of an experiment and we should reduce the duration. We can exclude retention as an evaluation metric and consider the next limiting metric, net conversion. With a revised 685,275 necessary pageviews, it would then take 18 days to run the experiment.

# Experiment Analysis

The data for each group I used to calculate the information below can be in the table below.

Unique cookies to view page per day	| 40000
Unique cookies to click "Start free trial" per day	| 3200
Enrollments per day	| 660
Click-through-probability on "Start free trial" | 	0.08
Probability of enrolling, given click | 	0.20625
Probability of payment, given enroll | 	0.53
Probability of payment, given click	 | 0.1093125

## Sanity Checks
*For each of your invariant metrics, give the 95% confidence interval for the value you expect to observe, the actual observed value, and whether the metric passes your sanity check. (These should be the answers from the "Sanity Checks" quiz.)

For any sanity check that did not pass, explain your best guess as to what went wrong based on the day-by-day data. Do not proceed to the rest of the analysis unless all sanity checks pass.*

Evaluation Metric | 95% Confidence Interval | Observed | Result
----------------- | ----------------------- | -------- | ------
Number of cookies | [.4988, .5012] |  .5006 | PASS
Number of clicks on “Start free trial” | [.4959, .5041] | .5005 | PASS
Click-through-probability on “Start free trial”| [.0812, .0830] | .0822 | PASS

## Result Analysis

### Effect Size Tests
*For each of your evaluation metrics, give a 95% confidence interval around the difference between the experiment and control groups. Indicate whether each metric is statistically and practically significant. (These should be the answers from the "Effect Size Tests" quiz.)*

Evaluation Metric | Confidence Interval | Experiment | Result
----------------- | ------------------- | ---------- | ------
***Gross Conversion*** | [-.0291, -.0120] | statistically significant | practically significant
***Net Conversion*** | [-.0116, .0018] | not statistically significant | not practically significant

### Sign Tests
*For each of your evaluation metrics, do a sign test using the day-by-day data, and report the p-value of the sign test and whether the result is statistically significant. (These should be the answers from the "Sign Tests" quiz.)*

Evaluation Metric | p-value | Result
----------------- | ------- | ------
***Gross Conversion*** | .0026 | statistically significant
***Net Conversion*** | .6776 | not statistically significant


### Summary
*State whether you used the Bonferroni correction, and explain why or why not. If there are any discrepancies between the effect size hypothesis tests and the sign tests, describe the discrepancy and why you think it arose.*

The effect size tests determine that gross conversion is both statistically and practically significant, while net conversion is neither statistically or practically significant.

The Bonferroni correction was not utilized, as this experiment was only testing one , not multiple. The Bonferroni correction may be useful to apply if we decide to do post-test segmentation on the results, for example based on browser type, operating system, mobile, countries of origin, etc...

## Recommendation
*Make a recommendation and briefly describe your reasoning.*

Gross conversion turned out to be negative and practically significant. This is a good outcome because we lower our costs by discouraging trial signups that are unlikely to convert.

Net conversion unfortunately ended up being statistically and practically insignificant and the confidence interval includes negative numbers. This indicates a risk that putting the change into production could lead to a drop in conversions. It actually appears that the screener appears to increase the rate in which people leave the trial, it should be considered to test other designs of the screener before we decide whether to release the feature, or not launch the conception into production and change the site.


# Follow-Up Experiment
*Give a high-level description of the follow up experiment you would run, what your hypothesis would be, what metrics you would want to measure, what your unit of diversion would be, and your reasoning for these choices.*

## Pre-enrollment

A follow-up experiment that I would run would deal with students' pre-existing student characteristics.

There is a concept in higher education known as pre-entering characteristics. Essentially this boils down to student demographic and academic achievement information. There is a large body of research that shows how these pre-entering characteristics affect student success (SAT score, high school GPA, whether or not the students parents completed college, etc...).

A similar formula could be applied when student's are signing up for the 14-day trail period. For example, some of the other nanodegrees probably require more programming knowledge in order for a student to hit the ground running and not feel overwhelmed. Others may require a statistics background in, or at least the basic concepts before getting started. The idea being, the better we can align the students expectation for what the nanodegree will consist to empower them from the get go, the more likely they may be to maintain their enrollment after the 14 day trail. We could assess this through a brief survey before the student enrolls in the 14-day trial and have Udacity coach provide feedback. If the coach believes the student may need some additional knowledge they could recommend an introductory Udacity course the student should complete beforehand.

## Experiment Setup

***Design***: Users are either diverted into the experiment group, which completes the pre-requisites, or the control group, which is not filtered and enrolls in the free-trial normally.

***Null Hypothesis***: The additional pre-requisite measures will not increase the number of students that continue on past the free-trial period by the statistically significant difference defined.

***Unit of Diversion***: Similarly to how the original experiment was set up, the unit of diversion would be a unique cookie, and then user-id after a user enrolls in the free-trial period.

***Invariant Metrics***: These would be the same as the original experiment.

***Evaluation Metrics***: These would also be the same as the original experiment.
