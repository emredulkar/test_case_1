This model is about monthly temperature prediction of 36 months ahead. The given predictor(independent) variables are precipitation, relative humidity, wind speed. Data source is NASA POWER API. The selected locaiton is Istanbul Technical Universtiy Campus.

A. Data retrieval- cleaning- visualisation - formatting

  1. Data is retrieved from the NASA POWER API by using request python library. The dates are between 2000 and 2025 June.
  2. Values printed to consol and made a visual check.
  3. Drop the sum of every years value in the data since it is not the raw data.
  4. Check the missing data is any.(There is no by the way)
  5. Droping the -999 values of after June 2025.
  6. Converting the necessary python pandas timeseries format for univariate analysis and dataframe format multivariate analysis.

B. Modeling

2 approaches are evaluated here.

  1. Using a univariate timeseries model- there is no predictor variable here. Temperature predicton is done by using temperature data itself.28 models have been tried, like auto arıma, Arıma etc. Best is selected. Considered metric is R^2 and RMSE.
     
  2. Using a multivariate machine learning model, predictor variables are used. 18 models have been tried, like adaboost, random forest etc. Best is selected. Considered metric is R^2.
     

Although knowing the disadvantages of the second approach, an initial scan has been done by reviewing the main metrics. (here predicting the independent variables can make the model more noisy since we use them again to predict the dependent variable.)

First approach might be more straightforward using univariate time series models. For both approach, Pycaret library is used. Pycaret enables us to make a quick review of many models.

First approach - Univariate models

Several univariate time series models have been compared, The top models performence are very close to each other,their MAE is almost 1 degree Celcius. since RMSE is very sensitive to peaks(droughts) and bottom, the lowest RMSE value is of Elastic Net w/ Cond. Deseasonalize & Detrending model(and the highest R^2 which is 0.9664), so it has been selected for further analysis.

<img width="1222" height="798" alt="image" src="https://github.com/user-attachments/assets/c3cdeb22-cd46-4c27-8690-f11ad4af861e" />


The test plot can be shown as below.

<img width="1302" height="421" alt="image" src="https://github.com/user-attachments/assets/09d4f49c-affa-43cc-8186-06f0a7f557e8" />

Finally 36 months forecasted graph is presented.

<img width="1300" height="506" alt="image" src="https://github.com/user-attachments/assets/24cc7fcc-ecbf-4696-a171-75fea0330399" />

Second approach - Multivariate models

Several models have been tried. Best one is extra trees regressor with a R^2 value of 0.8010. Comparing to the first approach this is significantly low.

<img width="822" height="642" alt="image" src="https://github.com/user-attachments/assets/28d630a7-61a7-4a3a-95fc-6f605c769031" />

Besides the lower R^2, second approach has a disadvantage such that predicting the independent variables can make the model more noisy since we use them again to predict the dependent variable. At this stage, progressing more is not useful. Modelling study has been interrupted.




