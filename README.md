# Neuromatch-24
---
Group name: Resourceful Orchid from the pod Oak	Contact name: Apollo Yang	
Contact email: yanghuaihou@outlook.com
Dataset: IBL dataset
Members: Chinmay Sharma, Apollo Yang,

## To Do
---
Implement Logistic Regression on the Dataset
Peruse the newest IBL documentation
Complete the method rereview and come up with the testing procedure
Finish abstract writing on W2D5
Hard DDL: Get our results and graph on W3D3
Work on the presentation outline
Rehearse the presentation on W3D4/W3D5 morning


## Modelling steps (for our reference)
---
Step 1: Identify the Phenomenon to be modelled
Motivation: Why can’t all mouse decision making be modelled with a simple psychometric curve?
Evaluation Method: Fitting a model to the mice decision making data
Ideas: HMMs, GLM-HMMs, CNNs (to account for the fact that the decision at a time t may be affected by conditions from a window of time before that).

Our evaluation would be good if we can fit the data to a significant degree of accuracy and also explain our results mechanistically/intuitively.

Step 2: Literature review
Queries/Current Problems:
How do we standardise inputs for our GLM across different training protocols?
Theoretical Models of Mental “Cost”
Do mice exhibit time dependency?

Ashwood 2021 2nd last paragraph “Another promising direction will be to replace the model's fixed transition matrix with a GLM so as to allow external covariates to modulate the probability of state changes, This would allow us to identify the factors that influences state changes (for example, a preponderance of unrewarded choices) and, potentially, seek to control such transitions.”

Roy 2021: "Of course, by incorporating weights on additional task covariates (e.g., choice and reward history), the model can characterise time-varying strategies that are more complex than those captured by a simple psychometric curve."

Gupta 2024: "In this work, we explore the idea that history biases reflect a misbelief about non-stationarity in the world, and demonstrate that normative decision-making under such beliefs gives rise to choices that are both history-dependent and appear to be evidence independent (i.e. akin to lapses). This corresponds to an accumulation to bound process with a history dependent initial state... Despite heterogeneity in history biases and lapse rates in this population, we show that a substantial fraction of lapses can be explained by the presence of history dependence during evidence accumulation."

Step 3: What aspects of our data need modelling: 
The choices of mice as the outcome measures serially in time
The signed contrast (intensity)
Training period (length)

Step 4: Hypothesis in mathematical form

Step 5: Selecting the toolkit

Step 6: Planning/ drafting the model

Step 7: Implementing the model

Step 8: Completing the model 

Step 9: Testing and evaluating the model (our project stops here)

Step 10: Publishing the model

## Project Proposal
---
The project aims to study the decision making in mice using the IBL dataset which contains data of different subject mice from different laboratories made to undergo the 2AFC task.

It is observed in this dataset, a simple psychometric curve fixed throughout the trial is not sufficient in explaining the behavioural variation throughout the trial and learning. Therefore, several researchers have taken different modelling approaches (such as the HMM-GLM and PsyTrack package) based on the existing Bernoulli-GLM by introducing hyperparameters tuning the shape of the psychometric curves to better fit the data. However, these methods have their shortcoming being unable to account for the mice subject’s progressive update in light of the trial-history information. The HMM transition matrix, for example, exhibits the memoryless property and is unable to factor in the past data, while the optimisation method used in PsyTrack is a “global” method, by finding the minimum of the data in an entire period instead of updating progressively. Both authors have mentioned the possible extension of their model to account for the “external covariates” such as “choice and reward history” (Ashwood; Roy). Such that the psychometric curve can capture more complex and nuanced mice behaviours. 

This led us to our research question: “Does the trial-history bias play a role in accounting for the difference in the decision-making behaviour in the mice 2AFC task, in particular quantified by the accuracy of fit of the psychometric curve to a logistic regression for different mice?”

In their research by Gupta, et al., 2024, the team focuses on the trial-history biases as the explanatory mechanism of the apparent lapses. The group devised an “accumulator” to factor in the historical choices in the parameters governing the shape of the psychometric curve. 

We hypothesise that the trial-history bias plays a role in mice’s behaviour, specifically:
“Difference in training period contributes to the history biases in some mice despite meeting criteria”.
“The error rates (number of correct/incorrect choices) of the mice’s past performances affect how likely they will adhere to their existing strategy or change.”
The trial-history will be introduced as a modification of the GLM model with the form of time integration.

## Abstract
---
The trial-history bias is the influence of the previous trial outcomes on the decision-making processes during subsequent trials. This study investigates the role of trial-history bias in mice decision-making using the International Brain Laboratory (IBL) dataset that includes data from multiple labs on the Two Alternatives Forced Choice (2AFC) task, in which mice must make the binary choice depending on the visual cues of varying light intensities in order to receive water rewards. Traditional psychometric curves fail to account for behavioural variations observed during trials and learning phases. Previous studies have indicated that such biases can reflect a misbelief about non-stationarity, leading to history-dependent choices. To address this, we proposed a linearised model incorporating trial-history biases. The model aims to capture these biases by introducing historical performance data and other task variables such as the intensity of light cues and left-right probability bias. The Principle Component Analysis (PCA) is employed for dimensionality reduction and lasso regression to ensure model sparsity. The goal is to achieve a balance between interpretability and expressiveness of our model, providing a nuanced understanding of mice decision-making behaviours and capturing the rich time-dependency that is being ellipsed in previous studies.


## Abstract ver.2 with feedback
---
The trial-history bias is the influence of the previous trial outcomes on the decision-making processes during subsequent trials. Previous studies have indicated that such biases can reflect a misbelief about non-stationarity, leading to history-dependent choices. However, in the experiment where mice have to make binary decisions based on external cues, models often neglect the history-dependent aspect due to the static and globally sampling nature of the curve-fitting and the optimisation procedures employed. As a result, researchers still do not fully understand the effect of previous trials on current trial performance. This study investigates the role of trial-history bias in mice decision-making using the International Brain Laboratory (IBL) dataset that includes data from multiple labs of mice performing the above task.

Here, we proposed a linear model that incorporates trial-history biases. The model aims to capture these biases by introducing historical performance data and other task variables such as the intensity of light cues and left-right probability bias. The Principle Component Analysis (PCA) is employed for dimensionality reduction. Then, we further applied the lasso regression to capture the features underlying the decision making process while ensuring model interpretability through the applied sparsity. We found weak correlations between the trial history and the mice current choice in the first 5 lagging windows. And in some mice, this relation is negative. In general, shorter training corresponds to more pronounced correlation between the choice and trial history. This combination between exploration in the latent space and linear regression provides a nuanced understanding of mice decision-making behaviours and captures the rich time-dependency that is being ellipsed in previous studies.

