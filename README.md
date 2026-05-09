# logistic-injury-prediction-modeling

Note: this is part of a paper I wrote "Using Logistic Modeling to Improve Player Injury Predictions in the English Premier League" which started out as my Math50 project last term


## Background and Motivation

Predicting player injuries is one of the most biggest challenges in elite football analytics. Professional clubs collect workload, recovery, and GPS-based tracking data on every player and session, hoping to help inform which players are most likely to get hurt and when. Modern analytics literature has responded by reaching for increasingly complex tools such gradient boosting, random forests, deep neural networks, under the assumption that more sophisticated models will yield better predictions. But in a domain where model outputs inform high-stakes decisions about human bodies, predictive accuracy is not the only thing that matters. Interpretability is a key piece that matters as well.

This project investigates a question the intersection of these concerns: can a well-specified logistic regression model, incorporating domain-informed nonlinear and interaction terms, achieve predictive performance comparable to ensemble methods reported in the literature on EPL injury prediction? And if so, what does this imply for the interpretability-performance tradeoff in applied sports analytics?

The motivation for this question comes from Chang et al.'s "Football Analytics: Assessing the Correlation between Workload, Injury and Performance of Football Players in the English Premier League" (2024). The authors apply gradient boosting, random forest, and decision tree models to EPL tracking data, achieving AUC values in the range of 0.69–0.72. Their results highlight an important pattern that often gets glossed over which is that returns to model sophistication diminish quickly. The performance gap between their simplest and most complex specifications is modest, and all of their models operate as effective black boxes. They are capable of producing risk scores but not of explaining, in terms a medical staff can act on, why a given player is flagged.

This matters because injury prediction in elite sport is not a pure prediction problem. It is a decision-support problem. When a model identifies a player as high-risk, the question that immediately follows from coaches and medical staff is why. Should training load be reduced? Is recovery the issue? Is the schedule the problem? An XGBoost feature importance plot or a SHAP value can attempt at answers, but a logistic regression coefficient, expressed as an odds ratio, can give one directly. (For example an additional match in the prior seven days raises injury odds by approximately 23%). These are numbers a performance scientist can integrate into workload-management decisions whereas a black-box risk score is not.

Given this, the goal of this paper is to test whether a simpler probabilistic model can approach the predictive power of more computationally intensive algorithms while preserving the interpretability that applied practitioners require.
