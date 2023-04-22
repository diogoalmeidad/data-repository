## Minimum Detectable Effect (MDE): 
Used to calculate the sample size - experiment owners need to estimate what is the percentage uplift that they expect the experiment to have 

## [Markov Chains](https://blog.developer.adobe.com/understand-marketing-channel-effectiveness-using-hidden-markov-model-for-conversions-in-adobe-170592032fb6): 
- What is it: Assigns probability from moving from one state to the other.
- In Marketing context: It makes a prediction on the propensity to convert as the individual visitor transitions to various campaigns/channels over time. It looks into the paths that led to the conversion to assess the contribution of the channel/campaign and use the 'removal effect' to understand the effect of removing a touchpoint has on conversions.
- Outcome: This allows to understand transition probabilities and then each touchpoint gets assigned a percentage of conversion based on the transition probability.
- Observable variables = sales | not sales 
- Hidden variables = channels
