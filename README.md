# program-evaluation-with-matching

## Project Overview: Program evaluation without random assignment (with matching)

Walk through of a hypothetical program evaluation, where we evaluate training program's effect on performance, where participation was not randomized and matching is used to control for differences between participants and non-participants.

- Utilized a kaggle sample dataset for attrition analysis from ibm to mirror real employee data relationships
- Simulated participation in the program
- Explored differences between participant group and non-participant population
- Attempted and evaluated different types of matching specifications
- Obtained matches using our best matching specs
- Esimated marginal effect of particpation on performance
- Brief explanation on limitations of matching

Sources
[kaggle ibm attrition dataset](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)
[getting started with matchit](https://cran.r-project.org/web/packages/MatchIt/vignettes/MatchIt.html)
[matching methods](https://cran.r-project.org/web/packages/MatchIt/vignettes/matching-methods.html#coarsened-exact-matching-method-cem)

Data Simulation
IBM attrition dataset has a feature called 'TrainingTimesLastYear'. To keep any inherent relatinoships in the data I used this feature to create a training participation flag. If you attented a training more than 4 times last year ( use that as a signal that this person is likely to opt into a training program if they were invited. To similuate the invitation, I decided this particular training was of most benefit to early career R&D employees and restricted the flag to turn on only for these groups (Job level 1-3, dept = R&D).

Exploratory Group Differences

![unnamed-chunk-5-1](https://github.com/user-attachments/assets/f6b56ed0-1cfb-498e-a675-6039b5d7d977)


Matching Types

Estimate Marginal Effects

Limitations
