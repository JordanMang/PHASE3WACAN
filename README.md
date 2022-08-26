# Washington Community Action Network
### Predictive Model of Arrests following Terry Stops

## Project Overview:
The Washington Community Action Network has asked me to explore how Terry Stops, a form of police traffic stop that only requires detection of "suspicious' behavior to conduct, negatively impacts minority communities. WCAN hopes that through the creation of a predictive model that they can develop an app to combat disproportionate arrests in the minority community. Along with this predictive model they have asked me to do some EDA as well as provide actionable next steps for refining this model.

When viewing the Jupyter Notebooks please note the the first notebook includes the exploration of my baseline model, the second notebook uses more advanced algorithms and the third notebook utalizes a revised set of arrest data  to verify the functionality of the models and well as some EDA.

## Business and Data Understanding:
WCAN does not currently have its own dataset of Terry Stops and the only publically avaiable dataset is provided by the Seattle Police Department. There are many limitations to this dataset but mostly it will be used as a starting point and a way of understanding what features will be important to include in their round of data gathering. 

It is important to understand that their proposed app would be downloaded by consumers, a short survery would be taken and then if they were to be pulled over the information provided and gathered would be run through the predictive model to detect the likelihood of an arrest. If that likelihood of arrest is high a volunteer lawyer would be dispatched to mediate the scenario. 

After cleaning the dataset and eleminating features that were irrelevent or had high multicolinearity I was left with ten features. Of these ten features the most noteable were, Officer race and gender, subject race and gender, time of terry stop and location of the stop. All of the features were categorical. It should be fairly obvious that from the limited scope of these features the creation of a predictive model was destined to underperform.

## Modeling:
Although my model failed to perform better than the baseline model there were many insights to be gained which will be discussed after a quick look into what models I ran and an explaination of some of my steps in attempting to troubleshoot it.

### Dummy Model (Baseline):

![Dummy.png](https://github.com/JordanMang/PHASE3WACAN/blob/main/Image/Dummy.png)

From my baseline model you can see that the dataset is fairly imbalanced and that most of my models will be deceptively accurate. To combat this I created some Synthetic data through the use of SMOTEN.

### Logistic Regression (Basic):

![Logistic%20Regression.png](https://github.com/JordanMang/PHASE3WACAN/blob/main/Image/Logistic%20Regression.png)

Here you can see that the Logistic Regression was one of the better performing models. This is attributed to the fact that it is known to handle categoricals best but tends to perform poorly on imbalanced sets. The regression pictured above does have SMOTEN within it's pipeline as a way to counteract the imbalanced classes.

### Random Forest Classifier:

![RFC.png](https://github.com/JordanMang/PHASE3WACAN/blob/main/Image/RFC.png)

In an attempt to bypass the class imbalance a Random Forest Classifier was then used. Although not strong in the processing of categoricals RFC are known to work well with imbalanced sets. The RFC pictured above does also have SMOTEN within it's pipeline but was only added in a final attempt to convince the model to bahave.

### Gradient Boost Classfier:

![GBC.png](https://github.com/JordanMang/PHASE3WACAN/blob/main/Image/GBC.png)

One final model was applied in a desparate attempt to convince my f1 score to heights greater than .16 but sadly it never happened.

## Evaluation:

As of right now it appears that we do not currently have all the information needed to create a working model to predict who gets arrested after a Terry Stop. A Terry Stop is essentially a random stop and the most damaging part is that although it may appear that most races have a 1/10 chance of being arrested from a Terry Stop (Based on the information provided by SPD), minorities are pulled over for being "suspicious" at a disproportionate rate leading to unjust arrests. To make an accurate prediction of arrests we need to full picture, not just the race and gender information provided by SPD. From the data all we can say now is that there is a disproportionate number of minority members being pulled over.

![proportional%20arrests.png](https://github.com/JordanMang/PHASE3WACAN/blob/main/Image/proportional%20arrests.png)

## Conclusion:

If a predictive model is to be made more data is needed and it needs to be information that shows the full story of why a person was or wasn't arrested. The creation of a new and unbiased dataset is key in the completion of this project. Understanding what features are important is paramount, where is the feature that explains why they were arrested or a feature stating if the vehile smelled like weed or alcohol? There are so many variable unaccounted for in the current dataset that if we are to truly know what goes into making an arrest following a Terry Stop we would need to do our own data gathering. Based off the current dataset I dont believe SPD would actually fill out consistantly an expanded report that had all the information nessesary

It is also importnat to note that there may never be a model that can accurately predict whether a person will be arrested following a Terry Stop. The feature needed to create this model may not be tangible or measurable, understanding the prejudice of an officer or how someone may react to unjustly being pulled over the nth time may not be possible but we won't know until more data is gathered.

