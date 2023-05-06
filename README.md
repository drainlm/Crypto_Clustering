CryptoClustering

Using K-means and Principal Component Analysis (PCA), this script performs clustering anaylsis on cryptocurrency market data (crypto_market_data.csv) in an effort to predict if cryptocurrencies are affected by 24 hour or 7 day price changes.

### Dependencies

* pandas
* hvplot
* sklearn.cluster.Kmeans
* sklearn.decomposition.PCA
* sklearn.preprocessing.StandardScaler

### Initial Market Data:

Below is an overview of our original data.

`<png>`

`<png>`

### **Prepare the Data**

Using StandardScaler()) module, the data is normalized and a DataFrame is created with the scaled data.

`<png>`

### Find the Best Value for k Using the Original Data.

Creating a list of k-values 1-11 and an empty list to store the inertia values, a loop then computes the inertia for each possible value. The inertia values are appended to the inertia list. Using the k-values and inertia values from the lists, a new DataFrame referencing the scaled data is created to plot the Elbow curve to help identify the optimal value for k.

`<png>`

* **Question:** What is the best value for `k`?

**
    Answer:** k4

### Cluster Cryptocurrencies with K-means Using the Original Scaled Data

Initizalizing a k-means model with 4 clusters and fitting it to the original scaled DataFrame, we then predict clusters to group the cryptocurrencies and add a new column to hold the predicted clusters. A scatterplot is then created to display the clustered scatter plot, with more information on the columns when hovering over each data point.

`<png>`

### Optimize Clusters with Principal Component Analysis

Performing a PCA and reducing the features to three principal components transforming the scaled data using fit.transform. The explained variance is then calculated to understand the amount of information attributed to each principal component, and the total explained variance is computed as well.

`<png>`

* **Question:** What is the total explained variance of the three principal components?
  Answer: The total explained variance is 89.5% of the total variance in the dataset.



Find the Best Value for k Using the PCA Data

    Use the elbow method on the PCA data to find the best value for`k` using the following steps:

    * Create a list with the number of k-values from 1 to 11.

* Create an empty list to store the inertia values.
* Create a `for` loop to compute the inertia with each possible value of `k`.
* Create a dictionary with the data to plot the Elbow curve.
* Plot a line chart with all the inertia values computed with the different values of `k` to visually identify the optimal value for `k`.
* Answer the following question in your notebook:

  * What is the best value for `k` when using the PCA data?
  * Does it differ from the best k value found using the original data?

    #### Cluster Cryptocurrencies with K-means Using the PCA Data

    Use the following steps to cluster the cryptocurrencies for the best value for `k` on the PCA data:


    * Initialize the K-means model with the best value for `k`.
* Fit the K-means model using the PCA data.
* Predict the clusters to group the cryptocurrencies using the PCA data.
* Create a copy of the DataFrame with the PCA data and add a new column to store the predicted clusters.
* Create a scatter plot using hvPlot as follows:

  * Set the x-axis as "price_change_percentage_24h" and the y-axis as "price_change_percentage_7d".
  * Color the graph points with the labels found using K-means.
  * Add the "coin_id" column in the `hover_cols` parameter to identify the cryptocurrency represented by each data point.
* Answer the following question:

  * What is the impact of using fewer features to cluster the data using K-Means?
