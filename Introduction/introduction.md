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
1  -1.449468563 -0.43467715
2  -1.412224970 -2.69728331
3  -1.356143535 -2.93309685
4  -1.295288538 -0.63168442
5  -1.109861637 -1.35620539
6  -0.472350831 -0.88871584
7  -0.307326190 -0.05702575
8  -0.294743273  2.23597211
9  -0.265656262  1.18730194
10 -0.045960507  3.31856798
11  0.005738867  0.51513747
12  0.275531235  3.22376965
13  0.362254084  1.25564122
14  0.399026190  0.92240848
15  0.512208606  4.54113381
16  0.532727425  2.86182990
17  0.742907240  4.51803132
18  1.075863450  4.51659463
19  1.676887157  5.18851912
20  2.021411486  7.63003891
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




