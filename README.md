# CIFAR10
Creating different Neural Networks models to tackle this common CIFAR10 datasets.\
Note: Datasets are unable to be uploaded due to the 25mb file size limit.

Convolutional Neural Networks model should perform a lot better in tackling this problem, however I will still try with MLP model and see how much I can do with it.\
I will revisit this problem again with CNN in the future if needed.


## Approaches:
1. MLP (20 x 100, ELU, he_normal, softmax, Nadam, Cat-CrossEntropy, EarlyStopping, Performance LR Schedule)
2. MLP (20 x 100, ELU, he_normal, softmax, Nadam, Cat-CrossEntropy, ***Batch Normalization***, EarlyStopping, Performance LR Schedule)
3. MLP (20 x 100, ***No PCA***, ELU, he_normal, softmax, Nadam, Cat-CrossEntropy, EarlyStopping, Performance LR Schedule)
4. MLP (20 x 100, ***SELU***, ***lecun_normal***, softmax, Nadam, Cat-CrossEntropy, EarlyStopping, Performance LR Schedule)
5. MLP (20 x 100, ELU, he_normal, softmax, Nadam, Cat-CrossEntropy, ***Dropout***, EarlyStopping, Performance LR Schedule)
6. MLP (5 x 400, ELU, glorot_uniform, softmax, Nadam, Cat-CrossEntropy, EarlyStopping, Performance LR Schedule)
7. MLP (5 x 400, ELU, glorot_uniform, softmax, Nadam, Cat-CrossEntropy, EarlyStopping, ***L1***, Performance LR Schedule)
8. MLP (5 x 400, ELU, glorot_uniform, softmax, Nadam, Cat-CrossEntropy, EarlyStopping, ***L1***, ***Dropout***, Performance LR Schedule)

## Conclusion
The best MLP model that I discovered so far for predicting CIFAR10 datasets is as follow:

Model: Sequential (5 hidden layers with 400 neurons each)\
Activation: ELU\
Initialization: Glorot Uniform\
Regularization: Early Stopping, L1 (a = 0.0001) Dropout (rate = 0.1)\
Optimizer: Nadam\
Loss Function: Sparse Categorical Cross Entropy\
Learning Rate Schedule: Performance Scheduler (factor = 0.5, patience = 3)\
Output Activation: Softmax

Evaluation Accuracy: 0.5680

Perhaps we should try other neural networks architectures in the future, it seems like this is pretty much what we can try for now.
