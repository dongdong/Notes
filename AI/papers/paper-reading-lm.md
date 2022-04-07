### Paper Reading Notes


##### AlexNet

- ImageNet classification with deep convolutional neuron network
  * It shows that a large, deep convolutional neural network (without any unsupervised pre-training) is capable of achieving record-breaking result
  * larger dataset, more powerful model, better techniques for preventing overfitting
  * End-to-end, no pre-process or pre-training
- CNN
  * 5 convolutional layers + 3 fully connected layers
- Main tricks:
  * ReLU Nonlinearity - several times faster
  * Data augmentation - increase training set -> reduce overfitting, 256x256 -> random 224x224
  * Dropout
- Others:
  * Training on multiple GPUs
  * Local Response Normalization
  * Overlapping Pooling
  * weight decay - l2 regularization
  * Momentum
  

##### ResNet

- Deep Residual Learning for Image Recognition
  * shows that residual networks are easier to optimize, and can gain accuracy from considerably increased depth
  * 152 layers, but lower complexity
  * also powerful on object detection


- Degradation problem
  * deep model leads to high training error -> not overfitting
- deep residual learning framework
  * F(x) = H(x) - x
  * Hypothesis: it's easier to optimize the residual mapping than optimize the original, unreferenced mapping 
  * shortcut connection: skip one or more layers, perform identity mapping
  * no extra parameters to learn, easy to implement

  ![img.png](images/resnet_1.png)


- Network Architecture
  - Plain network - inspired by VGG
    - 3x3 filters
    - feature map size halved, number of filters doubled
  - Residual network
    - when same dimension: directly used
    - when dimension increased: a. zero padding, b. projection
  - Deeper Bottleneck Architecture
    - use 1x1 convolution layers to reduce and then restoring dimensions
    - reduce model parameters/computation -> reduce training time

  ![img.png](images/resnet_2.png)


- Other Implementation details
  - Image augmentation: 224x224 crop, horizontal flip, color augmentation
  - Batch normalization
  - sgd, min-batch, learning rate decay
  - weight decay, momentum
  - do not use dropout
  

##### Transformer


##### Bert


##### GPT


##### GPT-2


##### GPT-3


##### GAN


##### GNN
......