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
	- If the probability of getting a particular sample mean is less than $\alpha$, it is  


### 10. t-test

### 11. One-Way ANOVA

### 12. Correlation

### 13. Regression

### 14. Chi-Sqaured test
