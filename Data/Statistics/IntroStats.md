# Introduction to Statistics @ Udacity

### 1. Intro to Research Methods

* Constructs & Operational defination
	- A construct is a variable that is not directly observable or measurable
	- Example (Operational defination): Intelligence (IQ test), Effort (minutes donging homework, grades, GPA), Age (age in years, wisdom), Hunger (how often tummy grumbles), Itchiness
	- Counterexample: Gallons of gasoline, Annual salary in USD


* Lurking variables
	- Extraneous factors, need to be controlled


* Sampling error 

	![sampling_error](imgs/IntroStats_1_1.png)


* Correlation & Causation
	- Correlation does **NOT** prove causation
	- Observational studies, Surveys => show relationships
	- Controlled experiment => show causation



### 2. Visualization Data

* Table:
	- Frequency, Relative frequence, Propotion, Percent


* Histogram
	- bin size


* Histogram & Bar graph
	- Histogram: x-axis: numberical/quantitative
	- Bar graph: x-axis: categorical/qualitiative 


* Biased graphs
	
	![biased_graphs](imgs/IntroStats_2_1.png)



### 3. Central Tendency

* Mode
	- The value at which frequency is highest
	- Uniform distribution has NO mode
	- Mode can be used to descibe any type of data, numerical or categorical
	- Not all scores in the dataset affect the mode
	- If we take a lot of samples from the same population, the mode will NOT be  the same in each sample
	
 
* Median
	- Value in the middle, the average of the two middle numbers when data size is even
	- Not affected by outliers 
	

* Mean
	- Average
	- All score in the distribution affect the mean
	- Many samples from the same population will have similar means
	- The mean of a sample can be used to make inferences about the population it came from
	- Mean with outlier

	![mean_with_outlier](imgs/IntroStats_3_1.png)


* Measure of Center

	![distribution_1](imgs/IntroStats_3_2.png)

	![distribution_2](imgs/IntroStats_3_3.png)

	![meansure_of_center](imgs/IntroStats_3_4.png)



### 4. Variability

* Range
	- Range = Max - Min


* IQR
	- Inter-Quartile Range
	- IQR = Q3 - Q1

	![IQR](imgs/IntroStats_4_1.png)

	- About 50% of the data falls within the IQR
	- The IQR is not affected by every value in the dataset
	- The IQR is not affected by outliers 


* Outlier
	- Outlier < (Q1 - 1.5 * IQR) ... (Q3 + 1.5 * IQR) < Outlier


* Boxplots

	![Boxplots](imgs/IntroStats_4_2.png)	


* Measeure variability
	- Average deviation is 0
	- Absolute deviation
	- Variance: average squared deviation
	- Standard deviation: square root of Variance


* Sample standard deviation & Bessels correction

	![sample_standard_deviation](imgs/IntroStats_4_3.png)



### 5. Standardizing

* Relative Frequency Distribution
	- Concerned  with the propotion less than or greater than a certain value on a distribution
	
	![relative_frequency_distribution](imgs/IntroStats_5_1.png)


* Continuous Distribution

	![continuous_distribution_1](imgs/IntroStats_5_2.png)

	![continuous_distribution_2](imgs/IntroStats_5_3.png)


* Theoretical Normal Distribution
	
	![normal_distribution_1](imgs/IntroStats_5_4.png)


* Standard Normal Distribution
	
	![normal_distribution_2](imgs/IntroStats_5_5.png)

	
* Z-score
	- Number of standard deviations away from the mean
	
	![z-score_1](imgs/IntroStats_5_6.png)

	![z-score_2](imgs/IntroStats_5_7.png)


### 6. Normal Distribution

* PDF: Probability Distribution Function

	![PDF_1](imgs/IntroStats_6_1.png)


* Z-table



### 7. Sampling Distribution

* Sample Mean Distribution
	- Sampling distribution => distribution of sample means
	- Sampling distribution is normal distribution


* Central Limit Theorem
	
	![Central_Limit_Theorem_1](imgs/IntroStats_7_1.png)

	![Central_Limit_Theorem_2](imgs/IntroStats_7_2.png)

	![standard_err](imgs/IntroStats_7_3.png)

	

### 8. Estimation

* Point estimate

	![point_estimate](imgs/IntroStats_8_1.png)


* Margin of error, Confidence Interval

	![margin_of_error_1](imgs/IntroStats_8_2.png)

	![margin_of_error_2](imgs/IntroStats_8_3.png)


* Critical values of z

	![z_critical_value](imgs/IntroStats_8_4.png)

	![95_confidence_interval](imgs/IntroStats_8_5.png)

	![98_confidence_interval](imgs/IntroStats_8_6.png)


### 9. Hypothesis Testing

* Alpha levels
	- levels of likelihood
	- .05 (5%), .001 (1%), .001(0.1%)
	- If the probability of getting a particular sample mean is less than alpha, it is unlikely to occur

	
* Critical regions

	![critical_regions](imgs/IntroStats_9_1.png)

	
* One-tailed vs. two-tailed test

	![tailed_test](imgs/IntroStats_9_2.png)


* Hypothesis
	- Null hypothesis
	- Alternative hypothesis

	![hypothesis](imgs/IntroStats_9_3.png)

	![reject_null_hypothesis](imgs/IntroStats_9_4.png)


* Decision errors
	
	![decision_errors](imgs/IntroStats_9_5.png)



### 10. t-test I II

* z-test
	- z-test works when we know population mean and population standard deviation


* t-test
	- how different a sample mean is from a population
	- how different two sample means are from each other
		- dependent
		- independent
	

* t-distribution

	![t-distribution](imgs/IntroStats_10_2.png)


* Degree of Freedom
	- df = n -1

	
* t-table

	![t-table](imgs/IntroStats_10_3.png)
	

* t-statistics

	![t-statistics](imgs/IntroStats_10_4.png)


* One-sample t-test

	![one_sample_t-test](imgs/IntroStats_10_5.png)


* p-value

	![p-value](imgs/IntroStats_10_6.png)


* Cohen's d

	![cohens_d](imgs/IntroStats_10_7.png)


* Dependent samples

	![dependent_samples](imgs/IntroStats_10_8.png)

	![dependent_t_test](imgs/IntroStats_10_9.png)

	![t_confident_interval](imgs/IntroStats_10_10.png)


* Types of Design
	
	![types_of_design](imgs/IntroStats_10_11.png)


* Results sections
	1. Descriptive statistics
		- Mean, Stardard Deviation, etc.
		- in text, in graphs, in tables
	2. Inferential statistics
		- hypothesis test
			- kind of test, e.g. one-sample t-test
			- test statistic
			- degree of freedom
			- p-value
			- direction of test
			- confidence interval on the mean difference
		- APA style
	3. Effect size measures
	
	![APA_test_statistics](imgs/IntroStats_10_12.png)

	![APA_confidence_interval](imgs/IntroStats_10_13.png)	

	![APA_effect_size](imgs/IntroStats_10_14.png)



### 11. t-test III

* Dependent vs. Independent Samples

	![dependent_independent_samples](imgs/IntroStats_11_1.png)


* Independent samples t-test

	![independent_t-test](imgs/IntroStats_11_2.png)

	![independent_t-test_example](imgs/IntroStats_11_3.png)


* Pooled Variance

	![pooled_variance](imgs/IntroStats_11_4.png)


* t-Test Assumptions

	![t-test_assumptions](imgs/IntroStats_11_5.png)



### 12. One-Way ANOVA

* Grand mean

	![grand_mean](imgs/IntroStats_12_1.png)


* Between-group variability, Within-group variability

	![group_variability](imgs/IntroStats_12_2.png)


* ANOVA
	- Analysis of Variance
	- One-Way ANOVA: one independent variable


* Hypothesis

	![ANOVA_hypothesis](imgs/IntroStats_12_3.png)

	![ANOVA_hypothesis_example](imgs/IntroStats_12_4.png)

	
* F-statistic

	![F-ratio](imgs/IntroStats_12_5.png)
	
	![ANOVA_example](imgs/IntroStats_12_6.png)



### 13. ANOVA, Continued

* Multiple Comparison Test

	![multiple_comparison_test](imgs/IntroStats_13_1.png)
	

* Tukey's HSD

	![tukeys_hsd](imgs/IntroStats_13_2.png)


* Cohen's d for multiple comparison

	![cohens_d](imgs/IntroStats_13_3.png)


* Explained variation

	![explained_variation](imgs/IntroStats_13_4.png)


* Reporting results of ANOVA

	![reporting_results](imgs/IntroStats_13_5.png)


* POWER

	![POWER_1](imgs/IntroStats_13_6.png)

	![POWER_2](imgs/IntroStats_13_7.png)


* ANOVA assumption

	![ANOVA_assumption](imgs/IntroStats_13_8.png)


* Summary

	![ANOVA_summary_1](imgs/IntroStats_13_9.png)

	![ANOVA_summary_2](imgs/IntroStats_13_10.png)



### 14. Correlation

* Two variables

	![two_variables](imgs/IntroStats_14_1.png)


* Scatterplot

	![scatterplot](imgs/IntroStats_14_2.png)


* Strength & Direction
	
	![strength_direction](imgs/IntroStats_14_3.png)


* Correlation Coefficient

	![correlation_coefficient](imgs/IntroStats_14_4.png)


* Hypothesis testing

	![hypothesis_testing_1](imgs/IntroStats_14_5.png)

	![hypothesis_testing_2](imgs/IntroStats_14_6.png)

	
* Confidence Interval, p_value

	![confidence_interval](imgs/IntroStats_14_7.png)


* Outlier
	- r is sensitive to  outliers

	![outlier](imgs/IntroStats_14_8.png)



### 15. Regression

* Linear Regression
	- The line of best fit

	![linear_regression](imgs/IntroStats_15_1.png)	


* Observed data, Expected data, residual

	![residual](imgs/IntroStats_15_2.png)


* Regression equation

	![regression_equation_1](imgs/IntroStats_15_3.png)

	![regression_equation_2](imgs/IntroStats_15_4.png)

	![regression_equation_3](imgs/IntroStats_15_5.png)


* Standard Error of Estimate

	![standard_error_of_estimate](imgs/IntroStats_15_6.png)


* Confidence intervals

	![confidence_intervals](imgs/IntroStats_15_7.png)


* Hypothesis testing for slope

	![t-test_for_slope](imgs/IntroStats_15_8.png)


* Outlier
	- factors that affect simple linear regression

	![outlier](imgs/IntroStats_15_9.png)
	

* Summary of Linear regression

	![summary](imgs/IntroStats_15_10.png)


* Multiple regression

	![multiple_regression](imgs/IntroStats_15_11.png)



### 16. Chi-Sqaured test
