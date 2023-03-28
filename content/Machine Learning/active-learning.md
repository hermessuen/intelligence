---
title: "Active Learning"
date: 2023-03-28T00:07:04-08:00
draft: true
---

# What is Active Learning?

- **Def:** Active learning is a type of semi-supervised learning in which the learning algorithm selects unlabeled data points to be annotated by the user.
- **Algo:**
    1. Start with a small labeled dataset
    2. At each iteration, pick a set of unlabeled data points according to metric S. Label those points and train a new model
    3. Repeat step 2
- **Motivation:** The main motivation for active learning is data efficiency. When facing large unlabeled data, the cost associated with annotating those data could be huge. Active learning allows the model to achieve the same performance by annotating only a subset of data.

# Three Categories of Active Sampling

- **Stream-based selective sampling**
    - Unlabeled instances are fed into the model in a data stream. This means that upon being presented with a data instance, the learning algorithm will need to immediately decide if it wants to query its label.
    - Pro: memory efficiency
    - Con: hard to estimate the total number of data points queried
- **Pool-based sampling**
    - Evaluate the entire dataset before it selects the best query or set of queries
    - Pro: can decide the query threshold based on annotation budget
    - Con: requires substantial memory as the entire dataset needs to be stored in memory 
- **Membership query synthesis**
    - The active learner generates its own synthetic data for labeling
    - Pro: can generate the optimal instances that will benefit model learning the most
    - Con: only applicable if synthetic data are easy to generate 

# Uncertainty Sampling

Uncertainty sampling is a type of active learning that selects the data instances that the model is the most uncertain about to get human feedback. The intuition is straightforward: if the model struggles the most with predicting one example, then providing the correct answer to that problem will help the model improve the most. 

## Types of Uncertainty Scores

Several measures of uncertainy are available for uncertainty sampling. Here we discuss three of the most popular metrics:

### Least Confidence

- Sort by the model’s confidence scores.

![Source: https://towardsdatascience.com/active-learning-in-machine-learning-525e61be16e5. Same below.](Active%20Learning%20c3e79bd0e5624b6aa536f2b85085e0b9/Untitled.png)

- **Con:** Only takes into consideration the most probable label and disregards the other label probabilities.

### Margin Sampling

- Sort by the difference between the highest probability and the second-highest probability.

![Untitled](Active%20Learning%20c3e79bd0e5624b6aa536f2b85085e0b9/Untitled%201.png)

### Entropy

- High entropy: the model distributes equally the probability for all classes as it is not certain at all which class that data point belongs to.
- Low entropy: the model is very confident about the data point being in a specific class.

![Untitled](Active%20Learning%20c3e79bd0e5624b6aa536f2b85085e0b9/Untitled%202.png)

# **Balance Exploration and Exploitation**

- Relation to RL: essentially a question between trading off exploration and exploitation, but not in the action space or state space, but in the data space.

![Untitled](Active%20Learning%20c3e79bd0e5624b6aa536f2b85085e0b9/Untitled%203.png)

- D(xi): Label density score [EXPLORATION]
    - **Intuition:** Once a data point is labeled, we don’t want the other data points in its dense neighborhood to be labeled as well, in future iterations.
- R(xi): Uncertainty score [EXPLOITATION]
- Balancing the trade off:
    - At first: $\epsilon$ < 0.5
    - After a few iterations: $\epsilon$ > 0.5

# References

[](https://towardsdatascience.com/active-learning-in-machine-learning-525e61be16e5)

[Active learning machine learning: What it is and how it works](https://www.datarobot.com/blog/active-learning-machine-learning/)

[Active learning (machine learning)](https://en.wikipedia.org/wiki/Active_learning_(machine_learning))

[Guided Labeling Episode 3: Model Uncertainty - DATAVERSITY](https://www.dataversity.net/guided-labeling-episode-3-model-uncertainty/)