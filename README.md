# Amazon-sells-processing

# Documents
**Order Report**

amz.py: the Python functions file. It is not shown here due to business concerns. 

Amazon Market Analysis.ipny: the results of market analysis using Python

# Libraries Used
- Pandas
- Numpy
- Scikit-learn
- Matplotlib
- Scipy
- astropy
- re
- nltk
- 

# Functions
## 1. Data Cleaning
1.1 `x_ray_clean(df)`: cleans the dataframe from the x-ray data. 
    1. Delete unnecessary columns
    2. take ',' out of numbers
    3. change the Sales, Revenue, BSR, Review Count data type from string to integer or float
    4. drop na values in Sales
    5. sort the values by Sales
    6. Add 'Review Ratio', 'Volume', 'Size Tier Numeric', 'Listing Length' Column
    7. reset index
    
## 2. Data Understanding

2.1 `tokenize(text)`:split a sentence into individual words 
  - INPUT: 
    - text: a sentence
  - OUTPUT:
    - clean_tokens: a list of words with stopwords removed and stemmed and lemmatized

2.2 `keywords_analysis(df)`:analyze keywords from the product title
  - INPUT: 
    - df: dataframe (of the result extracted from Amazon website)
  - OUTPUT:
    - plot of top 10 keywords from top 5 products, top 15 keywords from top 10 products, top 20 keywords from top 50 products, top 20 keywords from top 100 products.
    - dataframe: list of keywords and their occurance in top 5, 10, 50 and 100 products in the category

2.3 `plot_Fulfillment(df)`:analyze the fulfillment method for the products 
  - INPUT: 
    - df: dataframe (of the result extracted from Amazon website)
  - OUTPUT:
    - Pie plot of fulfillment categories from the top 5 products, top 10 products, top 50 products, top 100 products.

2.4 `price_analysis(df)`:analyze price from the product title 
- INPUT: 
  - df: dataframe (of the result extracted from Amazon website)
- OUTPUT:
  - Histogram of price distrbution of all products.
  - Dictionary of mean, min, max and stdev of the prices
 
2.5 `ratings_analysis(df)`:analyze price from the product title 
  - INPUT: 
    - df: dataframe (of the result extracted from Amazon website)
  - OUTPUT:
    - One scatter plot of ratings distribution for the top products
    - Histogram of ratings distrbution of all products.
    - Dataframe of the mean, min, max and stdev in ratings in top 10, 50 and 100 products

2.6 `review_analysis(df)`:analyze price from the product title 
  - INPUT: 
    - df: dataframe (of the result extracted from Amazon website)
  - OUTPUT:
    - One scatter plot of review count distribution for the top products
    - Histogram of review count distrbution of all products.
    - One scatter plot of review ratio distribution for the top products
    - Histogram of review ratio distrbution of all products.
    - Dictionary of the mean, min, max and stdev in review count and ratio in all products
  
2.7. `size_analysis(df)`:analyze size from the product title 
  - INPUT: 
    - df: dataframe (of the result extracted from Amazon website)
  - OUTPUT:
    - One scatter plot of item volume distribution for the top products
    - Histogram of item volume and item weight distrbution of all products.
    - A pie chart of the Size Tier categories.

2.8. `plot_sales(df)`: plot the sales data
  - INPUT: 
    - df: (Dataframe) of the cleaned x-ray data
  - OUTPUT:
    - plot consisting of 4 graphs:
    1. Sales vs. BSR
    2. Revenue vs. BSR
    3. Sales vs. # within category
    4. BSR vs. # within category
  
2.9. `date_image_analysis(df)`:analyze size from the product title 
  - INPUT: 
    - df: dataframe (of the result extracted from Amazon website)
  - OUTPUT:
    - Histogram of image number distrbution of all products.
    - One scatter plot of item days on Amazon distribution for the top products
    - Histogram of Years on Amazon distrbution for top 10, 50, 100 products.
    - A pie chart of the Size Tier categories.

## 3. Models
3.1 `one_ele_poly(x, beta_1, beta_2)`:
A single element polyniomial model used to model the BSR vs. # within category
  - INPUT:
    - x: varibale
    - beta_1, beta_2: constant for the model
  - OUTPUT:
    - y

3.2 `exp(x, beta_1, beta_2, beta_3)`:
An exponential model used to model the BSR vs. # within category
  - INPUT:
    - x: varibale
    - beta_1, beta_2, beta_3: constant for the model
  - OUTPUT:
    - y

3.3 `inv_one_ele_poly(x, beta_1, beta_2)`:
An inverse single element polyniomial model used to model the BSR vs. # within category
  - INPUT:
    - x: varibale
    - beta_1, beta_2, beta_3: constant for the model
  - OUTPUT:
    - y

3.4 `Lorentz_ranking(x, beta_1, beta_2)`: 
A Lorentz model that models sales vs. # within category
  - INPUT:
    - x: varibale
    - beta_1, beta_2: constant for the model
  - OUTPUT:
    - y 

3.5 `model_fitting(x, y, model)`:
Fit a set of x and y data using a model
  - INPUT:
    - x, y: array of data of the same length
    - model: model used for modelling
  - OUTPUT:
    - param: a dictionary containing betas, Mean absolute error, MSE, R2-score
    - A plot showing the fitted curve and original data
    
## 4. Model Fitting
4.1 `value_list_create(Val, df_list)`:
Create an array of values from a list of dataframes
  - INPUT:
    - Val: the value from the dataframe we want to create a list from
    - df_list: list of dataframes to be used
  - OUTPUT:
    - Data: array of data extracted

4.2 `get_df_name(df)`: get the name of the dataframe
  - INPUT: dataframe
  - OUTPUT: (string)name of the dataframe

4.3 `plot_rank_distri(cat, BSR, title = '')`: 
Plot categorial ranking vs. BSR as well as the distribution (derivative) of the ranking in BSR
  - INPUT: 
    - cat: (list or tuple) of the categorial ranking
    - BSR: (list or tuple) of the BSR ranking
    - title: title of the plot
  - OUTPUT:
    - plot 1: categorial ranking vs. BSR
    - plot 2: distribution (derivative) of the ranking vs. BSR

4.4 `Rank_Fit_Param_Table_generate(df_lst, model)`: generates a dataframe of parameters relating to the fitting of a series of dataframes using their categorial ranking and BSR
  - INPUT: 
    - df_lst: list of the name of the dataframe
    - model: model to be fitted
  - OUTPUT:
    - Fit_Param: dataframe of parameters

4.5 `Fit_Param_Table_generate(df_lst, x, y, model = inv_one_ele_poly)`:
generates a dataframe of parameters relating to the fitting of a series of dataframes using their categorial ranking and Sales
  - INPUT: 
    - df_lst: list of the name of the dataframe
    - model: model to be fitted
  - OUTPUT:
    - Fit_Param: dataframe of parameters

## 5. Evaluation
5.1 `cat_sales(df, model = inv_one_ele_poly)`:
predict the sales in a category using inverse one element polynomial model
  - INPUT:
    - df: the datafram of the items in the category containing its BSR and sales numbers
    - model: model used to predict sales based on the ranking
  - OUTPUT:
    - fitted: a dictionary containing betas, Mean absolute error, MSE, R2-score
    - A plot showing the fitted curve and original data
    - sales_results: a dictionary of the top few sales data
  
5.2 `cat_sales_table(df_lst)`:
generates a dataframe that returns the sales data from a list of dataframe
  - INPUT:
    - df: the datafram of the items in the category containing its BSR and sales numbers
  - OUTPUT:
    - df: a dataframe of the top sales data
  
5.3 `cat_cat_ranking(x, beta_1s, beta_2s, beta_1b, beta_2b)`:
Predicts the ranking of one category from the ranking of the other category
  - INPUT:
    - x: the ranking of the category to be converted
    - beta_1s, beta_2s: the inverse polynomial parameters of the smaller(sub-) category
    - beta_1b, beta_2b: the inverse polynomial parameters of the bigger category
  - OUTPUT:
    - y: the ranking of the converted category 
  
5.4 `cat_cat_rank_relat(general_cat, sub_cat)`:
analyze the relationship between two categories: a general category and its sub-category
  - INPUT: 
    - general_cat: dataframe of the general category
    - sub_cat: dataframe of the sub-category
  - OUTPUT: 
    - cat_cat_relat: a dictionary predicting the ranking of the top ranking in the general category, and the percentage of the top 10, 50, 100 tops in the general category

## 6. Deployment
6.1 `prod_in_cat(prod_df, cat_df)`:
Calculate some parameters relating to a product in a category.
  - INPUT: 
    - prod_df: dataframe of the product
    - cat_df: dataframe of the category
  - OUTPUT:
    - ranking_by_BSR: ranking of the product in the category by the BSR
    - ranking_by_Sales: ranking of the product in the category by Sales
    - percentile: the percentile of the product in the cateory in ranking
