# Predictive-ML-Models-for-Final-Grade
## Introduction
The goal of the following work is to train some machine learning models in order to predict the final portuguese grade of students attending two schools in Portugal. In the portuguese scholar system the grades are between 0 and 20, following this hierarchy (https://en.wikipedia.org/wiki/Academic_grading_in_Portugal): <br>

|   Grade	|   Qualification	|  
|---	|---	|
|  20-17.5 	|   Excellent	|  
|   17.4-15.5		|   Very good	|   	
|   15.4-13.5	|   Good	|  
|   13.4-9.5		|   Sufficient	| 
|   9.4-3.5		|   Weak	| 
|   3.4-0		|   Poor	| 

Furthermore the school year is divided into three parts, and in the end of all of them the students reiceve a grade. In the used dataset (https://www.kaggle.com/datasets/uciml/student-alcohol-consumption) all of the three grades are reported, but we only focused on the final grade, i.e. G3. <br> <br>
The work is organized as follows: <br>
1) First of all an exploratory data analysis (EDA) of the considered dataset is provided. In particular, the EDA is mainly focused on the label, namely the final portuguese grade (G3), but other insights from the data are also took into account. <br><br>
2) Second of all the machine learning models are trained on an appropriately training set. All the considered models have one or more hyperparameters, which are tuned thanks to a cross validation procedure. In specific, the machine learning models which have been considered are: <br>
* `K-Nearest Neighbors (KNN)` <br>
* `Decision Tree (DT)` <br>
* `Lasso Regression (Lasso)` <br>
* `Support Vector Regressor (SVR)` <br>
* `Random Forest (RF)` <br><br> 

3) After that, the trained models are tested on the test set and the best models are choosen. The latter results to be `Support Vector Regressor (SVR)` and `Random Forest (RF)`. Then a plot containing the real values and the predicted values is made, and the latter furnishes us an insight concerning the builded machine learning models. After that an analysis on the distribution of the errors commited by the two models is made, and the latter provides us a discriminant to choose between one of the two models. Lastly, a plot containing the most 'predictive' features is provided. <br><br>

Here there is a prospectus of all the features into the dataset: <br>

|   Variable name	|   Variable description	|   Type	|   Values	|
|---	|---	|---	|---	|
|   school	|  student's school 	|  categorical 	|   'GP' - Gabriel Pereira  <br>'MS' - Mousinho da Silveira	|
|   sex 	|   student's sex	|   categorical	|   'F' - female  '<br> M' - male	|
|   age	|   student's age	|   integer	|  from 15 to 22 	|
|  address 	|   student's home address type	|   categorical	|   'U' - urban <br> 'R' - rural	|
|   famsize	|   family size	|   categorical	|  'LE3' - less or equal to 3 <br> 'GT3' - greater than 3 	|
|   Pstatus	|   parent's cohabitation status	|  categorical 	|  'T' - living together <br> 'A' - apart 	|
|   Medu	|   mother's education	|  integer 	| 0 - none <br> 1 - primary education (4th grade) <br> 2 – 5th to 9th grade <br> 3 – secondary education  <br> 4 – higher education  	|
|   Fedu	|   father's education	|   integer	| 0 - none <br> 1 - primary education (4th grade) <br> 2 – 5th to 9th grade <br> 3 – secondary education  <br> 4 – higher education  |
|   Mjob	|   mother's job	|   categorical	|  'teacher' <br> 'health' care related <br>civil 'services' (e.g. administrative or police) <br> 'at_home' or 'other')	|
|   Fjob	|   father's job	|   categorical	|   'teacher' <br> 'health' care related <br>civil 'services' (e.g. administrative or police) <br> 'at_home' or 'other')		|
|   reason	|   reason to choose this school	|   categorical	|   close to 'home' <br> school 'reputation' <br> 'course' preference <br> 'other'	|
|  guardian 	|   student's guardian	|  categorical 	|   'mother' <br>'father' <br> 'other'	|
|   traveltime	|   home to school travel time	|   integer	|   1 - <15 min. <br> 2 - 15 to 30 min. <br> 3 - 30 min. to 1 hour <br> 4 - >1 hour	|
|  studytime 	|  weekly study time 	|   integer	|   1 - <2 hours <br> 2 - 2 to 5 hours <br> 3 - 5 to 10 hours <br> 4 - >10 hours	|
|   failures	|  number of past class failures 	|  integer 	|   n if 1<=n<3, else 4	|
|  schoolsup 	|   extra educational support	|   categorical	|  yes or no 	|
|   famsup	|   family educational support	|    categorical	|   yes or no	|
|   paid	|   extra paid classes within the course subject (Math or Portuguese) 	|   categorical 	|   yes or no	|
|   activities	|   extra-curricular activities	|    categorical	|   yes or no	|
|   nursery	|  attended nursery school 	|    categorical	| yes or no  	|
|   higher 	|  wants to take higher education 	|   categorical 	|   yes or no	|
|   internet	|   Internet access at home	|    categorical	|   yes or no	|
|   romantic	|   with a romantic relationship	|   categorical 	|   yes or no	|
|   famrel	|   quality of family relationships	|   integer	|   from 1 - very bad to 5 - excellent	|
|   freetime	|   free time after school	|   integer	|   from 1 - very low to 5 - very high	|
|   goout	|   going out with friends	|   integer	|   from 1 - very low to 5 - very high	|
|   Dalc	|   workday alcohol consumption	|   integer	|   from 1 - very low to 5 - very high	|
|   Walc	|   weekend alcohol consumption	|   integer	|   from 1 - very low to 5 - very high	|
|   health	|  current health status 	|   integer	|   from 1 - very bad to 5 - very good	|
|   absences	|   number of school absences	|   integer	|   from 0 to 93	|

## Conclusions

### In conclusion:
### 1) The best models to predict the final grade G3 are Support Vector Regressor (SVR) and Random Forest (RF), and the latter have a mean absolute error (MAE) around 2.25 and 2.27 respectively. 
### 2) Both SVR and RF tend to predict the final grade around the mean value of the latter. Consequencially, both tend to underestimate the grades higher than the mean and to overestimate the grade lower than the mean.
### 3) By analysing the distribution of the errors made by both models it follows that SVR is 'more balanced', i.e. it has a better ratio between underestimated and overestimated grades, while RF performs better on the outliers. Thus, the choice between which model to use depends on the application needs.
### 4) According to the common sense and the provided EDA the most important features for the prediction of G3 should be 'studytime', 'higher', 'failures', 'goout' and 'Walc'. However, the RF indicates 'failures', 'absences', 'higher', 'age',  and 'Walc' as the most important features. This is not surprising, since also the variables which we have not considered as the most important clearly show an influence of the final grade as showed in the EDA. Moreover, according to RF the 'failures' variable is by far the most important one. 
