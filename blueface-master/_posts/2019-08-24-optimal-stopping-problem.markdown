---
layout: post
title: Optimal Stopping Problem
tags: [distill]
mathjax: true
---

There are a lot of everyday situations where people make decisions one after the other, and what is decided earlier affects the choices later on. Most people probably go by some gut feeling about when it’s time to stop and select the next best option and settle down.

In this article we will examine the “Optimal Stopping Problem,” a mathematical puzzle that can manifest in many different real world examples. For instance:

* When should a hiring manager stop interviewing people for a new job position?   
This is the classical “secretary problem” within the field of study of mathematics: probability-optimization. This problem in it’s simplest form has following features:
    - There is one secretarial position available. 
    - The number of applicants is $n$. 
    - The applicants are interviewed sequentially in random order, each order being equally likely. 
    - After each interview the hiring manager must decide to reject or hire the applicant.
    - An applicant once rejected cannot later be recalled. 
    - Once the hiring manager decides to hire an applicant his/her search is over and there is no need to interview any more candidates.  
This basic problem has a remarkably simple solution and was outlined in the basic paper by  Gilbert and Mosteller ( 1966 ), with elegant derivations and extensions in a number of important directions.

* We have a house and we wish to sell it. Each day we get a new offer for the house, which could be higher or lower than the previous offer; however, each day the house is on the market we must pay for advertising. We wish to maximise the amount you earn by choosing a stopping rule. When should we stop looking at potential buyers and finally settle the deal?

* At some point in a lot of peoples lives, we wonder when we should stop dating and finally settle down with the right partner. Most people probably go by some gut feeling about when it’s time to stop. Editor’s Note: Of course, for mathematicians this is a purely theoretical example.

* Suppose we are a doctor and patients arrive sequentially at our clinic and must be treated immediately by one of the treatments. It is assumed that response from treatment is immediate so that the effectiveness of the treatment that the present patient receives is known before the next patient is treated. It is not known precisely which one of the treatments is best, but we must decide which treatment to give each patient, keeping in mind that our goal is to cure as many patients as possible. This may require us to give a patient a treatment which is not the one that looks best at the present time in order to gain information that may be of use to future patients. When should we **stop evaluating** more treatments and finally select the best one?  

There are many different solutions to the problems listed above, as the strategy we choose will depend on our objective. Do we want to ensure that the option we select is better than average? What if we just want to be sure that we do not pick the worst option? In this article our goal will be to “**minimize the risk**” of missing the best option. In other words, we want to “maximize the chances” (i.e. probability) of selecting the best option.

### The Prelude

The general form of our strategy will be to “gather information” when we are presented with our first options. We know that we will not choose any of these; however, we will examine them in order to know “how good” we should expect our options to be. After a certain point, once we are done gathering information, we will choose the first option that was better than all the ones we have seen before. After some thought, we can see that this strategy makes some intuitive sense. We don’t want to choose an option too early since there would be a high likelihood a better option would come later. But when should we stop gathering information? While we don’t want to choose an option too early, we certainly don’t want to gather information for too long and risk the best option passing us by.

This type of problem is called the “**Optimal Stopping Problem**", which mathematicians and computer scientists have researched for many years.

### A Real-life Example

Suppose we want to sell our house. We have a pool of n potential buyers (we number them from $1$ to $n$), who we meet one after the other. After a potential buyer has made their offer, we must decline or accept their offer. If we decide to accept their offer, we can no longer sell the house to anyone else and if we reject an offer the buyer will take their business elsewhere, and we will not be able to change our minds later on. For simplicity’s sake, we will assume there is no advertising cost (i.e. we do not have to pay to keep our house on the market).

Among our pool of $n$ people, there’s at least one who gives us the highest value for our property. We will call that person  $m$  (where  $m$  ranges from  $1$  to  $n$) – it’s who we’d ideally want to end up making deal with.

Our strategy is to discuss the deal with  $m-1$  of the $n$ people and then settle with the next best person who is better. (The reason for doing the calculations with  $m-1$  is that  m is the minimum number of potential buyers that we will encounter; there are  $m-1$  who give us the data we need before we start searching, and the $m^{th}$ is the first one who can be accepted.)

Given a pool of $n$ potential buyers, let $P(m; n)$ represent the probability that we will choose the best offer if we use the strategy discussed earlier. I.e. If there are $n$ buyers and we “gather information” during the first $m-1$ offers and pick the first offer that is better than the current best, the probability that we will select the best possible offer is $P(m; n)$.

Notice immediately that $P(1; n) = \dfrac{1}{n}$ and $P(n; n) = \dfrac{1}{n}$. These two cases essentially give no choice, meaning, it is just like the probability of picking one person at random out of total number of people ($n$) and hence the probability is $\dfrac{1}{n}$. But interesting things happen ‘***in between***’ these two extremes. As we see more people , we already have a notion of the “best so far,” and the next person we see that beats the current “best so far” is more likely to be the best person in the group for us. Unfortunately, it works the other way around as well. As we continue to see more people, the likelihood of having already passed the best so far increases, thereby decreasing our chances at finding the optimal person.

We want to find the optimal place to stop – a sort of middle ground that maximizes our chances of choosing the optimal person.

To do this, we want to maximize $P(m; n)$. In the process of doing this, we want to make sure our solution generalizes. A good way to generalize is to find the right ratio $\dfrac{m}{n}$, the percentage of our population that we should analyze before making a decision.

#### Mathematical Formalism
Our first step here is to get an equation for $P(m; n)$.

Let’s say we have collected information about $m - 1$ potential buyers and now are looking at the $k^{th}$ person in the sequence, where  $m-1 \leq k \leq n$.

Now let’s break down some things that are going on here:  
* We know that this  $k^{th}$  person has a $\dfrac{1}{n}$ probability of being the best buyer.
* We also know that in order to be considering the $k^{th}$ buyer in this sequence, the highest ranking person thus far must be in the group of $m - 1$ people out of the $k - 1$ people we had previously inspected and rejected (otherwise we would have stopped at someone before the $k^{th}$ person).

And the probability of the highest ranked person thus far being in that group of $m - 1$ people out of the $k - 1$ people inspected is:
\\[ \dfrac{m - 1}{k - 1}. \\]

And therefore, the overall probability of finding the best potential partner this time is:
\\[ (\dfrac{m - 1}{k - 1}).(\dfrac{1}{n}) = \dfrac{m - 1}{n(k - 1)}\\]

Note: In the following section we will use summation notation ($ \sum $ symbol), which works as follows: Suppose we have a sequence of numbers $x_1, x_2, ..., x_n$, then, by definition, $\sum_{i=1}^{n} x_i = x_1 + x_2 + x_3 + ... + x_n$. Thus $\sum_{i=1}^{n} 1 = n$ and $\sum_{i=1}^{3} x_i = x_1 + x_2 + x_3$. We use this notation because it is shorter than writing out each term in the sum.

Now to determine $ P(m; n) $, we must remember that $ k $ can take on any value from $ m $ to $ n $. As a consequence, we must sum these probabilities for any value of $ k $ (note the range of $ k $ above). A compact way to express this is as follows:
\\[P(m; n) =\sum_{k=m}^{n} \dfrac{m-1}{n(k - 1)}= \dfrac{m-1}{n}\sum_{k=m}^{n}\dfrac{1}{k-1}. \tag{1} \label{1}\\]

At this point, it is possible to determine the maximum value using methods of optimization one learns in calculus, but this can get nasty pretty quickly. We will lay out a more elegant (albeit more mathematically involved) approach in the following section.

#### To Get More Technical
Given a number $n$, we want to maximize the value of $P(m;n)$. Hence, the optimal value for $ m $ will be such that:
       \\[P(m - 1; n) < P(m; n) \text{ and } P(m + 1; n) < P(m;n) \tag{2} \label{2}\\]

Author’s Note: If you want to be very pedantic, you could ask what happens if there are two “best” values of $ m $, with one of those strict inequality signs replaced by a partial inequality. It turns out that the only time when equality is possible is when $ n=2 $, which is not very interesting anyway.

Let’s break this down part by part. From the first inequality in (\ref{2}) and using (\ref{1}):
\\[P(m - 1; n) < P (m; n)\\]

\\[\dfrac{m-2}{n}\sum_{k=m-1}^{n} \dfrac{1}{k - 1}<\dfrac{m-1}{n} \sum_{k=m}^{n}\dfrac{1}{k-1}\\]

\\[(m-2)\sum_{k=m-1}^{n} \dfrac{1}{k - 1}<(m-1) \sum_{k=m}^{n}\dfrac{1}{k-1}.\\]

Rewriting the left hand side:

\\[(m-2)(\dfrac{1}{m-2})+\sum_{k=m}^{n} \dfrac{1}{k - 1}<(m-1) \sum_{k=m}^{n}\dfrac{1}{k-1}.\\]

After algebraic simplification, we get:
    \\[1<\sum_{k=m}^{n}\dfrac{1}{k-1}\tag{3} \label{3}\\]

Let’s now do the same thing for the other inequality from (\ref{2}):

\\[P (m; n) > P (m + 1; n)\\]

\\[(m-1)\sum_{k=m}^{n}\dfrac{1}{k-1}>m\sum_{k=m+1}^{n}\dfrac{1}{k-1}\\]

Performing a similar calculations to what we did with the last inequality, we get:

\\[(m-1)(\dfrac{1}{m-1}+\sum_{k=m+1}^{n}\dfrac{1}{k-1})>m\sum_{k=m+1}^{n}\dfrac{1}{k-1}\\]

\\[(1+(m-1)\sum_{k=m+1}^{n}\dfrac{1}{k-1})>m\sum_{k=m+1}^{n}\dfrac{1}{k-1}\\]

\\[1>\sum_{k=m+1}^{n}\dfrac{1}{k-1}\tag{4}\label{4}\\]

Let’s remember that our goal here is to find an appropriate approximation for the ratio $ \dfrac{m}{n} $ for the best $ m  $.

One fact that is going to help us immensely in this calculation is the approximation of the partial sum of a harmonic series. Mathematically, the approximation is:

 \\[\sum_{k=1}^{x}\dfrac{1}{k}\approx\ln(x)+c \\]

where $ c $ is the Euler-Mascheroni constant.

Now this approximation greatly helps us simplify inequalities (\ref{3}) and (\ref{4}).

Using this approximation for (\ref{3}), we derive the following:

\\[1<\sum_{k=m}^{n}\dfrac{1}{k-1}=\sum_{k=m-1}^{n-1}\dfrac{1}{k}=\sum_{k=1}^{n-1}\dfrac{1}{k}-\sum_{k=1}^{m-2}\dfrac{1}{k}\approx\ln(\dfrac{n-1}{m-2})\\]

Similarly, for (\ref{4}), we obtain:

\\[1>\sum_{k=m+1}^{n}\dfrac{1}{k-1}=\sum_{k=m}^{n-1}\dfrac{1}{k}=\sum_{k=1}^{n-1}\dfrac{1}{k}-\sum_{k=1}^{m-1}\dfrac{1}{k}\approx\ln(\dfrac{n-1}{m-1})\\]

Alright, almost done! Notice that we can make another approximation of these results for large $ n $.

For sufficiently large $ n $, the constants in our expressions will make negligible difference in our final result, allowing us to make the following claim:

\\[1\approx\ln(\dfrac{n}{m})\\]

Now, using the properties of natural logarithm, value of $e$ and then taking it’s inverse, we get:

\\[\boxed{(\dfrac{m}{n})\approx(\dfrac{1}{e})\approx 0.37}\\]

_Q.E.D._

This result was proven through a lot of (good) approximations, but other more rigorous methods including those used in optimization come to the same result.

So here we have it! A proof of why you should keep $37\%$ on your mind when it comes to matters of making choices.