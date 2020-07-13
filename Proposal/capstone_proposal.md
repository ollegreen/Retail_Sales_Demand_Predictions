# Machine Learning Engineer Nanodegree
## Capstone Proposal
Olle Green

*olleg.green@gmail.com*

July 5th, 2020

## Proposal

### Domain Background


The key area of interest is: As an organisation grow larger, the more vital the precision in these predicitons become. Therefore, we will explore the possibility to utilise Machine Learning algorithms to predict the demand of certain products, in order for the SCM-team to make better planning for instance purchasing product components for an upcoming season. 

### Problem Statement

The problem organisations SCM-departments face is that inaccurate forecasting for future demand cost organisations a lot of either missed sales or increased costs due to handling and storage of inventory (Thomas & Griffin, 1996). Therefore, we will test the hypothesis of comapring classic and more common statistical demand forecasting models to the more recent neural networks and machine learning algorithms, to assess if they produce better results. This will be used for predicting the department-wide sales for each store for the following year given our dataset of 45 retail stores. With this set-up, we can see that it is quantifiable, measurable and replicable. 

### Datasets and Inputs

We will use the dataset provided by Manjeet Singh on Kaggle.com "Retail Data Analytics



Contains data related to the store, department, and regional activity for the given dates.

* Store - the store number
* Date - the week
* Temperature - average temperature in the region
* Fuel_Price - cost of fuel in the region
* MarkDown1-5 - anonymized data related to promotional markdowns. MarkDown data is only available after * Nov 2011, and is not available for all stores all the time. Any missing value is marked with an NA
* CPI - the consumer price index
* Unemployment - the unemployment rate
* IsHoliday - whether the week is a special holiday week
* Sales



* Store - the store number
* Dept - the department number
* Date - the week
* Weekly_Sales -  sales for the given department in the given store
* IsHoliday - whether the week is a special holiday week



Anonymized information about the 45 stores, indicating the type and size of store. 

* The store number (anonomised) 
* Type 
* Size

#### Size of total dataset 

The different files containts the following amount of data: 

#### How will we work with these files 


### Solution Statement



### Benchmark Model


### Evaluation Metrics


* mean squared error (MSE) - measures the average of the squares of the errors 
* Root Mean Squared Error (RMSE) - the square root of the variance, known as the standard error

![Formulas](https://i.stack.imgur.com/83BUy.png)

All of which will help us to assess which models are providing us with the better demand forecast model. The smaller the number is (closer to 0), the better. 


1. To start we will set up a notebook instance and set up the training, validation and test data. 
2. Then we will proceed to visualise the data to get a better grip of what it looks like and how the different categorical data could be helping in the predictive demand forecasting model. In this part, we will include a correlation heat map, to understand how the data affect each other. Similar to the one attached: ![Correlation heatmap](https://i.stack.imgur.com/Lh8tv.png)
3. Then we will build our models -- In this case it seems fitting to test it with a moving average and a neural network to find some good predictions for the sales of the company. 
4. Then compare the scores -- Comparing the different models form step 3, might be other considered when we get into the data if needed. 
5. Finalise the results in a summary of what each model gave and what some notes in regards to the use of each model. 



-----------

**Before submitting your proposal, ask yourself. . .**

- Does the proposal you have written follow a well-organized structure similar to that of the project template? **Answer**: Yes. 

- Is each section (particularly **Solution Statement** and **Project Design**) written in a clear, concise and specific fashion? Are there any ambiguous terms or phrases that need clarification? **Answer:** Yes
- Would the intended audience of your project be able to understand your proposal?
- Have you properly proofread your proposal to assure there are minimal grammatical and spelling mistakes?
- Are all the resources used for this project correctly cited and referenced? **Answer:** Yes



## References

Jaipuria, S., & Mahapatra, S. S. (2014). An improved demand forecasting method to reduce bullwhip effect in supply chains. Expert Systems with Applications, 41(5), 2395–2408. https://doi.org/10.1016/j.eswa.2013.09.038

Shukla, M., & Jharkharia, S. (2011). ARIMA models to forecast demand in fresh supply chains. International Journal of Operational Research, 11(1), 1. https://doi.org/10.1504/ijor.2011.040325

Thomas, D. J., & Griffin, P. M. (1996). Coordinated supply chain management. European Journal of Operational Research, 94(1), 1–15. https://doi.org/10.1016/0377-2217(96)00098-7
