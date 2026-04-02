## Statistical Capstone Collaboration with VolleyStation
# Project Contributors:
Sydney Stanton, Ethan Leap,  Chase Meining, Rishi Nair

# Project Overview 
This study presented an approach to predict rally and set win probabilities in volleyball by
integrating a generalized additive model (GAM) with a Markov chain simulation. Prior studies have
used only men’s or professional volleyball data, whereas this study focused on women’s collegiate
volleyball data from the University of Colorado Boulder (CU). Our research quantified patterns
previously based solely on intuition to inform evidence-based strategies in collegiate volleyball.
We implemented a GAM to predict rally win probabilities, then fed them into our Markov chain
simulation to output set win probabilities from CU’s perspective. The components of our modeling
captured the effects of the serving team and score differential. Our results demonstrated that this
integrated approach improves probability accuracy in women’s collegiate volleyball compared to
past research. The findings underscored the effectiveness of our probability tree visualization in
enhancing in-game coaching by providing data-driven insights into win probabilities across different
match scores.

# Code Implementation 

# Final Results Summary 
To evaluate the performance of our proposed model, we first compared our logistic regression to our GAM. Both models were built into the Markov chain framework to calculate point-by-point transition probabilities and overall set win probabilities. The logistic regression served as a baseline model, whereas the GAM provided a more flexible model that could capture the nonlinear effects of score difference and serving status. Because of that flexibility, we opted to use the GAM in our final
Markov chain. To prevent overfitting at extreme values, we clamped the Markov chain at a score differential of ±12. For example, if CU leads by 15, we instead use the transition state when CU leads by 12 to avoid instances where there aren’t enough data points at a given score differential, since the model would not return a confident prediction. Therefore, Fig. 3 displays all predicted win
probabilities in the score differential threshold range compared with empirical values, differentiating by which team is serving. The size of the points on the plot represents the number of observations at each score differential in the dataset.

Across both models, the predicted win probabilities were very similar, showing that the model is stable and that the score differential and serving team are strong predictors of rally outcomes.

The deuce band is scores that are around 22–30 points for both teams. These late rallies are highly decisive, making large impacts on set win outcomes. At the start of the set, CU’s chance of winning the set was about 51–54%, depending on who served first. When CU was the team to serve first, the logistic regression model estimated a probability of winning of about 0.510, while the GAM estimated 0.517. When the opponent served, the probabilities were slightly higher (around 0.535–0.542), reflecting the slight advantage in women’s collegiate volleyball that comes with receiving.
In late-set situations, the model showed steep shifts in win probability. At a score of 24–23 and CU serve, CU’s chance of winning was roughly 0.74, increasing to 0.82 when the opponent served at the same score. When CU trails 23–24, the win probability dropped to 0.19 0.28, showing how one point near the end of a set can completely swing the expected outcome of a set. In near-deuce situations—scores tied late in a set, such as 23–23—both models showed win probabilities close
to 50%, meaning the outcome could go either way. As soon as one team gained a slight two-point advantage (e.g., 24–22), the predicted chance of winning the set rose sharply to around 90%, reflecting how decisive late rallies become in determining win probability. Overall, the GAM’s predictions differed by less than one percentage point from the logistic model’s predictions, confirming that both methods capture the same underlying trends. The logistic model provides a simpler interpretation, while the GAM produces smoother transitions near close scores. Together, they accurately show how serving and score progression shape live set win probabilities. 

# Conclusion
Ultimately, our study was set out to understand how win probabilities shift throughout a women’s collegiate volleyball set, and we found that they are largely driven by two main factors: score differential and serving team. We did this by using a GAM for rally-win-level prob
abilities and a Markov chain for set-win probabilities. Throughout the score states, we showed that rallies late in the set produced steep swings in set probabilities. We formally confirmed the existence of these high-leverage rally scores in the deuce band, demonstrating that a single rally could change CU’s set win probability by 30–40 percentage points. In contrast, earlier states had much smaller leverage. By clustering states into tiers of probability swing, we also demonstrated that score states can be grouped into a handful of meaningful rally importance zones, rather
than being treated individually for greater and quicker interpretability. Overall, our GAM-driven Markov chain provides a coherent, CU-specific map of how win probabilities evolve within a set, and the same framework can be applied to other teams to support more data-driven coaching and in-game decision-making in the future.


