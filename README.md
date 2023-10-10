## Analyzing Car Crash Data from The Chicago Data Portal

## Overview

This project involves the comprehensive task of identifying a target variable from a dataset with 50 columns and then finding predictor variables that are influencing the target variable. To reach this goal, data was exported from the Chicago Data Portal and then loaded into Python. Then, by sorting through unique items of each column, it was possible to identify a strong target variable and predictor variables. These variables were plugged into an initial baseline Logistic Regression model and then adjusted based on how many of the variables were statistically signficiant. 

## Business Objective 

The findings of this study are being presented to stakeholders at an Insurance Company based in Chicago. The problem this Insurance company is having is that they're spending extra money covering accidents where there were no injuries and the cars aren't in need of a tow truck. In an effort to save more money they'd like to gain a better understanding of what's influencing accidents with No Serious Injuries. Then they can use this information to allocate funds more efficiently. 

## Data Understanding and Analysis

The first step in this process was to go through the 50 columns of data and get a sense of the value counts to see how many unique items were in each column. Through this process the Crash Type column was a clear target variable that would be informative because it is classified as either resulting in a Non-Injury(0) or an Injury(1). At first, the Non-Injury and Injury categories were object variables so it was necessary to use a label encoder to covert the object to that numeric value of 0 or 1. With other columns as predictors of the impact on this target Injury column I felt confident that stakeholders would find this study useful in an effort to be more effficent and save money. 

The second step was to identify predictor variables. The predictor columns selected were based on how informative it would be to explaining the severity of an accident. Weather Condition, for example, was selected because accidents on a clear day are probably less likely to result in injuries compared to rainy or snowy/icy conditions. The other 15 predictor columns selected were Lighting Condition, Trafficway Type, First Crash Type, Device Condition, Damage, Primary Cont Cause, Posted Speed Limit, Crash Month, Crash Day, Crash Hour, Surface Condition, Street Number, Street Direction, and Beat of Occurance. There were also additional Injury variables that were added in an effort to strengthen the accuracy of the study. 

The third step was to balance the dataset. This was required since the number of Injured far outweighted the number with No Injury. The iloc function was used to balance the dataset and then concat to merge the datasets together for each value of 0 or 1. 

The fourth step was to do a train test split of the data once the data was balanced. 

The fifth step was to OneHot Encode the object variables from the train dataset so that each value of each column has a value of 0 or 1. That was then merged with a numbers dataframe for numeric variables using concat. The same was done to the test dataset, however, instead of using OneHot Enocode the transform function was used on the test dataset.

The sixth step was to run and fit the logistic regression model. The resulting score was around 0.50 or 50% so the initial observation is that the predictive variables are not having a signficant effect on our target variable. Then y hat train and test variables were created for a residual variable that generates the absolute value of the y hat train subtracted from the y-train. This shows the abosolute value. 

A hyperparameter for loop was created for logistic regression models with a c value that increased in increments of a 10th power (ie. 0.1,1,10,100,10000). The results did not show drastic increases for accuracy. The accuracy was also lower than what is considered to be ideal at around 0.45-0.46. Some of the factors that might have contributed to this result from the data is that there are several object variables or columns that have high levels of unique values making it difficult to incorporate into a train test split function. 

Cross Validation and decision trees were also used and the resulting accuracy was around 50%. This was not the most ideal outcome, however, if more predictive variables were used and NaN values were filled for those variables it could have strengthened the results. 


## Dropped Columns

Several columns were dropped for this study. Of the 50, 28 were used so the other 22 were dropped. A lot of these columns had signficant levels of Nan values that would weaken the reliability of the study. The columns also were not deemed as informative to what might or might not result in such as if the accident occured in a work zone or not. There were several columns with Nan values that were used.



## Predictive Findings and Recommendations

The initial and conclusive predictive findings were that the accuracy level driven by all models for this study were not making the accuracy higher than 50%. This includes the initial baseline regression model, hyperparameter models genenrated from a for loop, cross validation, and decision trees. 

One thing that is important for any data driven study is to focus on what could further strengthen the measures being tested for. Therefore, my primary recommendation to the stakeholders would be that more work is needed on the predictive variables to drive the accuracy levels higher. That would entail working with columns that have signifcant number of NAs and either filling those NAs with other values based on frequency or the mean. One problem I also found was that some object variables had too many unique values so it wasn't possible to generate a train test split because jupyter would freeze up. 

Other than that, you could select a different target variable that the predictive variables would have a greater impact on. The ultimate recommendation is that furthering the study would strengthen the conclusion reached that the predictive variables aren't impacting the target variable. It's very possible that adding in more predictive variables such as Location or Zipcodes would make a drastic difference. However, with so many unique values it becomes challenging to plug all of the unique values into a train test split. Overcoming that hurdle would strengthen the study as long as the split results in an accuracy that is higher and closer to a 70-90 range. 
