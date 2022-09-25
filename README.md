# Ugly Christmas Party

## Introduction
Ugly Christmas Party (UCP) is a seasonal small business dedicated to selling Christmas sweaters online shipped through Amazon and their own warehouse.

## Dataset
The data was taking from programs (Channel Advisor and SKU Vault) UCP uses to keep track of their products. The final dataset used to apply models was a combination of UCP’s inventory, sales, and pricing datasets.
Sources: 
•	uglychristmasparty.com 
•	channeladvisor.com
•	skuvault.com

## Purpose of the analysis
UCP loses thousands of dollars every year when they do not order enough and sell out of a Christmas sweater or when they overestimate the number of sweaters that they will sell. Once the sweaters are ordered they cannot order more or return them. Seasonal product companies like UCP lose money every year in inventory costs whether it’s in house or in the Amazon warehouses. Storing and housing a large amount of sweaters that are not sold during the Christmas season cost the business a lot of money. At the end of 2020 UCP had 11,843 sweaters left over = $110,000 approximately of unsold merchandise. The company needs an accurate model to help them determine how many sweaters they will sell for each design created.

## Research Question
How do Decision Tree, Random Forest, K-nearest neighbor, and Linear Regression compare with each other in predicting how many Ugly Christmas sweaters will be sold based on the sweater’s characteristics?

## Variables
Output variable:
-	Sold Quantity: Number of sweaters sold.
Input variables: 
-	SKU: unique sweater ID.
-	Buy It Now Price: $14-$50.
-	Category: Cute, Pop culture, Religious, Comedy, Costume, Alcohol, Naughty, and 3D Pop out.
-	Change Price: has the price changed during the season or not?
-	Character: Reindeer, Elf, Snowman, Jesus, Cat, Tv Show, Tree, Dog, Mrs. Claus, Gingerbread man, Santa, Llama, Fireplace, Giraffe, Godzilla, Internet, Polar bear, Menorah, Dinosaur, Sleigh, Penguins, Skull, Tuxedo, Wine, and Yeti.
-	Color: black, green, blue, orange, red, grey, white, yellow, multicolor, turquoise, and purple.
-	Image Count: 1-9.
-	Lights: does the sweater have lights or not?
-	Hood: does the sweater have a hood or not?
-	Size: X-Small - 4X-Large.
-	Classification: Men’s Sweater, Women’s Sweater, and Dog Sweater.

## Exploratory Data Analysis
#### Sold Quantity Boxplot
![alt text](https://github.com/natvalenz/uglyXmas/blob/main/Picture2.png)
This graph shows the variable has a great number of outliers and further action will be needed.

#### Variable Heatmap
![alt text](https://github.com/natvalenz/uglyXmas/blob/main/Picture3.png)
The map shows no correlation between variables.

#### Descriptive Statistics
![alt text](https://github.com/natvalenz/uglyXmas/blob/main/Picture4.png)
The table describes counts, means, standard deviations, and percentiles.

#### Variable Pairplot
![alt text](https://github.com/natvalenz/uglyXmas/blob/main/Picture5.png)
Histograms and Scatterplots.


## Data Preprocessing, Data Partitioning, and Feature Selection
The sales, inventory, and pricing datasets were analyzed, and the data was very dirty. Irrelevant, duplicate, and over 400 null values columns were dropped. The dataset was scaled appropriately based on the type of data (categorical or continuous). Sold Quantity had a lot of outliers, so anything with the y variable above 200 was dropped. The data was cleaned thoroughly and merged into a final dataset containing 430 observations and 11 variables. The data was split into 70% training data and 30% testing data.
The model was performing poorly, so feature importance using Decision trees and field knowledge was used to select the most important variables. Variables that looked important in the graphs were included, and then were left out because they were not adding significantly to the model’s performance.

#### Profit Histogram
![alt text](https://github.com/natvalenz/uglyXmas/blob/main/Picture13.png)
The sweaters in the alcohol and pop culture categories made the most profits.

#### Feature Importance Graph
![alt text](https://github.com/natvalenz/uglyXmas/blob/main/Picture14.png)
The size, image count, change price, and price variables were the most relevant.

## Algorithms
A Decision Tree, Random Forest, K-nearest neighbor, and Linear Regression models were applied. The training data was used to fit the model. In an intent to improve the results the output variable was made categorical using bins of 5 for the number of sweaters, but this did not improve the model significantly. Each model was hyper tuned using a grid search method, and the best result was the Random Forest model. This model had the least number of sweaters off by of 35 which implies the model is possibly not predicting well. 

#### Model: Random Forest
![alt text](https://github.com/natvalenz/uglyXmas/blob/main/Picture15.png)
The model is not performing well it is overfitting.

#### Hyperparameter Tuning: Random Forest
![alt text](https://github.com/natvalenz/uglyXmas/blob/main/Picture16.png)
![alt text](https://github.com/natvalenz/uglyXmas/blob/main/Picture17.png)
Although the model was tuned, the overfitting has not been corrected.

#### Model Selection: Random Forest
![alt text](https://github.com/natvalenz/uglyXmas/blob/main/Picture18.png)
Although the model was tuned, the overfitting has not been corrected.
![alt text](https://github.com/natvalenz/uglyXmas/blob/main/Picture19.png)

## Conclusion
In 2020 UCP had an excess of 12,000 sweaters or $115,000 approximately, and the best model would be off by 14,000 sweaters or $195,000 by average not including storage costs. The datasets were not created to collect relevant data to solve the issue, and UCP does not have the infrastructure to collect the data needed to solve the problem. Although a lot was done to address the overfitting, this resulted in underfitting and to be off by 3 more sweaters (38 total per SKU). From the results of all the models applied it is clear important variables that explain how many sweaters will sell are missing. In the future text analysis of the reviews and social media promotions done in 2021 should help improve the model.
