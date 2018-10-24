---
layout: "post"
title: "Bayes Theorem"
date: "2018-10-24 13:05"
author: Jiayun
---
{% include mathjax.html %}
### Conditional Probability and some useful formulas
The conditional probability of B given A is:<br><br>
$$P(A|B)=\frac{P(A\cap B)}{P(B)}$$ <br><br>
thus<br><br>
$$P(A\cap B)=P(A|B)*P(B)$$ <br><br>
and the bayes'rule: <br><br>
$$P(B|A)\ =\ \frac{P(A\cap B)}{P(A)}\ =\ \frac{P(A|B)*P(B)}{P(A)}$$

### Prior probability, posterior probability and likelihood
Consider we are making dinner and we are going to cook a fish. There are different **approaches** to cook the fish: **steam** and **pan-sear**. As a result of cooking, there may be two different **outcomes**: the final dish may be delicious or horrible (different individual varies in different cooking skills!).

![delicious](/myblog/assets/fish_1.jpg){:height="40%" width="40%"}![delicious](/myblog/assets/fish_2.jpg){:height="20%" width="35%"}

Below are the **likelihood** given for different conditions. <br><br>
$$L(Outcome|Approach)$$ = $$P(Outcome|Approach)$$ <br><br>

| Approach | Outcome |
|:---:|:---:|
| steam  | 70% delicious, 30% horrible |
| pan-sear | 80% delicious, 20% horrible  |

And in general, let us assume that the chances of outcomes are 50/50, which means the **Prior probabilities** are: <br><br>
$$P(delicious)\ =\ 0.5$$ and $$P(horrible)\ =\ 0.5$$<br><br>
Now the guest Bob is served with a poorly cooked fish (horrible outcome), what is the probability of that Alice pan-seared the fish? The probability we are looking for is<br><br>
$$P(pan-sear|horrible)$$.<br><br>
This is the **posterior probability** - given the result, we try to find the reasons (or approaches) that caused this result.
According to Bayes' rule, <br><br>
$$P(pan-sear|horrible)$$ = $$\frac{P(horrible|pan-sear)}{P(horrible)}$$ = $$\frac{0.2}{0.5}$$ = $$0.4$$ <br><br>
So, Bob knows that there are a 40% chance that Alice pan-seared the horrible fish.
