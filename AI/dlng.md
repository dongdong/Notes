### Outline

* Neural Networks and Deep Learning
* Improving Deep Neural Networks: Hyperparametere tuning, Regularization and Optimization
* Structuring your Machine Learning project
* Convolutional Neural Networks
* Natural Language Processing: Building sequence models


### 1. Introduction to Deep Learning

![intro_to_deep_learning](dlng/tf_1.jpg)

* Supervised Learning
* Network Architectures
* Structure & Unstructured data
* Data versus Performance
* Big breakthroug: Sigmoid -> relu
* Iterative Process

### 2. Logistic Regression as a Neural Network

![lr](dlng/tf_2.jpg)

* Binary classification
* Linear regression + sigmoid
* Loss function
* Gradient descent
* Mini Nerual Net 

### 3. Shallow Neural Networks

![snn](dlng/tf_3.jpg)

* 2 layer neural network
* Activation function and why
* Initializing parameters randomly


### 4. Deep Neural Networks

![dnn](dlng/tf_4.jpg)

* Why deep Neural networks?
* Features


### 5. Setting up your ML App

![setting_up](dlng/tf_5.jpg)

* Data splits & Distribution
* Bias &  Variance
* The ML recipe


### 6. Regularization Preventing overfitting

![regularization](dlng/tf_6.jpg)

* L1 & L2 regularization
* Dropout
* Data augmentation
* Early stopping


### 7. Optimizing Training

![optimizing_training](dlng/tf_7.jpg)

* Normalizing inputs
* Vanishing / Exploding gradients
* Gradient checking


### 8. Optimization Algorithms

![optimization_algorithms](dlng/tf_8.jpg)

* Mini-batch gradient descent
* Momentum
* RMSProp
* Adam
* Learning rate decay


### 9. Hyper-Parameter Tuning

![Hyperparam_tuning](dlng/tf_9.jpg)

* Hyper-params
* Grid search vs. Random search
* Scales
* Batch normalization
* Multi-class classification


### 10. Structuring your Machine Learning Porjects

![structure_ml_project](dlng/tf_10.jpg)

* Set goals
* Select dev/test sets
* Human level performance
* Guides to optimization


### 11. Error Analysis

![error_analysis](dlng/tf_11.jpg)

* Analysis mislabeled data
* Random errors vs. Systemic errors

### 12. Train vs. Dev/Test Mismatch

![train_dev_mismatch](dlng/tf_12.jpg)

* Available data
* Train-dev set
* Addressing data mismatch


### 13. Extended Learning

![extended_learning](dlng/tf_13.jpg)

* Transfer learning
* Multi-task learning
* End-to-end learning


### 14. Convolution Fundamentals

![cnn_basics](dlng/tf_14.jpg)

- Computer vision
- Why Convolutions?
- Convolution

![cnn_basics](dlng/tf_15.jpg)

- Padding
- Stride
- Filter
- One CONV. Net layer

![cnn_basics](dlng/tf_16.jpg)

- A Deep CNN
- Typical CONV. Net layers
- CONV net example (LeNet-5)


### 15. Classic Convolutional Networks 

![classic_conv_nets](dlng/tf_17.jpg)

- LeNet-5
- AlexNet (Relu)
- VGG-16


### 16. Special Networks

![Special_Networks](dlng/tf_18.jpg)

- ResNets
- Network in Network
- Inception Networks


### 17. Practical Advices

![practical_advices](dlng/tf_19.jpg)

- Use open source implementations
- Data Augmentation
- Transfer Learning
- Tips for doing well on benchmarks/competitions
	- Ensembling
	- Multi-crop at test time


### 18. Detection Algorithms

![detection_algorithms](dlng/tf_20.jpg)

- Object detection
- Landmark detection
- Sliding Windows
- YOLO: You Only Look Once
- IOU: Intersection Over Union
- Non Max Suppression
- Anchor Boxes


### 19. Face Recognition

![Face_recognition](dlng/tf_21.jpg)

- One-shot learning
- Siamese Network - DeepFace
- Triple Loss


### 20. Neural Style Transfer

![Neural_style_transfer](dlng/tf_22.jpg)

- Content Cost Function
- Style Const Function


### 21. Recurrent Neural Networks

![RNN_1](dlng/tf_23.jpg)

![RNN_2](dlng/tf_24.jpg)

- Sequence Problems
- Recurrent Neural Networks
- Types of RNN
- Language Modeling
- Sampling Sentences
- Vanishing Gradients
- GRU: Gated Recurrent Unit
- LSTM: Long Short Term Memory
- BRNN: Bi-Directional RNN
 

### 22. NLP Word Embeddings

![word2vec_1](dlng/tf_25.jpg)

![word2vec_2](dlng/tf_26.jpg)

- Word embeddings
- Using word embeddings
- Learning word embeddings
	- Using a neural language model
	- Skip-grams
	- Negative sampling
	- GloVe word vectors
- Sentiment classification
- Eliminating bias in word embeddings
	- Identify bias direction
	- Neutralize
	- Equalize pairs


### 23. Sequence to Sequence

![sequence-to-sequence_1](dlng/tf_27.jpg)

![sequence-to-sequence_2](dlng/tf_28.jpg)

- Basic Models
- Beam search
	- How do we pick B
	- Error analysis in Beam Search
- BLEU score
- Attention Model
- Speech Recognition
- Trigger Word detection


### Reference

* https://zhuanlan.zhihu.com/p/34346816