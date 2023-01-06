This code calculates the Kullback-Leibler (KL) divergence between different Poisson distributions using samples drawn from those distributions. The KL divergence is a measure of the distance between two probability distributions, and it is commonly used in information theory and machine learning.

The code first defines three Poisson distributions with different values of the parameter lambda, which determines the mean of the distribution. It then generates samples from each of these distributions using the sample method of the tfd.Poisson class.

Next, the code estimates the value of lambda for each distribution using the maximum likelihood estimation (MLE) method. This involves calculating the mean of the samples and using that value as an estimate of lambda.

The code then constructs the probability distribution functions (PDFs) for each distribution using the estimated values of lambda. It does this by calculating the probability of each value in a range of possible values (0 to 30 in this case) using the probability mass function (PMF) of the Poisson distribution.

Finally, the code calculates the KL divergence between each pair of distributions using the kl_divergence function, which takes as input the shannon_entropy and cross_entropy functions that are defined earlier in the code. The kl_divergence function calculates the KL divergence between two distributions by first calculating the Shannon entropy of the first distribution using the shannon_entropy function and then calculating the cross entropy between the first and second distributions using the cross_entropy function.

The code then performs a series of checks to verify that the KL divergence behaves as expected. For example, it checks that the KL divergence between two identical distributions is zero, that the KL divergence between two distributions is not symmetric (i.e., the KL divergence from distribution A to distribution B is not equal to the KL divergence from distribution B to distribution A), and that the KL divergence between two distributions is always greater than or equal to zero.


```py title="kl_divergence" linenums="1"
from typing import List, NamedTuple, Dict, Callable
from pprint import pprint

import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
sns.set_style("whitegrid")

import tensorflow_probability as tfp
tfd = tfp.distributions

def shannon_entropy(variable1: List) -> float:
    return np.nansum(variable1 * -np.log(variable1))

def cross_entropy(variable1: np.array, variable2: np.array) -> float:
    return - np.nansum(variable1 * np.log(variable2))

def kl_divergence(shannon_entropy: Callable, cross_entropy: Callable) -> float:
    return -shannon_entropy + cross_entropy

# 1. Get samples 
A = tfd.Poisson(2) # lambda = 2
sampleA =  A.sample(1000)
B = tfd.Poisson(5) # lambda = 5
sampleB = B.sample(1000)
C = tfd.Poisson(10)# lambda = 10
sampleC = C.sample(1000)

# 2. Find lambda: Maximum Likelihood Estimation
lambdaA = sampleA.numpy().sum()/len(sampleA)
lambdaB = sampleB.numpy().sum()/len(sampleB)
lambdaC = sampleC.numpy().sum()/len(sampleC)

# 3. Assume the original distribution and get probabilities for same length
pdfA = []
for k in range(30):
    probability = lambdaA**k*np.e**(-lambdaA)/np.math.factorial(k)
    pdfA.append(probability)
    
pdfB = []
for k in range(30):
    probability = lambdaB**k*np.e**(-lambdaB)/np.math.factorial(k)
    pdfB.append(probability)

pdfC = []
for k in range(30):
    probability = lambdaC**k*np.e**(-lambdaC)/np.math.factorial(k)
    pdfC.append(probability)

# 4. Measure KL Divergence
divergence_AA = kl_divergence(shannon_entropy(pdfA), cross_entropy(pdfA, pdfA))
divergence_AB = kl_divergence(shannon_entropy(pdfA), cross_entropy(pdfA, pdfB))
divergence_BA = kl_divergence(shannon_entropy(pdfB), cross_entropy(pdfB, pdfA))
divergence_AC = kl_divergence(shannon_entropy(pdfA), cross_entropy(pdfA, pdfC))

# 5. Verify the behavior
assert divergence_AA == 0; print("Identical distributions")
assert divergence_AB != divergence_BA; print("KL Divergencve is assymetric")
assert divergence_AB < divergence_AC; print("D_KL(Pois(2) || Pois(5)) < D_KL(Pois(2) || Pois(10)) ")
```