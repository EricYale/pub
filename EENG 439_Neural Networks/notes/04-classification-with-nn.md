# Classification with Neural Networks

## One-Hot Output
- For classification, each output node represents the probability the data belongs to a class, with output on range $[0, 1]$.
- This means you should make your training data follow one-hot format, with each tagged object having one `1` and the rest `0`s.

$$
\begin{bmatrix}
0 \\
1 \\
0 \\
0 \\
\end{bmatrix}
$$

## Softmax
- Softmax is a function that takes a vector of real numbers and returns a vector of probabilities, making it so that the output vector is normalized (sums to 1).
- To take a softmax:
    1. Raise $e$ to the power of each element in the vector
    2. Divide each element by the sum of all elements in the vector

$$
-log(\frac{e^{z_i}}{\sum_{j=1}^{m}e^{z_j}})
$$

## Loss Function
- The loss function for classification is the cross-entropy loss function.
- The loss is equal to the sum of all expected values, times the log of the predicted values.

$$
L(\hat{y}, y) = -\sum_{i=1}^{m} y_i \log(\hat{y}_i)
$$

> Note: the loss before any training will be the $log_{10}$ of the # of classes.

- $y_i$ is zero except for the correct class (due to one-hot format), meaning only the correct class's probability is used in the loss function. However, this is OK because the softmax ensures normalization, so if incorrect classes are high, the correct class is lower.

> Note: Softmax will never reach a full binary one-hot output, so the loss will never be zero.
