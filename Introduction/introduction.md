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

Contents
========================================================
- I will show you the basics, you should figure out the rest yourselves.
- Please, do ask questions and interrupt.

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
             x          y
1  -3.36036438 -8.2255986
2  -1.67415781 -3.4254527
3  -1.28843583 -1.6274842
4  -1.12398265 -1.6607849
5  -0.79909384 -0.3644841
6  -0.66600733  0.3086723
7  -0.59372833  0.1873957
8  -0.59034664  0.8194618
9  -0.58946921  0.8746883
10 -0.11633386  0.9574701
11 -0.05839936  1.5326324
12 -0.04541250  1.4010884
13  0.01851941  1.7617596
14  0.17032248  2.7476527
15  0.47701840  3.4969438
16  0.91837569  3.3880732
17  1.12012158  5.7335285
18  1.15159940  5.5316939
19  1.29460706  6.3070198
20  1.42823681  5.5571250
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




