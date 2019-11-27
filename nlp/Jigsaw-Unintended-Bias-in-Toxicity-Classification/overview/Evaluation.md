# Jigsaw Unintended Bias in Toxicity Classification

> Detect toxicity across a diverse range of conversations



## Evaluation

### Competition Evaluation

This competition will use a newly developed metric that combines several submetrics to balance overall performance with various aspects of unintended bias.

First, we'll define each submetric.



### Overall AUC

This is the ROC-AUC for the full evaluation set.



### Bias AUCs

To measure unintended bias, we again calculate the ROC-AUC, this time on three specific subsets of the test set for each identity, each capturing a different aspect of unintended bias. You can learn more about these metrics in Conversation AI's recent paper *[Nuanced Metrics for Measuring Unintended Bias with Real Data in Text Classification](https://arxiv.org/abs/1903.04561)*.



#### Subgroup AUC

Here, we restrict the data set to only the examples that mention the specific identity subgroup. *A low value in this metric means the model does a poor job of distinguishing between toxic and non-toxic comments that mention the identity*.

$\rightarrow$ 값이 클수록 구별 작업을 제대로 못했다



#### BPSN (Background Positive, Subgroup Negative) AUC

Here, we restrict the test set to the non-toxic examples that mention the identity and the toxic examples that do not. *A low value in this metric means that the model confuses non-toxic examples that mention the identity with toxic examples that do not*, likely meaning that the model predicts higher toxicity scores than it should for non-toxic examples mentioning the identity.

$\rightarrow$ 값이 작을수록 identity를 언급하는 정상(non-toxic) 예제와 그렇지 않은 악성(toxic) 예제를 혼동한다는 것을 의미



#### BNSP (Background Negative, Subgroup Positive) AUC

Here, we restrict the test set to the toxic examples that mention the identity and the non-toxic examples that do not. *A low value here means that the model confuses toxic examples that mention the identity with non-toxic examples that do not*, likely meaning that the model predicts lower toxicity scores than it should for toxic examples mentioning the identity.

$\rightarrow$ 값이 작을수록 identity에 대해 언급하는 악성(toxic) 예제와 그렇지 않은 정상(non-toxic) 예제를 혼동한다는 것을 의미



### Generalized Mean of Bias AUCs

To combine the per-identity Bias AUCs into one overall measure, we calculate their generalized mean as defined below:
$$
M_p \left(m_s\right) = \left({1 \over N} \sum_{s=1}^N m^p_s \right)^{1 \over p}
$$
where:

$M_p$ = the $p$ th power-mean function

$m_s$ = the bias metric $m$ calculated for subgroup $s$

$N$ = number of identity subgroups

For this competition, we use a $p$ value -5 to encourage competitors to improve the model for the identity subgroups with the lowest model performance.



### Final Metric

We combine the overall AUC with the generalized mean of Bias AUCs to calculate the final model score:
$$
score = w_0 AUC_{overall} + \sum_{a=1}^A w_a M_p \left(m_{s,a}\right)
$$
where:

$A$ = number of submetrics (3)

$m_{s,a}$ = bias metric for identity subgroup $s$ using submetric $a$

$w_a$ = a weighting for the relative importance of each submetric; all four $w$ values set to 0.25



**While the leaderboard will be determined by this single number, we highly recommend looking at the individual submetric results, [as shown in this kernel](<https://www.kaggle.com/dborkan/benchmark-kernel>), to guide you as you develop your models.**



### Submission File

```
id,prediction
7000000,0.0
7000001,0.0
etc.
```

