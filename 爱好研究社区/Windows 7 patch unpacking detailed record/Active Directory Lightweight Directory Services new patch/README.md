# Windows6.1-KB2462137-v2-x64 update.mum

## DirectoryServices-ADAM-Package-Client [目录服务 ADAM 包 客户端]

### The following is a detailed introduction to ADAM ?

    1.What is the Adam optimization algorithm?

    Adam is a first-order optimization algorithm that can replace the traditional stochastic gradient descent process, which iteratively updates the neural network weights based on the training data. Adam was originally proposed by Diederik Kingma of OpenAI and Jimmy Ba of the University of Toronto in the ICLR paper submitted to 2015 (Adam: A Method for Stochastic Optimization). Both parts of this paper are based on the discussion and interpretation of the paper.

    First of all, the algorithm is called "Adam", which is not an acronym or a person's name. Its name comes from adaptive moment estimation. When introducing this algorithm, the original paper listed the advantages of applying the Adam optimization algorithm to non-convex optimization problems:

    straight to the point
    Efficient computing
    less memory required
    Invariance to diagonal scaling of gradients (proved in part 2)
    Suitable for solving optimization problems with large-scale data and parameters
    Suitable for non-stationary targets
    Suitable for problems with very noisy or sparse gradients
    Hyperparameters can be interpreted intuitively, and basically only need a small amount of tuning


    2.Basic mechanism of Adam optimization algorithm

    Adam algorithm is different from traditional random gradient descent. The random gradient descent maintains a single learning rate (i.e. alpha) to update all weights, and the learning rate will not change during the training process. Adam designs independent adaptive learning rates for different parameters by calculating the first-order moment estimation and the second-order moment estimation of the gradient.

    The proponent of Adam algorithm described it as a set of advantages of two kinds of random gradient descent expansion, namely:
    Adaptive gradient algorithm (AdaGrad) reserves a learning rate for each parameter to improve the performance on sparse gradient (i.e. natural language and computer vision problems).


    Root-mean-square propagation (RMSProp) is based on the mean of the nearest magnitude of the weight gradient to adaptively guarantee the study rate of each parameter. This means that the algorithm has excellent performance in unsteady and online problems.

    Adam algorithm obtains the advantages of AdaGrad and RMSProp algorithm at the same time. Adam not only calculates the adaptive parameter learning rate based on the first-order moment mean value as the RMSProp algorithm, but also makes full use of the second-order moment mean value of the gradient (that is, the biased variance/uncentered variance). Specifically, the algorithm calculates the exponential moving average of the gradient, and the superparameters beta1 and beta2 control the decay rate of these moving averages.

    The initial value of the moving average and beta1 and beta2 are close to 1 (recommended value), so the deviation of moment estimation is close to 0. The deviation is improved by first calculating the estimate with deviation and then calculating the estimate corrected by deviation. If you are interested in the specific implementation details and derivation process, you can continue to read the second part and the original paper.

    3.Efficiency of Adam algorithm

     Adam is a very popular algorithm in the field of deep learning, because it can quickly achieve good results. The empirical results show that Adam algorithm has excellent performance in practice and has great advantages over other kinds of random optimization algorithms.

     In the original paper, the author empirically proved that the convergence of Adam algorithm conforms to the theoretical analysis. The Adam algorithm can apply the optimized logistic regression algorithm to the MNIST handwritten character recognition and IMDB emotion analysis data set, and can also be applied to the multi-layer perceptron algorithm on the MNIST data set and the convolutional neural network on the CIFAR-10 image recognition data set. They concluded: "In the case of using large models and data sets, we have proved the efficiency of the Adam optimization algorithm in solving local deep learning problems."

     Comparison of Adam optimization algorithm and other optimization algorithms in multi-layer perceptron model

     In fact, Indofar, RMSprop, Adadelta and Adam algorithms are relatively similar optimization algorithms, and they can perform very well in similar situations. However, the deviation correction of Adam algorithm makes it faster and better than RMSprop algorithm when the gradient becomes sparse. Inofsar and Adam optimization algorithms are basically the best global options. Similarly, in the CS231n course, Adam algorithm is also recommended as the default optimization algorithm.

     Although Adam algorithm is better than RMSProp in practice, we can also try SGD+Nesterov momentum as an alternative to Adam. That is, we usually recommend using Adam algorithm or SGD+Nesterov momentum method in the deep learning model.

    4.Parameter configuration of Adam

     Alpha: also known as learning rate or step size factor, it controls the update rate of weight (such as 0.001). Larger values (such as 0.3) will have faster initial learning before the learning rate is updated, while smaller values (such as 1.0E-5) will make the training converge to better performance.

     Beta1: the exponential decay rate of the first-order moment estimation (such as 0.9).

     Beta2: exponential decay rate of second-order moment estimation (such as 0.999). This super parameter should be set to a number close to 1 in sparse gradient (such as in NLP or computer vision tasks).
     
     Epsilon: This parameter is a very small number to prevent dividing by zero in the implementation (such as 10E-8).

     In addition, learning rate attenuation can also be applied to Adam. The original paper uses the decay rate alpha=alpha/sqrt (t) to update each epoch (t) in logistic regression.
