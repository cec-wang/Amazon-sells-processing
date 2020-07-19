# Amazon-sells-processing

# Documents
**Order Report


# Functions
## Data Cleaning
`x_ray_clean(df)`: cleans the dataframe from the x-ray data. 
1. Delete unnecessary columns
2. take ',' out of numbers
3. change the Sales, Revenue, BSR, Review Count data type from string to integer or float
4. drop na values in Sales
5. sort the values by Sales
6. Add 'Review Ratio', 'Volume', 'Size Tier Numeric', 'Listing Length' Column
7. reset index
## Data Understanding
`tokenize(text)`:split a sentence into individual words 
- INPUT: 
  - text: a sentence
- OUTPUT:
  - clean_tokens: a list of words with stopwords removed and stemmed and lemmatized

`keywords_analysis(df)`:analyze keywords from the product title
- INPUT: 
  - df: dataframe (of the result extracted from Amazon website)
- OUTPUT:
  - plot of top 10 keywords from top 5 products, top 15 keywords from top 10 products, top 20 keywords from top 50 products, top 20 keywords from top 100 products.
  - dataframe: list of keywords and their occurance in top 5, 10, 50 and 100 products in the category

`plot_Fulfillment(df)`:analyze the fulfillment method for the products 
- INPUT: 
  - df: dataframe (of the result extracted from Amazon website)
- OUTPUT:
  - Pie plot of fulfillment categories from the top 5 products, top 10 products, top 50 products, top 100 products.

`price_analysis(df)`:analyze price from the product title 
- INPUT: 
  - df: dataframe (of the result extracted from Amazon website)
- OUTPUT:
  - Histogram of price distrbution of all products.
  - Dictionary of mean, min, max and stdev of the prices
 
`ratings_analysis(df)`:analyze price from the product title 
- INPUT: 
  - df: dataframe (of the result extracted from Amazon website)
- OUTPUT:
  - One scatter plot of ratings distribution for the top products
  - Histogram of ratings distrbution of all products.
  - Dataframe of the mean, min, max and stdev in ratings in top 10, 50 and 100 products

`review_analysis(df)`:analyze price from the product title 
- INPUT: 
  - df: dataframe (of the result extracted from Amazon website)
- OUTPUT:
  - One scatter plot of review count distribution for the top products
  - Histogram of review count distrbution of all products.
  - One scatter plot of review ratio distribution for the top products
  - Histogram of review ratio distrbution of all products.
  - Dictionary of the mean, min, max and stdev in review count and ratio in all products
  
`size_analysis(df)`:analyze size from the product title 
- INPUT: 
  - df: dataframe (of the result extracted from Amazon website)
- OUTPUT:
  - One scatter plot of item volume distribution for the top products
  - Histogram of item volume and item weight distrbution of all products.
  - A pie chart of the Size Tier categories.

`plot_sales(df)`: plot the sales data
- INPUT: 
  - df: (Dataframe) of the cleaned x-ray data
- OUTPUT:
  - plot consisting of 4 graphs:
  1. Sales vs. BSR
  2. Revenue vs. BSR
  3. Sales vs. # within category
  4. BSR vs. # within category
  
`date_image_analysis(df)`:analyze size from the product title 
- INPUT: 
  - df: dataframe (of the result extracted from Amazon website)
- OUTPUT:
  - Histogram of image number distrbution of all products.
  - One scatter plot of item days on Amazon distribution for the top products
  - Histogram of Years on Amazon distrbution for top 10, 50, 100 products.
  - A pie chart of the Size Tier categories.

## Modelling
`one_ele_poly(x, beta_1, beta_2)`:
A single element polyniomial model used to model the BSR vs. # within category
- INPUT:
  - x: varibale
  - beta_1, beta_2: constant for the model
- OUTPUT:
  - y

`exp(x, beta_1, beta_2, beta_3)`:
An exponential model used to model the BSR vs. # within category
- INPUT:
- x: varibale
- beta_1, beta_2, beta_3: constant for the model
- OUTPUT:
- y

`inv_one_ele_poly(x, beta_1, beta_2)`:
An inverse single element polyniomial model used to model the BSR vs. # within category
- INPUT:
- x: varibale
- beta_1, beta_2, beta_3: constant for the model
- OUTPUT:
- y

`model_fitting(x, y, model)`:
Fit a set of x and y data using a model
- INPUT:
- x, y: array of data of the same length
- model: model used for modelling
- OUTPUT:
- param: a dictionary containing betas, Mean absolute error, MSE, R2-score
- A plot showing the fitted curve and original data

`value_list_create(Val, df_list)`:
Create an array of values from a list of dataframes
- INPUT:
- Val: the value from the dataframe we want to create a list from
- df_list: list of dataframes to be used
- OUTPUT:
- Data: array of data extracted

`get_df_name(df)`: get the name of the dataframe
- INPUT: dataframe
- OUTPUT: (string)name of the dataframe

`Rank_Fit_Param_Table_generate(df_lst, model)`: generates a dataframe of parameters relating to the fitting of a series of dataframes using their categorial ranking and BSR
- INPUT: 
- df_lst: list of the name of the dataframe
- model: model to be fitted
- OUTPUT:
- Fit_Param: dataframe of parameters

