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

Participants had slightly lower performance ratings on average relative to non-participants (3.12 vs 3.16), but being lower levels and R&D it is possible these groups had lower ratings to begin with and performance actually increased due to participation. We will attempt to tease out the true relationships using matching.

As expected with a training targeting early career employees, participants were younger and had less experience than participants.

![unnamed-chunk-5-1](https://github.com/user-attachments/assets/f6b56ed0-1cfb-498e-a675-6039b5d7d977)

R&D employeees indexed higher on education than other employees and our lower job levels is born out in the data.

![unnamed-chunk-6-1](https://github.com/user-attachments/assets/7715a865-d15a-4543-9807-f83403147c9c)

Participants were also more likely to be female than non-particpants, perhaps related to R%D roles relative to other departments, but also possiblly having to do with likelihood of opting in for more training.

![unnamed-chunk-7-1](https://github.com/user-attachments/assets/3d920760-fdfb-442a-9f4c-0a13bf7ff549)

Matching Types

- Exact Matching: with our set of variables only 5 parcipant observations got matches.
- Coarsened Exact Matching (CEM): a defautl model improved to 34 of 185 participants getting matches. With some extra specification in binning of the continuous variables we improve to 177 of 185 participants getting matches and those matches do a very good job at minimizing the standardized mean difference across variables.
  ![unnamed-chunk-14-1](https://github.com/user-attachments/assets/e3f49a1c-dcbc-4e61-9869-17be8c995cea)

- Propensity Score Matching (PSM): A default model gets matches for every participant, but the quality of matches is slightly worst than our CEM model with cutom binning.
![unnamed-chunk-16-1](https://github.com/user-attachments/assets/4404d5d3-96a3-4415-9573-daa88a9b7f7e)

- Exact + PSM: A model using exact binning to create strata and PSM to assign matches within strata retains all participant observations and slighly outperforms our CEM model. By altering the PSM matching method and the link function for the propensity model we improve the match qualitiy slightly again.
  
![unnamed-chunk-18-1](https://github.com/user-attachments/assets/2700c941-dd74-42f7-9c47-0d9a928b526d)

Our final matching specification does well at minimizing the distance between participant and non-participant lines/distributions along our variables.

![unnamed-chunk-19-2](https://github.com/user-attachments/assets/bd2aa612-cc94-4b03-90e6-2605363ccd4f)
![unnamed-chunk-19-3](https://github.com/user-attachments/assets/d5f76f82-6231-4261-aa85-a875a4f8d05b)
![unnamed-chunk-19-4](https://github.com/user-attachments/assets/6c1545b8-dde1-4999-8211-ef7571103d11)

Estimate Marginal Effects

With

Limitations
