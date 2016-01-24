Bayesian Biostatistics
========================================================
author: Petr Keil 
date: January 2016

![](introduction-figure/theorem.png)

![](introduction-figure/logo.jpg)

Contents
========================================================
***DAY 1***
- Likelihood, probability distributions
- First Bayesian steps

***DAY 2***
- First Bayesian steps
- Classical models (regression, ANOVA)

***DAY 3***
- Advanced models (mixed, time series)
- Inference, uncertainty, model selection.

Elementary notation
========================================================
- $P(A)$ vs $p(A)$ ... Probability vs probability density
- $P(A \cap B)$ ... Joint (intersection) probability (AND)
- $P(A \cup B)$ ... Union probability (OR)
- $P(A|B)$ ... Conditional probability (GIVEN THAT)
- $\sim$ ... is distributed as
- $\propto$ ... is proportional to (related by constant multiplication)

Elementary notation
========================================================
- $P(A)$ vs $p(A)$
- $P(A \cap B)$
- $P(A \cup B)$
- $P(A|B)$
- $\sim$ 
- $\propto$ 

========================================================

![eu](introduction-figure/plato2.jpg)

*Statistical models are stories about how the data came to be.*

========================================================

![eu](introduction-figure/plato2.jpg)

*Parametric statistical modeling* means describing a caricature of the "machine" that plausibly could have produced the nubmers we observe.

Kéry 2010

Data
========================================================

```
            x           y
1  -2.6752963 -7.30451838
2  -1.5043773 -3.31614134
3  -1.2159767 -3.06174470
4  -0.8751864 -0.24706471
5  -0.8324993 -1.00163385
6  -0.6257749  0.90514833
7  -0.4790895 -0.05846111
8  -0.3962544  1.83626690
9  -0.1467560  1.60552707
10  0.3358358  2.05026583
11  0.3801426  2.15671791
12  0.4667478  3.00757351
13  0.5963684  2.99207297
14  0.6215438  5.03307082
15  0.6406253  3.10982529
16  0.6940547  5.14629478
17  0.7020274  3.92351235
18  1.2788644  6.95091694
19  1.3649134  6.82355127
20  1.4449811  5.40895676
```

Data
========================================================
![plot of chunk unnamed-chunk-2](introduction-figure/unnamed-chunk-2-1.png) 

Data, model, parameters
========================================================
![plot of chunk unnamed-chunk-3](introduction-figure/unnamed-chunk-3-1.png) 

$y_i \sim Normal(\mu_i, \sigma)$

$\mu_i = a + b \times x_i$ 

Can you separate the **deterministic** and the **stochastic** part?

Data
========================================================
![plot of chunk unnamed-chunk-4](introduction-figure/unnamed-chunk-4-1.png) 

Data, model, parameters
========================================================
![plot of chunk unnamed-chunk-5](introduction-figure/unnamed-chunk-5-1.png) 

Can you separate the **deterministic** and the **stochastic** part?

$x_i \sim Normal(\mu, \sigma)$

Can you tell what is based on a parametric model?
========================================================
- Permutation tests
- Kruskall-Wallis test
- Histogram
- t-test
- Neural networks
- ANOVA
- Survival analysis
- PCA (principal components analysis)
- Normal distribution

Data, model, parameters
========================================================

Let's use $y$ for data, and $\theta$ for parameters.

$p(\theta | y, model)$ or $p(y | \theta, model)$ 

The model is always given (assumed), and usually omitted:

$p(y|\theta)$  ... "likelihood-based" or "frequentist" statistics 

$p(\theta|y)$ ... Bayesian statistics

Why go Bayesian?
========================================================
- Numerically tractable for models of any **complexity**.
- Unbiased for **small sample sizes**.
- It works with **uncertainty**.
- Extremely **simple inference**.
- The option of using **prior information**.
- It gives **perspective**.

The pitfalls
========================================================
- Steep learning curve.
- Tedious at many levels. 
- You will have to learn some programming.
- It can be computationally intensive, slow.
- Problematic model selection.
- Not an exploratory analysis or data mining tool.

To be thrown away
========================================================
- Null hypotheses formulation and testing
- P-values, significance at $\alpha=0.05$, ...
- Degrees of freedom, test statistics
- Post-hoc comparisons
- Sample size corrections

Remains
========================================================
- Regression, t-test, ANOVA, ANCOVA, MANOVA
- Generalized Linear Models (GLM)
- GAM, GLS, autoregressive models
- Mixed-effects (multilevel, hierarchical) models

Are hierarchical models always Bayesian?
=======================================================
- No

Myths about Bayes
========================================================
- It is a 'subjective' statistics.
- The main reason to go Bayesian is to use **the Priors**.
- Bayesian statistics is heavy on equations.

Elementary notation
========================================================
- $P(A)$ vs $p(A)$
- $P(A \cap B)$
- $P(A \cup B)$
- $P(A|B)$
- $\sim$ 
- $\propto$ 

Indexing in R and BUGS: 1 dimension
========================================================

```r
  x <- c(2.3, 4.7, 2.1, 1.8, 0.2)
  x
```

```
[1] 2.3 4.7 2.1 1.8 0.2
```

```r
  x[3] 
```

```
[1] 2.1
```

Indexing in R and BUGS: 2 dimensions
========================================================

```r
  X <- matrix(c(2.3, 4.7, 2.1, 1.8), 
              nrow=2, ncol=2)
  X
```

```
     [,1] [,2]
[1,]  2.3  2.1
[2,]  4.7  1.8
```

```r
  X[2,1] 
```

```
[1] 4.7
```

Lists in R
========================================================

```r
  x <- c(2.3, 4.7, 2.1, 1.8, 0.2)
  N <- 5
  data <- list(x=x, N=N)
  data
```

```
$x
[1] 2.3 4.7 2.1 1.8 0.2

$N
[1] 5
```

```r
  data$x # indexing by name
```

```
[1] 2.3 4.7 2.1 1.8 0.2
```

For loops in R (and BUGS)
========================================================

```r
for (i in 1:5)
{
  statement <- paste("Iteration", i)
  print(statement)
}
```

```
[1] "Iteration 1"
[1] "Iteration 2"
[1] "Iteration 3"
[1] "Iteration 4"
[1] "Iteration 5"
```




