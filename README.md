![title](/Documents/images/Banner.png)

# Problem Statment

With the amount of data and technology at our fingertips we have the ability to build a proactive healthcare system instead of a reactive healthcare system. Saving time, money, energy, and heartache we can use this to help predict and detect early sign of disease. The goal of this project is to build a predictive model to classify patient diagnosed with dementia hospital patients using routine EHR data from the MIMCIII database. The main objective is to understand what differentiates patients diagnosed with dementia from those who are not. 

## Background info

Dementia is a general term for a decline in mental ability severe enough to interfere with daily life. Memory loss is an example. Dementia is not a specific disease. It’s an overall term that describes a group of symptoms associated with a decline in memory or other thinking skills severe enough to reduce a person’s ability to perform everyday activities.

Diagnosis of dementia: There is no one test to determine if someone has dementia. Doctors diagnose Alzheimer’s and other types of dementia based on a careful medical history, a physical examination, laboratory tests, and the characteristic changes in thinking, day-to-day function and behavior associated with each type. Doctors can determine that a person has dementia with a high level of certainty. But without symptoms this diagnosis increases in difficulty.

## Data
For this project the dataset being used was acquired through the MIMIC III database from PhysioNet. The database includes information such as demographics, vital sign measurements made at the bedside (~1 data point per hour), laboratory test results, procedures, medications, caregiver notes, imaging reports, and mortality (both in and out of hospital).


## Challenges
The dataset presented a number of challenges. In initial steps the challenges included handling a large database of encoded medical terms. The process done to extract the data was done in google cloud big query. The second challenge is common in most health data records, missing values. How to handle missing values was a major consideration when data cleaning. Lastly the biggest challenge is accounting for imbalanced data. The data had a major imbalance with the patients who were not diagnosed with dementia as the majority class. 

## Missing Values
Missing value methods for mean, median, and KNN were explored. Based on the descriptive statistics and change in distribution skewness the KNN imputation was used to fill missing values. 

![title](/Documents/images/Missingvalues.png)


## Class Imbalance
Several methods were explored against a baseline mode. The two methods that performed the best were Tomek Links and Neighborhood Cleaning Rule. 




## Modeling
![title](/Documents/images/Dementia_baseline2.2.png)

![title](/Documents/images/dementia1confusionMatrix.png)




## Conclusion
Feature that stood out were age, indicating that the most common difference that all dementia patients had was their age demographic. Other lab test that indicate varying levels of blood counts were also features that stood out. 
The final models were by no means the best model there are many more next steps that could be considered to improve this project.

![title](/Documents/images/features1.png)


## Next steps:
Finding more balanced data
Further model exploration
Data regarding physical examination 
MRI and ECG scans could be used to add to the feature set 