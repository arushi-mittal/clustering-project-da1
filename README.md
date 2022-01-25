# Data Analytics Project 1

##### Arushi Mittal (2019101120) and Meghna Mishra (2019111030)

### Data Visualization

1. We plotted histograms on the basis of positions, ages and skill moves.
2. We found the most 5 common countries and clubs and plotted the ages, heights and weights in a combined histogram for comparitive analysis. We observed that the distributions are normally distributed both overall and within individual countries.
3. We used the 5 most common player positions and compared the player's age and player's potential with the condition that their overall be greater than 80 in order to get the most relevant player results. We observed that positions CM and LB are associated with younger ages. Players in position CB are associated with taller heights than average.
4. We used boxplots and scatter plots to observe the outliers in the data on the basis of nationality, potential and overall. Neymar, Ronaldo and Messi are clearly visible as outliers at the top of the plot.

### K Means Clustering
1. We implemented K means clustering algorithms in the following manner:

   - The function takes two paramters, the data and the value `k` for the number of means.
   - The clusters are allocated by randomly sampling `k` rows from the given data.
   - When the clusters converge or number of iterations exceed 10, the function terminates.
   - The Euclidean distance between each row and each mean is calculated, by squaring the distance between every column of the current row and current centroid. The centroid with the minimum distance is chosen as the cluster and the clusters array is updated.
   - The new centroids are assigned by calculating the mean of every cluster. The new values are compared to previous cluster values. If there is no change, or if there have been more than 10 iterations, the clusters are returned. This is because with such large datasets, the differences between consecutive means can be small, but still not zero.
   - The new centroids and cluster array is returned. Each row has a cluster assigned to it which will be used later in the scatterplot.

2. The clusters can be viewed in `./2/images` or in the `2.ipynb` file.
3. We used the elbow method to calculate the best number of clusters.
    - Here we take values of `k` from `2` to `10` and find the WCSS (Within Cluster Sum of Squares) for each k value. 
    - This is done by finding the Euclidean distance between the centroid of the cluster and the current row. 
    - The total distances are stored in the `total_distance` variable, and are later used for plotting the graph.
4. We have graphs for 3, 5, and 7 clusters and now we plot for 4 means as well because it is the optimal number of clusters. Upon observation, we can see that 3 and 5 clusters are divided optimally and the clusters make sense. In the case of 7, the clustering seems excessive and illogical. The best clustering is in the case of 4 means, and all the data appears divided in an effective manner. The area of the graph is covered, and each region is clearly defined.

### Hierarchical Clustering

1. We clustered the data using agglomerative clustering using scipy.cluster.hierarchy which uses agglomerative clustering. 
2. Divisive Clustering involves splitting the clusters based on other clustering algorithms such as k means, DB SCAN, etc.
3. We plotted the dendrogram and observed that the optimum number of clusters is 4 by observing the distance of the longest line in the dendrogram.


### DB Scan Clustering

1. We implemented DB Scan using `sklearn.cluster.DBSCAN`
2. Finding Epsilon:
   - We find the optimal epsilon value by plotting a k-distance graph. 
   - This involves finding the nearest neighbor for each data point and calculating the distance between those points, using the sklearn neighbors library.
   - These distances are sorted and plotted to find the best epsilon value.
  

    Finding min_samples:
   - After obtaining the epsilon value, we plot graphs with various values of min_samples.
   - Since we have roughly 47 features and 18000+ data points, we start with a value of 50, and keep increasing it to achieve the optimum number.
   - Since 50 only yields 2 clusters, we gradually increase it until we get 3 clusters at 500, and 4 at 1000.
   - From k means, we understood that 4 is the optimum number of clusters. Therefore we start fine tuning around 1000 to get the correct value.
   - The diagrams are similar for ranges from 850 - 1100 so we choose 1000 as min_samples.

3. 4 clusters were formed using the optimal values of epsilon and min_samples. The 4 samples seem to be grouped effectively, covering the entire region appropriately and demonstrating the different values and features of the data set. 


### Analysis
- All three methods agree that 4 is the optimum number of clusters, however the way these graphs are visualized are very different for each method.
- The K means method seems to give slightly different outputs everytime it is run, and does not ignore noise. On the other hand, agglomerative clustering gives consistent outputs, but it is still affected by noise. DB Scan seems most resistant to noise, by automatically grouping noise and irrelevant data points into separate clusters.
- Outliers are visible in all the methods of clustering during visualization, and can be differentiated from the data.
