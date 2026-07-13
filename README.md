**Objective**

Develop a risk scoring model for auto insurance policies estimate the probability that a policy will experience at least one claim.



**Approach**

I reviewed the dataset and the prototype code. Figured out some improvements:

1\. Removed target leakage variables containing post-claim information.

2\. Filled NaNs with median values, not zero values.

3\. Replaced random train/test split with time-based split.

4\. Added ROC-AUC and PR-AUC metrics on top of the accuracy.

5\. Added normalization to business\_type casing (Trucking, TRUCKING, trucking) as it was inconsistent in the data.

6\. Used reasonable and usable columns.

7\. Experimented with RandomForestClassifier and HistGradientBoostingClassifier to enhance the results.



**Target Definition**

target = (claim\_count > 0).astype(int)

where

0 = no claim

1 = at least one claim

The final risk score represents the predicted probability of at least one future claim.



**Validation Approach**

time-based validation strategy was used

Training data: 2020–2021

Validation data: 2022

Scoring data: 2023–2024



**Final model**

the final model is the Logistic Regression which was enhanced by scaling and NaN values filled with median values. To run the solution, simply put the 2 excel files in the same folder as the script named risk\_scorer.ipnyb and run the script.



**Known Limitations And Trade-Offs**

Limited Data Volume - The dataset contains approximately 15,000 historical policies, which limits the complexity of models that can be reliably trained.

Used features - some of the features should have been selected in the feature selection, and some of them should have been deleted. Additional features may improve performance.

Categorical Encoding - current implementation uses category codes. A production-grade implementation would use a more robust encoding strategy.

No External Data Sources - The model relies only on the provided dataset and does not use potentially valuable external information.

No Production Monitoring - Model monitoring, drift detection, model versioning, and CI/CD deployment were identified as future production roadmap items and were not implemented in this case study.



**AI tools** used in working at this study case were Copilot to help me find more patterns, inconsistencies that were found by me. To explain some financial word definitions and check the completion of all the tasks given. Claude code was used to fix the code bugs after the copilot as it is the better tool for this. GitHub Copilot to write comments in the code.

