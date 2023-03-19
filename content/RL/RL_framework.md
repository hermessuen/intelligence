
---
title: "The RL Framework"
date: 2023-03-12T00:06:02-08:00
draft: false
---

## The Reinforcement Learning Framework

In its most general form, Reinforcement Learning is all about learning the best way to act given a current state and action. Many toy and example RL problems have to do with games - Atari, Go, Pong, etc. RL is also closely linked with Control problems and of course there are many applications of RL for robotics. These are all classic examples of "intelligence". In popular literature Chess is often (perhaps incorrectly) used as an example of peak human reasoning. 


What is interesting though is that this general framework of learning how to act given a current state can be applied to all sorts of situations other than robotics or games. 




#### Enter Finance
A greedy (no pun intended) example of this would be in the world of finance. Remember that in RL framework, we believe that the entire sequence of an agents history (a vector of tuples, which of which consists of an action, reward, transition), can be put into a single representation. We call this **S_t**. We believe that the this state completely determines **what will happen next**. The environment of course has a state, that we sometimes observe completely (i.e. in a game) where I know if this is the current state of the pixels, I know exactly what the next thing state will be. This is also down as a Markov Decision Process. 

Can everything be cast as a Markov Decision Process? i.e. can everything be described as a series of states that are entirely dependent on its previous state?

In a world like Finance, it may seem tricky, but it is only tricky because the agent can only partially . Suppose we want to train an agent to learn how to trade stocks. What would we want the states to be? We want the agent to take in a state, and learn what the optimal strategy is to move forward. The environment's state (the stock market) is actually Markovian. As in, if one knew *everything* there is to know about the universe, what people were thinking, the sate of the weather, etc, then of course the stock price the next day is known. It's just too much information 


Thus, we must reduce the state the agent sees. A classic formulation of a stock trading agent is to frame the state as a 3-dimensional vector. The first dimension corresponds to the stock price, the second dimension the stock shares owned and the third dimension represents the remaining balance of the agent. Is this enough? At least emprirically, it captures enough information to form a probability distribution over how the next state will look like and the total predicted reward. No one is getting rich anytime soon, but training an agent may at least be better than a human. Or is it? 




#### How do Humans do it? 
In the show Billions, a hedge fund manager is known for "beating the market" consistently, year after year. How does he do it? He too consumes a lot of information - more so than the simple agent we described above. His "state" of the world includes the news, previous stock trading experiences, conversations with friends, real-world events, and what other hedge funds are doing. The question is - are humans also casting the problem of stock prediction as Markovian in their own head? I believe much of what we predict about the world has some element of a Markov Decision Process, whether or not we are aware of it. We make some predictions over what the Expected Value is of various actions, and try to maximize some rewards. I think about sending a text to someone I have a crush on, what do I think her reaction will be? What is the likelihood of the various responses? What constitutes my reward in this case? The same is true for all aspects of our lives - work, family, hobbies. RL is useful for modelling games, and we are all playing games, of various kinds.


#### What problems cannot be cast into an RL framework?
My current thinking then, is that the limitations of using RL for a general learning machine lies entirely in a machines ability to cast really complicated games into an MDP. The complexity of finding a policy typically will grow exponentially with the number of States (although there are efforts to go around this). Any true AGI, if it wants to act optimally to learn arbitrary tasks, will have to confront extremely large state spaces. Just think about parameterizing all of the information we receive within a day, through twitter, articles, and conversations. Additionally, we are often balancing various rewards at various times, and sometimes the reward itself is not so clear. Can literally everything be placed onto a scalar value? 

Additionally, for many simple problems, the states are clear. In a chess board, we easily see what the state of the game is. But for other difficult tasks, humans themselves are unsure of the state we are in. An easy solution would be to give an agent simply all of the possible information (such as LLM's being trained on large swaths of the internet). The limitation for RL is being able to **attend** to the right values, and reduce the complexity of all this information, in the cases where humans ourselves are unsure of what the possible states are



