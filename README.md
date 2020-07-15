# Amazon-sells-processing

# Documents
**Order Report


# Functions
`x_ray_clean(df)`: cleans the dataframe from the x-ray data. 
1. Delete unnecessary columns
2. take ',' out of numbers
3. change the Sales, Revenue, BSR data type from string to integer or float
4. drop na values in Sales
5. sort the values by BSR
6. reset index

`plot_sales(df)`: plot the sales data
INPUT: 
df: (Dataframe) of the cleaned x-ray data
OUTPUT:
plot consisting of 4 graphs:
1. Sales vs. BSR
2. Revenue vs. BSR
3. Sales vs. # within category
4. BSR vs. # within category

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

