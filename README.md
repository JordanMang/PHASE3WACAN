{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Project Overview:"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The Washington Community Action Network has asked me to explore how Terry Stops, a form of police traffic stop that only requires detection of \"suspicious' behavior to conduct, negatively impacts minority communities. WCAN hopes that through the creation of a predictive model we can better understand what leads to an arrest followingg a Terry stop. Along with this predictive model they have asked me to do some EDA as well as provide actionable next steps for refining this model. <br> <br> When viewing the Jupyter Notebooks please note the the first notebook includes the exploration of my baseline model, the second notebook uses more advanced algorithms and the third notebook utalizes a revised set of arrest data and well as some EDA."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Business and Data Understanding:"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "WCAN does not currently have its own dataset of Terry Stops and the only publically avaiable dataset is provided by the Seattle Police Department. There are many limitations to this dataset but mostly it will be used as a starting point and a way of understanding what features will be important to include in their round of data gathering. After cleaning the dataset and eleminating features that were irrelevent or had high multicolinearity I was left with ten features. Of these ten features the most noteable were, Officer race and gender, subject race and gender, time of terry stop and location of the stop. All of the features were categorical. It should be fairly obvious that from the limited scope of these features the creation of a predictive model was destined to fail."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Modeling:"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Although my model failed to perform better than the baseline model there were many insights to be gained which will be discussed after a quick look into what models I ran and an explaination of some of my steps in attempting to troubleshoot it."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Dummy Model (Baseline):"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "![Dummy.png](attachment:./Image/Dummy.png)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "From my baseline model you can see that the dataset is fairly imbalanced and that most of my models will be deceptively accurate. To combat this I created some Synthetic data through the use of SMOTEN."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Logistic Regression (Basic):"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "![Logistic%20Regression.png](attachment:./Image/Logistic%20Regression.png)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Here you can see that the Logistic Regression was one of the better performing models. This is attributed to the fact that it is known to handle categoricals best but tends to perform poorly on imbalanced sets. The regression pictured above does have SMOTEN within it's pipeline as a way to counteract the imbalanced classes."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Random Forest Classifier:"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "![RFC.png](attachment:./Image/RFC.png)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "In an attempt to bypass the class imbalance a Random Forest Classifier was then used. Although not strong in the processing of categoricals RFC are known to work well with imbalanced sets. The RFC pictured above does also have SMOTEN within it's pipeline but was only added in a final attempt to convince the model to bahave."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Gradient Boost Classfier:"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "![GBC.png](attachment:./Image/GBC.png)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "One final model was applied in a desparate attempt to convince my f1 score to heights greater than .16 but sadly it never happened."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Evaluation:"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "As of right now it appears that we do not currently have all the information needed to create a working model to predict who gets arrested after a Terry Stop. A Terry Stop is essentially a random stop and the most damagine part is that although it may appear that most races have a 1/10 chance of being arrested from a Terry Stop (Based on the information provided by SPD), minorities are pulled over for being \"suspicious\" at a disproportionate rate leading to unjust arrests. To make an accurate prediction of arrests we need to full picture, not just the race and gender information provided by SPD. From the data all we can say now is that there is a disproportionate number of minority members being pulled over."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "![proportional%20arrests.png](attachment:./Image/proportional%20arrests.png)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Conclusion:"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "If a predictive model is to be made more data is needed and it needs to be information that shows the full story of why a person was or wasn't arrested. The creation of a new and unbiased dataset is key in the completion of this project. Understanding what features are important is paramount, where is the feature that explains why they were arrested or a feature stating if the vehile smelled like weed or alcohol? There are so many variable unaccounted for in the current dataset that if we are to truly know what goes into making an arrest following a Terry Stop we would need to do our own data gathering. Based off the current dataset I dont believe SPD would actually fill out consistantly an expanded report that had all the information nessesary<br><br> It is also importnat to note that there may never be a model that can accurately predict whether a person will be arrested following a Terry Stop. The feature needed to create this model may not be tangible or measurable, understanding the prejudice of an officer or how someone may react to unjustly being pulled over the nth time may not be possible but we won't know until more data is gathered."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python (learn-env)",
   "language": "python",
   "name": "learn-env"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
