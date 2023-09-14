# A/B Test Results Analysis
 In this document, the results of an A/B test run by an e-commerce website will be presented ana analyzed. The target of this analysis is to help the company take any of the following actions:
* Implement the new webpage,
* Keep the old webpage, or
* Perhaps run the experiment longer to make their decision.


Here is the description of the used data:
| **Data columns** |                                                                                                                                                                                                                                                                                                                           **Purpose** |         **Valid values** |
|-----------------:|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|-------------------------:|
|          user_id |                                                                                                                                                                                                                                                                                                                             Unique ID |             Int64 values |
|        timestamp |                                                                                                                                                                                                                                                                                          Time stamp when the user visited the webpage |                        - |
|            group | In the current A/B experiment, the users are categorized into two broad groups. The control group users are expected to be served with old_page; and treatment group users are matched with the new_page. However, **some inaccurate** rows are present in the initial data, such as a control group user is matched with a new_page. | ['control', 'treatment'] |
|     landing_page |                                                                                                                                                                                                                                                                           It denotes whether the user visited the old or new webpage. | ['old_page', 'new_page'] |
|        converted |                                                                                                                                                                                                                 It denotes whether the user decided to pay for the company's product. Here, 1 means yes, the user bought the product. |                   [0, 1] |

## Null Hypothesis  𝐻0 Testing
The decision will be based on the Null Hypothesis testing. The main rule here is:
```
𝐻0 =  𝑃𝑛𝑒𝑤 -  𝑃𝑜𝑙𝑑 <= 0
𝐻1 =  𝑃𝑛𝑒w-  𝑃𝑜𝑙𝑑 > 0
```
The hypothesis here are stated in terms of $p_{old}$ and  $p_{new}$ , which are the "converted" probability (or rate) for the old and new pages respectively.

* Here are the steps that will be taken in this test:
    - Simulate (bootstrap) sample data set for both groups, and compute the  "converted" probability $p$ for those samples. 
    - Use a sample size for each group equal to the ones in the `df2` data.
    - Compute the difference in the "converted" probability for the two samples above. 
    - Perform the sampling distribution for the "difference in the converted probability" between the two simulated-samples over 10,000 iterations; and calculate an estimate.
 
## Final result 
After taking the mentioned steps, the results in dicate that ***the new page did not make much impact*** compared to the old one.
