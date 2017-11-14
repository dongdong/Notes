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

	
* Regularization 

	- Cost function

	![cost_function](imgs/mlng_7_4.png)

	![regularization_parameter](imgs/mlng_7_5.png)

	- gradient descent

	![regularized_linear_regression](imgs/mlng_7_6.png)

	- Regularized logistic regression

	![regularized_logistic_regression_1](imgs/mlng_7_7.png)
	
	![regularized_logistic_regression_2](imgs/mlng_7_8.png)


### 8. Neural Networks: Representation

* Non-linear hypotheses
	- Non-linear classification


* Neural Networks
	- Origins: algorihtms that try to mimic the brain
	- Was very widely used in 80s and early 90s; popularity diminished in late 90s
	- Recent resurgence: state-of-the-art technique for many applications


* Model representation

	![neural_network_model_1](imgs/mlng_8_1.png)

	![neural_network_model_2](imgs/mlng_8_2.png)


* Forward propagation

	![forward_propagation](imgs/mlng_8_3.png)


* Example and intuition

	![forward_propagation_example](imgs/mlng_8_4.png)


* Multi-class classification

	![multi-class_classification](imgs/mlng_8_5.png)


### 9. Nural Networks: Learning

* Cost function
	
	![cost_function](imgs/mlng_9_1.png)


* Backpropagation algorithm

	- Forward propagation

	![forward-propagation](imgs/mlng_9_2.png)

	- Backpropagation
	
	![backpropagation_1](imgs/mlng_9_3.png)

	![backpropagation_2](imgs/mlng_9_4.png)


* Gradient checking

	![numerical_estimation_of_gradients](imgs/mlng_9_5.png)

	![parameter_vector](imgs/mlng_9_6.png)

	![implementation_note](imgs/mlng_9_7.png)


* Random initialization
	- Zero initialization: after each update, parameters corresponding to inputs going into each hidden units are identical
	- Random initialization: symmetry breaking


* Training a neural network

	- Pick a network architecture

	![network architecture](imgs/mlng_9_8.png)

	- Training a nerual network 
	
	![training_steps](imgs/mlng_9_9.png)

	
### 10. Advice for Applying Machine Learning

* Machine learning diagnostic
	- Diagnostic: a test that you can run to gain insight what is/isn't working with a learning algorithm, and gain guidance as to how best to improve its performance
	- Diagnostics can take time to implement, but doing so can be a very good use of your time


* Evaluating a hypothesis
	- training set & test set 


* Model selection and training/validation/test sets
	
	![model_selection_1](imgs/mlng_10_1.png)

	![train_validation_test_error](imgs/mlng_10_2.png)

	![model_selection_2](imgs/mlng_10_3.png)
	

* Diagnosing bias vs variance

	![bias_variance_1](imgs/mlng_10_4.png)
	
	![bias_variance_2](imgs/mlng_10_5.png)

	![bias_variance_3](imgs/mlng_10_6.png)


* Regularization and bias/variance

	![Linear_regression_with_regularization](imgs/mlng_10_7.png)

	![choosing_regularization_parameter_1](imgs/mlng_10_8.png)

	![choosing_regularization_parameter_2](imgs/mlng_10_9.png)

	![bias_variance_of_regularization_parameter](imgs/mlng_10_10.png)

	
* Learning curves

	![learning_curves](imgs/mlng_10_11.png)

	![learning_curves_high_bias](imgs/mlng_10_12.png)

	![learning_curves_high_variance](imgs/mlng_10_13.png)
	

* Summary: deciding what to do next

	![debuging_learning_algorithm](imgs/mlng_10_14.png)

	
* Neural networks and overfitting

	![neural_networks_and_overfitting](imgs/mlng_10_15.png)


### 11. Machine Learning System Design

* Error analysis
	- Recommended approach
		- Start with a simple algorithm that you can implement quickly. Implement it and test it on your cross-validation data
		- Plot learning curves to decide if more data, more feature, etc. are likely to help
		- Error analysis: Manually examine the examples in cross validation set that your algorithm made errors on. See if you spot any systematic trend in what type of examples it is making errors on
	- Error analysis may not be helpful for deciding if this is likely to improve performance. Only solution is to try it and see if it works; Need numerical evaluation of algorithm's performance


* Error metrics for skewed classes
	
	![precision_recall](imgs/mlng_11_1.png)

	
* Trading off precision and recall
	
	![trading_off_precision_recall](imgs/mlng_11_2.png)

	![F1_score](imgs/mlng_11_3.png)


* Data for machine learning

	![data_for_machine_learning](imgs/mlng_11_4.png)

	![large_data_rationale](imgs/mlng_11_5.png)


### 12. Support Vector Machines

* Optimization objective
	
	![cost_function_1](imgs/mlng_12_1.png)


* Large margin intuition
	
	![cost_function_2](imgs/mlng_12_2.png)
	
	![decision_boundary](imgs/mlng_12_3.png)


* Kernels

	- Non-linear decision boundary

	![non-linear_decision_boundary](imgs/mlng_12_4.png)

	![kernel](imgs/mlng_12_5.png)

	![kernel_and_similarity](imgs/mlng_12_6.png)

	![kernel_similarity_example](imgs/mlng_12_7.png)

	![kernel_example](imgs/mlng_12_8.png)

	![svm_with_kernel_1](imgs/mlng_12_9.png)

	![svm_with_kernel_2](imgs/mlng_12_10.png)

	![svm_parameters](imgs/mlng_12_11.png)


* Using an SVM

	![logistic_regression_vs_SVM](imgs/mlng_12_12.png)


### 13. Clustering

* K-means algorithm

	![k-means](imgs/mlng_13_1.png)


* Optimization objective

	![optimization_objectives_1](imgs/mlng_13_2.png)

	![optimization_objectives_2](imgs/mlng_13_3.png)
	

* Random initialization

	![random_initialization_1](imgs/mlng_13_4.png)

	![local_optima](imgs/mlng_13_5.png)

	![random_initialization_1](imgs/mlng_13_6.png)


* choosing the number of clusters

	![elbow_method](imgs/mlng_13_7.png)

	![choosing_value_k](imgs/mlng_13_8.png)


### 14. Dimensionality Reduction

* Motivation I: Data Compression

	![reduce_data_from_2D_to_1D](imgs/mlng_14_1.png)

	![reduce_data_from_3D_to_2D](imgs/mlng_14_2.png)
	

* Motivation II: Data Visualization

	
* Principal Component Analysis problem formulation
	
	![PCA_problem_formulation](imgs/mlng_14_3.png)

	
* Principal Component Analysis algorithm

	- Data preprocessing
	
	![data_preprocessing](imgs/mlng_14_4.png)

	- PCA algorithm

	![svd](imgs/mlng_14_5.png)

	- Summary

	![svd_summary](imgs/mlng_14_6.png)
	

* Reconstruction from compressed representation

	![reconstruction](imgs/mlng_14_7.png)


* Choosing the number of principal components

	



### 15. Anomaly Detection


### 16. Recommender Systems


### 17. Large Scale Machine Learning


### 18. Application Example: Photo OCR


### 19. Conclusion





