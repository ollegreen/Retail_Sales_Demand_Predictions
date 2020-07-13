# Machine Learning Engineer Nanodegree
## Capstone Report
Olle Green

*olleg.green@gmail.com*

July 12th, 2020

## I. Definition
_(approx. 1-2 pages)_

### Project Overview
In this section, look to provide a high-level overview of the project in layman’s terms. Questions to ask yourself when writing this section:
- _Has an overview of the project been provided, such as the problem domain, project origin, and related datasets or input data?_
- _Has enough background information been given so that an uninformed reader would understand the problem domain and following problem statement?_

**Olle**

#### Problem domain
Being a Master student in Operations Management at Stockholm University, the academic litterature has showed that the supply chain is an important part of orgnsations, that not many might know is facing some difficult pressures. As mentioned in the propsal, demand predictions in supply chain managagemnt (SCM) and logistics have historically been a constant pressure to make them more precise (Thomas & Griffin, 1996). The reason for this is due to the fact that inaccurate forecasting results in either too low supply to fulfill the current market demand, or too much, which in turn results in increased holding costs from inventory. Common ways to predict demand in SCM have been statistical models such as the ARIMA model (Jaipuria & Mahapatra, 2014). Academic articles have also tested different modern machine learning algorithms such as XGboost and compared them to more classical linear regressions (Vanichrujee, Horanont, Pattara-atikom, Theeramunkong, & Shinozaki, 2018). This is still a new concept of using more advanced machine learning algorithms to predict demand over classical statistical models such as linear regressions, which is a domain we would like to explore further in this project.

The key area of interest is: As an organisation grow larger, the more vital the precision in these predicitons become. Therefore, we will explore the possibility to utilise Machine Learning algorithms to predict the demand of certain products, in order for the SCM-team to make better planning for instance purchasing product components for an upcoming season. 

In this case, we will take a look at Walmart, the largest retailer in the US and use their data, which has been provided on kaggle.com in order to predict future demand of their sales. 

#### Problem origin
The broader demand forecasting prediciton problem has been studied for decades by academics and professionals (Suganthi & Samuel, 2012), however the the utlisation of Machine Learning algortihms for this purpose is a more recent phenomenon that academics still explore to this date (Carbonneau, Laframboise, & Vahidov, 2008) (Law, 2000). 

This specific demand forecasting problem for Walmart originated from kaggle.com and their demand forecasting predicition competition. See link to the competition [here](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting/overview). 

As we have the opportunity to utilise more modern algorithms, we would like to test how good results we can get from these compared to what the general forecaster uses. The general forecaster in this case will be the user "Hari Khanal" on the kaggle competition leaderboards for the Walmart competition, with a prediction score of 3985.79966. Why we chose Hari is because he is close to the median score out of 700 competitors for the Walmart competition. 

#### Related data sets or input data
The data used for this report was given in the kaggle competition by Walmart, which is as follows; 

##### 1. features.csv

Contains data related to the store, department, and regional activity for the given dates.

* Store - the store number
* Date - the week
* Temperature - average temperature in the region
* Fuel_Price - cost of fuel in the region
* MarkDown1-5 - anonymized data related to promotional markdowns. MarkDown data is only available after * Nov 2011, and is not available for all stores all the time. Any missing value is marked with an NA
* CPI - the consumer price index
* Unemployment - the unemployment rate
* IsHoliday - whether the week is a special holiday week

##### 2. train.csv

Historical sales data used for training. Within this tab you will find the following fields:

* Store - the store number
* Dept - the department number
* Date - the week
* Weekly_Sales -  sales for the given department in the given store
* IsHoliday - whether the week is a special holiday week

##### 3. test.csv

Same as train.csv in terms of columns, but instead we don't find the "Weekly_Sales", as this will be our dependent variable we will try to predict future sales in the final submission for the kaggle competition.

##### 4. stores.csv

Anonymized information about the 45 stores, indicating the type and size of store. 

* The store number (anonomised) 
* Type 
* Size

##### Note:
Currently given the data provided in the competition, we do not have any other related data sets or input data that we could or should utilise, to be in alignment with the competition rules at kaggle.com. 


### Problem Statement
In this section, you will want to clearly define the problem that you are trying to solve, including the strategy (outline of tasks) you will use to achieve the desired solution. You should also thoroughly discuss what the intended solution will be for this problem. Questions to ask yourself when writing this section:
- _Is the problem statement clearly defined? Will the reader understand what you are expecting to solve?_
- _Have you thoroughly discussed how you will attempt to solve the problem?_
- _Is an anticipated solution clearly defined? Will the reader understand what results you are looking for?_

#### What will we solve
We will solve the problem of predicitng future demand for sales of different Walmart stores, based on the provided data by the organsation. We will need to identify what data is helping the models, vs causing worse predicitons and adjust the data accordingly. 

#### how will we solve it 
We will use the data provided in the competition, clean it up so we can use it in our models. Then create demand predictions that are better then our kaggle-competition-benchmark score of 3985.79966. The intended solution will be based on the test.csv dataset for our demand predictions, where our machine learning algortihms will give use results which have taken the different features from the other datasets to give us good predictions of future demand. 


### Metrics
In this section, you will need to clearly define the metrics or calculations you will use to measure performance of a model or result in your project. These calculations and metrics should be justified based on the characteristics of the problem and problem domain. Questions to ask yourself when writing this section:
- _Are the metrics you’ve chosen to measure the performance of your models clearly discussed and defined?_
- _Have you provided reasonable justification for the metrics chosen based on the problem and solution?_


**Olle**

Ways to evalute the different models will be the following statistical measures of how accuracy and robustness;

#### Accuracy:
* Mean Absolute Error (MAE) - Measure the mean absolute errors. The smaller the number is (closer to 0), the better. 
* mean Squared Error (MSE) - measures the average of the squares of the errors. The smaller the number is (closer to 0), the better. 
* Root Mean Squared Error (RMSE) - the square root of the variance, known as the standard error. The smaller the number is (closer to 0), the better. 

#### Robustness:
* R-square (R^2) - Model used by academic (Nair & Vidal, 2011) for model robustness. The smaller the number is (closer to 0), the better. 

##### Why these metrics?
All of the above metrics assesses the errors between forecasts generated by our machine learning algoritms and compare them to the actual data. The metrics have been used for decades in statistics (C. J. Willmott et al., 1985) and in recent times been used for evaluation of Machine Learning models (Kavsaoğlu, Polat, & Hariharan, 2015). Therefore we will follow the academics and evaluate the machine learning preedictions using these measurements. 

#### Why multiple metrics instead of one?
We are choosing to not only look at one metric, but multiple as there has been exensive research of flaws of each metric when choosing between for example MAE vs RMSE (Willmott & Matsuura, 2005) (Chai & Draxler, 2014). Therefore, we will assess the final models using all three so we can verify the results. Meaning: instead of only looking at one, we instead look at three metrics to be certain there are not issues with our final results due to the metrics themselves. 

![Formulas](https://i.stack.imgur.com/83BUy.png)

#### Final note
All of these accuracy and robustness metrics will help us to assess which models are providing us with the better demand forecast model before submitting the best one to the kaggle competition to get our actual competition-score.



## II. Analysis
_(approx. 2-4 pages)_

### Data Exploration
In this section, you will be expected to analyze the data you are using for the problem. This data can either be in the form of a dataset (or datasets), input data (or input files), or even an environment. The type of data should be thoroughly described and, if possible, have basic statistics and information presented (such as discussion of input features or defining characteristics about the input or environment). Any abnormalities or interesting qualities about the data that may need to be addressed have been identified (such as features that need to be transformed or the possibility of outliers). Questions to ask yourself when writing this section:

- _If a dataset is present for this problem, have you thoroughly discussed certain features about the dataset? Has a data sample been provided to the reader?_

- _If a dataset is present for this problem, are statistics about the dataset calculated and reported? Have any relevant results from this calculation been discussed?_

- _If a dataset is **not** present for this problem, has discussion been made about the input space or input data for your problem?_

- _Are there any abnormalities or characteristics about the input space or dataset that need to be addressed? (categorical variables, missing values, outliers, etc.)_

**Olle**

#### Features discussion

To provide a decent analysis of all the features from the 3 different files of data into one file. See attached image for the header. 

IMAGE OF HEAEDER WITH COLUMNS. 

The different features are as follows: 

##### Store - the store number
This feature will be used for linking each other feature to the parent store to see if any linkage is find such as size etc. 

##### Date - the week
The date feature keeps the data in alignment so we compare the correct datapoints to eachother. However, we must note that it is very common that dates are in a string format, which was the case here, where we would change the data type into datetype format (Python Software Foundation, 2002) to handle the complex nature of dates and time. 

##### Temperature - average temperature in the region
The reason for including the temperature in this analysis is to see if perhaps we can find a postitive or negative relationship between how much people buy depending on how warm it is that week. For example it could be that on extremely hot weeks, people only buy a limited amount of products which relate to simply making handle the warmth itself. Thereby only buying ice cream. However, with the Data Scientist, Machine Learning Engineer or good old fashioned atatistician approach: we never assume, we test and find statistical significant measurments that indicate as such before any assumptions are made. 

##### Fuel_Price - cost of fuel in the region
This feature of cost of fuel in the region In a theoretical sense

##### MarkDown1-5 - anonymized data related to promotional markdowns. 

MarkDown data is only available after * Nov 2011, and is not available for all stores all the time. Any missing value is marked with an NA

##### CPI - the consumer price index

##### Unemployment - the unemployment rate

##### IsHoliday - whether the week is a special holiday week

##### Dept - the department number

##### Weekly_Sales 
Sales for the given department in the given store

##### IsHoliday - whether the week is a special holiday week

##### The store number (anonomised) 
Anonymized information about the 45 stores, indicating the type and size of store. 
##### Type 

##### Size


#### Abnormalities or Characteristics of the Data
* MarkDown data is only available after Nov 2011, and is not available for all stores all the time. Any missing value is marked with an NA.
* The test data is not through a full year, but instead it starts in november and ends in july. This needs to be taken into consideration as we split and analyse the time series part of the dataset. 
* It is a rather big dataset overall, with over 400 000 datapoints, but it is still only from a time perspective 3 years. It would be beneficial to have more data in order to verify the regressions results over not only these years, but longer time frames. But as this is what we have to work with, we will simply take this into consideration when we dive deeper into the analyis.  


### Exploratory Visualization
In this section, you will need to provide some form of visualization that summarizes or extracts a relevant characteristic or feature about the data. The visualization should adequately support the data being used. Discuss why this visualization was chosen and how it is relevant. Questions to ask yourself when writing this section:
- _Have you visualized a relevant characteristic or feature about the dataset or input data?_
- _Is the visualization thoroughly analyzed and discussed?_
- _If a plot is provided, are the axes, title, and datum clearly defined?_

**Olle**




### Algorithms and Techniques
In this section, you will need to discuss the algorithms and techniques you intend to use for solving the problem. You should justify the use of each one based on the characteristics of the problem and the problem domain. Questions to ask yourself when writing this section:
- _Are the algorithms you will use, including any default variables/parameters in the project clearly defined?_
- _Are the techniques to be used thoroughly discussed and justified?_
- _Is it made clear how the input data or datasets will be handled by the algorithms and techniques chosen?_

**Olle**




### Benchmark
In this section, you will need to provide a clearly defined benchmark result or threshold for comparing across performances obtained by your solution. The reasoning behind the benchmark (in the case where it is not an established result) should be discussed. Questions to ask yourself when writing this section:
- _Has some result or value been provided that acts as a benchmark for measuring performance?_
- _Is it clear how this result or value was obtained (whether by data or by hypothesis)?_

**Olle**




## III. Methodology
_(approx. 3-5 pages)_

### Data Preprocessing
In this section, all of your preprocessing steps will need to be clearly documented, if any were necessary. From the previous section, any of the abnormalities or characteristics that you identified about the dataset will be addressed and corrected here. Questions to ask yourself when writing this section:
- _If the algorithms chosen require preprocessing steps like feature selection or feature transformations, have they been properly documented?_
- _Based on the **Data Exploration** section, if there were abnormalities or characteristics that needed to be addressed, have they been properly corrected?_
- _If no preprocessing is needed, has it been made clear why?_

**Olle**



### Implementation
In this section, the process for which metrics, algorithms, and techniques that you implemented for the given data will need to be clearly documented. It should be abundantly clear how the implementation was carried out, and discussion should be made regarding any complications that occurred during this process. Questions to ask yourself when writing this section:
- _Is it made clear how the algorithms and techniques were implemented with the given datasets or input data?_
- _Were there any complications with the original metrics or techniques that required changing prior to acquiring a solution?_
- _Was there any part of the coding process (e.g., writing complicated functions) that should be documented?_

**Olle**



### Refinement
In this section, you will need to discuss the process of improvement you made upon the algorithms and techniques you used in your implementation. For example, adjusting parameters for certain models to acquire improved solutions would fall under the refinement category. Your initial and final solutions should be reported, as well as any significant intermediate results as necessary. Questions to ask yourself when writing this section:
- _Has an initial solution been found and clearly reported?_
- _Is the process of improvement clearly documented, such as what techniques were used?_
- _Are intermediate and final solutions clearly reported as the process is improved?_

**Olle**




## IV. Results
_(approx. 2-3 pages)_

### Model Evaluation and Validation
In this section, the final model and any supporting qualities should be evaluated in detail. It should be clear how the final model was derived and why this model was chosen. In addition, some type of analysis should be used to validate the robustness of this model and its solution, such as manipulating the input data or environment to see how the model’s solution is affected (this is called sensitivity analysis). Questions to ask yourself when writing this section:
- _Is the final model reasonable and aligning with solution expectations? Are the final parameters of the model appropriate?_
- _Has the final model been tested with various inputs to evaluate whether the model generalizes well to unseen data?_
- _Is the model robust enough for the problem? Do small perturbations (changes) in training data or the input space greatly affect the results?_
- _Can results found from the model be trusted?_

**Olle**



### Justification
In this section, your model’s final solution and its results should be compared to the benchmark you established earlier in the project using some type of statistical analysis. You should also justify whether these results and the solution are significant enough to have solved the problem posed in the project. Questions to ask yourself when writing this section:
- _Are the final results found stronger than the benchmark result reported earlier?_
- _Have you thoroughly analyzed and discussed the final solution?_
- _Is the final solution significant enough to have solved the problem?_

**Olle**




## V. Conclusion
_(approx. 1-2 pages)_

### Free-Form Visualization
In this section, you will need to provide some form of visualization that emphasizes an important quality about the project. It is much more free-form, but should reasonably support a significant result or characteristic about the problem that you want to discuss. Questions to ask yourself when writing this section:
- _Have you visualized a relevant or important quality about the problem, dataset, input data, or results?_
- _Is the visualization thoroughly analyzed and discussed?_
- _If a plot is provided, are the axes, title, and datum clearly defined?_

**Olle**



### Reflection
In this section, you will summarize the entire end-to-end problem solution and discuss one or two particular aspects of the project you found interesting or difficult. You are expected to reflect on the project as a whole to show that you have a firm understanding of the entire process employed in your work. Questions to ask yourself when writing this section:
- _Have you thoroughly summarized the entire process you used for this project?_
- _Were there any interesting aspects of the project?_
- _Were there any difficult aspects of the project?_
- _Does the final model and solution fit your expectations for the problem, and should it be used in a general setting to solve these types of problems?_

**Olle**



### Improvement
In this section, you will need to provide discussion as to how one aspect of the implementation you designed could be improved. As an example, consider ways your implementation can be made more general, and what would need to be modified. You do not need to make this improvement, but the potential solutions resulting from these changes are considered and compared/contrasted to your current solution. Questions to ask yourself when writing this section:
- _Are there further improvements that could be made on the algorithms or techniques you used in this project?_
- _Were there algorithms or techniques you researched that you did not know how to implement, but would consider using if you knew how?_
- _If you used your final solution as the new benchmark, do you think an even better solution exists?_

**Olle**


-----------

**Before submitting, ask yourself. . .**

- Does the project report you’ve written follow a well-organized structure similar to that of the project template? **Answer:**  
- Is each section (particularly **Analysis** and **Methodology**) written in a clear, concise and specific fashion? Are there any ambiguous terms or phrases that need clarification? **Answer:**  
- Would the intended audience of your project be able to understand your analysis, methods, and results? **Answer:**  
- Have you properly proof-read your project report to assure there are minimal grammatical and spelling mistakes? **Answer:**  
- Are all the resources used for this project correctly cited and referenced? **Answer:**  
- Is the code that implements your solution easily readable and properly commented? **Answer:**  
- Does the code execute without error and produce results similar to those reported? **Answer:**  
