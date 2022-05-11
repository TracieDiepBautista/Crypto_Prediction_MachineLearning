# Cryptocurrency Clusters

```diff
- Background
```

    As an Advisory Services member of a financial consultancy, one of our clients, a prominent investment bank, 
    was interested in offering a new cryptocurrency investment portfolio for its customers. The task was to create 
    a report that includes what cryptocurrencies were on the trading market and determine whether they can be grouped 
    to create a classification system for this new investment.
    
  ![blog_image_21-1](https://user-images.githubusercontent.com/93897775/167540512-1482f689-521d-45df-bc1c-b1fd0bd4549e.png)


```diff
+ Raw data to handle, so, the step-by-step of this project were:
```
    
    - Prep-processing data source to fit the machine learning models. Since there is no known classification system, 
      the unsupervised learning need to be used. 
    - Trying several clustering algorithms to explore whether the cryptocurrencies could be grouped together with 
      other similar cryptocurrencies. Y
    - Using data visualization techniques to share the key findings with the investment bank.
    - Discard all cryptocurrencies that are not being traded. In other words, filter for currencies that are currently being traded. 
    - Drop the `IsTrading` column from the dataframe.

    - Remove all rows that have at least one null value.

    - Filter for cryptocurrencies that have been mined. (the total coins mined should be greater than zero)

    - In order for the dataset to be comprehensible to a machine learning algorithm, convert its data should be numeric. 
    - Since the coin names do not contribute to the analysis of the data, delete the `CoinName` from the original dataframe.

    - Data preparation is to convert the remaining features with text values, `Algorithm` and `ProofType`, into numerical data. 
      (create dummy variables)

    - Standardize the dataset so that columns that contain larger values do not unduly influence the outcome.

```diff
+ Dimensionality Reduction
```

      Creating dummy variables above dramatically increased the number of features in the dataset: 
      
      - Perform dimensionality reduction with PCA. Rather than specify the number of principal components when 
        we instantiate the PCA model, it is possible to state the desired **explained variance**. 
        (For example, say that a dataset has 100 features. Using `PCA(n_components=0.99)` creates a model that will 
        preserve approximately 99% of the explained variance, whether that means reducing the dataset to 80 principal components
        or 3. For this project, 90% of the explained variance in dimensionality reduction was reserved.
        
       - reduce the dataset dimensions with t-SNE and visually inspect the results by running t-SNE on the principal components: 
       the output of the PCA transformation. Then created a scatter plot of the t-SNE output.
       

```diff
+ Cluster Analysis with k-Means
```

        - Create an elbow plot to identify the best number of clusters. Use a for-loop to determine the inertia for 
        each `k` between 1 through 10. (Determine, if possible, where the elbow of the plot is, and at which value of `k` it appears.)

```diff
- Tools and Resources used:
``` 

    - VSCode 
    - Python language | Matplotlib | Pandas 
    - pathlib
    - sklearn.preprocessing | sklearn.decomposition | sklearn.cluster (StandardScaler, PCA, K_Means)
    - The dataset was obtained from [CryptoCompare](https://min-api.cryptocompare.com/data/all/coinlist).
    
```diff
- Findings:
```

    Per the requirements, when applied PCA, 90% of the explained variance in dimensionality reduction 
    should be preserved, that meant, we should allow at least 90% of the data set to be useful. 
    
    - The above would get the most reliable results in which group (portfolio) of crypto mining is the best 
      to be invested. Unfortunately, the model turned out no portfolio is good in the data set for our investors
      at this moment. 
    
    - If we tried to adjust the PCA number of components to be lower before t-SNE on the principal components 
      that allow more trash data, let say, up to 50%, we would have 2 clusters to be considered as portfolio options. 
      However, I did not recommend this trial because the level of accuracy would be very low that might let our investors 
      take high risk. 


```diff
- Author:
```

    Tracie Bautista Nguyen
    Data Analyst 
    
