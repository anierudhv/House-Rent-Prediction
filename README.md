
# Predicting hose rent prices using regression techniques

# Steps to be followed:
### a) Keep the dataset and code in the same folder
### b) Run the code with this dataset


# Summary:
Housing prices fluctuate significantly based on myriad factors. As a result, completing a fair deal while purchasing or selling a property is still a challenge. This study aims to demystify the factors which go into objectively determining housing prices. The majority of property features shown by realtors demonstrate a linear relationship with housing price. Categorical features, in particular location-based features such as zip code, show a statistically significant relationship with price. However, due to the randomness associated with locations both linear and linear mixed effect models are considered in this model. The findings indicate that even though multiple factors are relevant in deciding housing prices, a small set of factors can be effectively used for predicting price. Furthermore, this study uncovers that pricing for certain types of properties deviate significantly from the norm in Kings Country, which are typically older and larger in lot size. The prediction accuracy of the final model indicates high efficacy in the Kings County region. Significant differences were not identified between the linear and a mixed effects model. The subset of identified predictors relevant to predicting housing price can be utilized as a starting point to build models for other regions. 


# Exploratory Data Analysis

## Distribution of data
This process is carried out to gain familiarity with the predictors involved. Histograms are effective for identifying data distributions. These distributions can be utilized to uncover patterns within the data, which can be used later to describe model behavior. Furthermore, histograms can also be utilized to  gather an understanding about the sparsity of data. 
For instance The sparsity of the `Sqft_basement` variable required transformation into a factor form rather than the numeric form retained by all other square footage related variables. The sparse data for basement data was due to ~61% of  residential properties not including a basement level. 


## Categorical variables
Boxplots of categorical variables plotted against the response variable are an effective method to gain a sense of within-group and between-group variability. Box Plots are utilized to understand which categorical variables are similar and aggregated to reduce the total number of categories within a predictor.


## Correlations
Correlation is measured between the predicting variables to detect (near) linear dependence and strengthen the interpretation of statistical statements. In particular, the presence of multicollinearity is evaluated to determine the precision of the estimate coefficients and quantify the statistical power of the final regression models. 


# Model choices and Goodness of Fit
For this data set and analysis, multiple linear regression is chosen to predict housing prices in Kings County. In addition, the linear mixed effects model is utilized to model the random effects contributed by the high dimensional zip code variable. The variability introduced by treating zip code as a random effect is used for variable selection and prediction. Each zip code contains idiosyncratic characteristics capturing the behavior of the residents and local infrastructure. In order to accommodate such characteristics, the linear mixed effects model is used with the random effect variable as zip codes. The `lme4` package provided by R statistical software has been used to model the mixed effects model, and the ‘glmmLASSO’ package has been used for variable selection.



## Data Transformations
Utilized Box-Cox transformations to ensure normality of response variable and constant variance amongst certain predicting variables


## Variable selection

In line with best practices, variable selection is performed to select the most relevant predictors and avoid overfitting the model. The methods employed in the project are Stepwise regression, Lasso and Elastic Net. Ridge regression is not utilized because it does not perform variable selection and there was no multicollinearity between predictors in the Kings County dataset. 
In order to avoid overfitting and effectively validate the model, the data is split into training and test sets. 75% of the data points are randomly selected to form the training set and the rest is set aside for testing.
Zip codes are used a controlling variable in linear models. Zipcodes are also used as variables with random effect when utilizing the mixed effects model.


## Model Validation
Mean Square Prediction Error (MSPE) is utilized to ascertain which model performs the best amongst our selection of models. 
Precision Measure(PM) gives a sense of the usefulness of the model in predicting the response.

## Categorical Variables
Predicting variables consisting of a discrete number of categories are converted to factors and inspected with box plots and ANOVA. The ANOVA analysis performed on the Year variable did not show statistical significance. Hence, we decided to drop ‘Year’ as a predicting variable.

