# Machine Learning by NG

### 1. Introduction

* Machine Learing
	- Grew out of work in AI
	- New capability for computers


* Examples:
	- Database mining
		- large datasets from growth of automation/web
		- E.g., Web click data, medical records, biology, engineering
	- Application can't program by hand
		- E.g., Autonomous helicopter, handwriting recignition, Natural Language Processing(NLP), Computer Vision
	- Self-customizing programs
		- E.g., Amazon, Netflix product recommendations
	- Understanding hunman learning(brain, real AI) 


* Machine Learning definition
	- Arthur Samuel (1959). Machine Learning: Field of study that gives computers the ability to learn without being explicitly programmed.
	- Tom Mitchell (1998). Well-posed Learning Problem: A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E.
	- E.g.
		- T: classifying emails as spam or not
		- E: watching you label emails as spam or not
		- P: the number of fraction of emails correctly classified as spam/not spam


* Machine learning algorithms
	- Supervised learning
	- Unsupervised learning
	- Others: reinforcement learning, recommender systems


* Supervised learning
	- "right answers" given
	- Regression: predict **continuous** valued output; e.g., housing price prediction
	- Classification: predict **discrete** valued output (0 or 1); e.g., cancer detection: malignant or benign


* Unsupervised learning
	- Clustering


### 2. Linear Regression with One Variable

* Model representation

	![Housing_Prices](imgs/mlng_2_1.png)

	![Training_set_data](imgs/mlng_2_2.png)

	![Machine_learning_model](imgs/mlng_2_3.png)


* Cost function

	![regression_equations_1](imgs/mlng_2_4.png)
	
	![cost_function_illustration_1](imgs/mlng_2_5.png)

	![cost_function_illustration_2](imgs/mlng_2_6.png)


* Gradient descent

	![Gradient_descent_outline](imgs/mlng_2_7.png)

	![Gradient_descent_illustration](imgs/mlng_2_8.png)

	![Gradient_descent_algorighm_1](imgs/mlng_2_9.png)
	
	![Gradient_descent_algorighm_2](imgs/mlng_2_10.png)


* Learning rate

	![Learning_rate](imgs/mlng_2_11.png)

	- Gradient descent can converge to a local minimum, even with the learning rate fixed


### 3. Linear Algebra Review

...


### 4. Linear Regression with Multiple Variables 

##### Multiple Variables

* Gradient descent for multiple variables

	![Linear_regression_multi-feature](imgs/mlng_4_1.png)


##### Gradient descent in practice

* Feature scaling

	![feature_scaling](imgs/mlng_4_2.png)

	- get every feature into approximately a [-1, 1] range

	- Mean normalization
	
	![mean_normalization](imgs/mlng_4_3.png)
	

* Learning rate: making sure gradient desent is working correctly

	![plots_for_learning_rate](imgs/mlng_4_4.png)

	![gradient_descent_not_working](imgs/mlng_4_5.png)
	
	![learning_rate_summary](imgs/mlng_4_6.png)
	

* Features and polynomial regression
	
	![polynomial_regression](imgs/mlng_4_7.png)


##### Normal equation

* Normal equation
	
	![normal_equation](imgs/mlng_4_10.png)


* Intuition
	
	![intuition_of_normal_equation](imgs/mlng_4_8.png)


* Compared with gradient descent

	![normal_equation_vs_gradient_descent](imgs/mlng_4_9.png)
	
	
### 5. Octave Turorial

...


### 6. Logistic Regression

* Hypothesis representation

	![logistic_regression_model](imgs/mlng_6_1.png)

	![interpretation_of_hypothesis](imgs/mlng_6_2.png)

	
* Decision boundary

	![decision_boundary](imgs/mlng_6_3.png)

	![non-linear_decision_boundary](imgs/mlng_6_4.png)


* Cost function

	![logistic_regression](imgs/mlng_6_5.png)

	![cost_function_1](imgs/mlng_6_6.png)

	![cost_function_2](imgs/mlng_6_7.png)

	![cost_function_3](imgs/mlng_6_8.png)


* Gradient descent

	![gradient_descent](imgs/mlng_6_9.png)
	

* Optimization algorithm

	![optimization_algorithm](imgs/mlng_6_10.png)


* Multi-class classification
	
	![multi-class_classification](imgs/mlng_6_11.png)
	
	![multi-class_classification](imgs/mlng_6_12.png)


### 7. Regularization

* The problem of overfitting

	![linear_regression_overfitting](imgs/mlng_7_1.png)

	![logistic_regression_overfitting](imgs/mlng_7_2.png)


* Addressing overfitting

	![addressing_overfitting_options](imgs/mlng_7_3.png)

	



### 8. Neural Networks: Representation


### 9. Nural Networks: Learning


### 10. Advice for Applying Machine Learning


### 11. Machine Learning System Design


### 12. Support Vector Machines


### 13. Clustering


### 14. Dimensionality Reduction


### 15. Anomaly Detection


### 16. Recommender Systems


### 17. Large Scale Machine Learning


### 18. Application Example: Photo OCR


### 19. Conclusion





