# Empirical Cumulative Distribution Function (ECDF) on Bimodal Data

This project demonstrates how to use the Empirical Cumulative Distribution Function (ECDF) to analyze data that does not follow a standard probability distribution such as the normal or binomial distribution.

Instead of assuming a theoretical distribution, the ECDF uses the observed data directly to estimate probabilities and answer questions about future observations.

The example in this notebook generates a bimodal dataset representing exam scores for students in a state-wide exam and uses ECDF to estimate probabilities of different score ranges.

---

## Overview

In many real-world situations, data is not well described by common distributions (normal, binomial, etc.). When this happens, one option is to work with the **Empirical Cumulative Distribution Function (ECDF)**, which is defined as:

$$
ECDF(x) = \frac{\text{Number of observations } \le x}{\text{Total number of observations}}
$$


This notebook:

- Creates a synthetic **bimodal** dataset by combining two normal distributions.
- Interprets the data as exam scores between 0 and 100.
- Uses ECDF to estimate the probabilities of scores being below, above, or within certain thresholds.
- Visualizes both the histogram of scores and the empirical CDF.

---

## What the Notebook Covers

### 1. Generate a Bimodal Dataset

- Two normal distributions are created:
  - One centered around 80 (e.g., high-performing group).
  - One centered around 60 (e.g., main population).
- These samples are combined into a single array to form a bimodal distribution.

```python
from numpy.random import normal
from numpy import hstack

sample1 = normal(loc=80, scale=5, size=300)
sample2 = normal(loc=60, scale=5, size=700)
sample = hstack((sample1, sample2))
