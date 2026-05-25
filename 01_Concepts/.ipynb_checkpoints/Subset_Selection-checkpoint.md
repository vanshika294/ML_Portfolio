## what is subset selection?
Subset selection means selecting a subset of input variables (features) to build the model, instead of using all available variables.

## Why do we even do this?
We do subset selection:
- To improve how well the model generalizes to new data by using only the most useful input variables.
- To reduce overfitting: fewer features → simpler model → better performance on new data
- To remove irrelevant features: eliminates noise that does not help prediction
- To remove redundant features: avoids duplication of information
- To improve model accuracy (generalization): focuses on truly useful inputs
- To make the model simpler and interpretable: easier to understand and explain
- To reduce computational cost: faster training and prediction

## Types of subset selction
**1. Best subset selection:** In this we try every possible combination of predictors and pick best one.
 for instance if we've 3 features x1,x2,x3 :
- we try building model using x1.
- Model with x2.
- Model with x3.
- Model with x1,x2.
- Model with x1,x3.
- Model with x2,x3.
- Model with x1,x2,x3
- Essentially, we try all the possible combinations of features and choose a model that performs best.
> Problem with this is that if we've 20 features, there would be over 1 million combinations. So this becomes computationally expensive.

**2. Forward selection:** start with no features, add one by one.
Steps:
- Start with empty model
- Add the feature that improves model most
- Keep adding until no improvement
- Faster than best subset
> Problem: omce u add a variable,you usually don't remove it. So, it might miss better combinations.

**3. Backward Selection:** Start with all features, remove one by one.
Steps:
- Start with all features
- Remove the least useful feature
- Repeat
- Works well when: number of features is small

**4. Stepwise Selection (Hybrid):** Combination of forward + backward
Idea:
- Add features (like forward)
- But also remove if they become useless
-  More flexible

