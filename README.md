1. Getting to know the data:
   
  The dataset contains four columns in total. 
  First, we have the student’s overall engagement in the minutes_watched column. Next up is the CLV, or customer lifetime value, followed by the geographical region, where the mapping is as follows:
![Screenshot 2024-04-01 145520](https://github.com/ElitsaKal/Customer-Segmentation-with-Hierarchical-Clustering-and-K-means/assets/162779608/6c7b3588-4094-416f-b902-62fd2bd7b498)
 
  The last column, channel contains results from the onboarding survey and the answer to the question, “How did you hear about us?” Note the mapping below:
  
![Screenshot 2024-04-01 145543](https://github.com/ElitsaKal/Customer-Segmentation-with-Hierarchical-Clustering-and-K-means/assets/162779608/d8f2df7c-717d-4950-80fc-0a58014caea7)

2. Data processing and feature engineering:
   
  After dealing with missing values (109) in this data we also create dummy variables for the country and channels column, as they are categorical.

3. Data visualization and correlation analysis:

   Before proceeding with the customer segmentation we perform statistical analysis to check on correlations in the data and data distribution.
   We do so, using a correlation heatmap and a scatter plot on minutes watched and CLV (Customer Lifetime Value).
![corr](https://github.com/ElitsaKal/Customer-Segmentation-with-Hierarchical-Clustering-and-K-means/assets/162779608/30cff576-36fa-4c7f-944c-5c31b74368f9)

![scatter](https://github.com/ElitsaKal/Customer-Segmentation-with-Hierarchical-Clustering-and-K-means/assets/162779608/a77e4977-cb1f-4b36-a0fb-0f40970f8f9c)
4. Hierarchical clustering:

After performing data standardization with StandardScaler, we can finally utilize the necessary clustering techniques, starting with hierarchical clustering. 
We use Ward’s method for distance and obtain 8 clusters from the hierarchical clustering.
![hierarchical](https://github.com/ElitsaKal/Customer-Segmentation-with-Hierarchical-Clustering-and-K-means/assets/162779608/dad3f690-9b56-4540-bfa3-92975ba67a23)
5. K-means clustering: 

In this step we implement the k-means algorithm. We perform an iteration with 10 steps, utilizing the k-means++ as the initializer. We've set the random state to 42
![line_chart](https://github.com/ElitsaKal/Customer-Segmentation-with-Hierarchical-Clustering-and-K-means/assets/162779608/26bbf95d-2d2f-4a70-a437-1b1f17c3714c)
   If we use the elbow method, we observe that the results of the k-means algorithm point to two, four, or nine different clusters. 
   These results differ from the eight clusters found by the hierarchical clustering with the elbow method.

6. Choosing the "right" number of clusters and discussion:

   In this case, we’ll opt for the hierarchical clustering results and apply them in the k-means—i.e., perform k-means clustering with eight clusters and analyze the resulting clusters using a summary table.
   But first, let’s justify why we opt for this approach instead of choosing the results of the k-means and also discuss why we’ve obtained such vastly different results from both techniques.
   Analysing the results: Note the following reasons why k-means and hierarchical clustering might suggest different numbers of clusters.
   Different methodologies: Hierarchical clustering builds a tree (or dendrogram) of clusters by successively splitting or merging them. The decision to split or merge can be based on various algorithms and 
   criteria. 
   On the other hand, k-means tries to find a predetermined number of clusters (k) that minimizes the within-cluster variance.
   Initial setup sensitivity: K-means is highly sensitive to initial starting conditions—i.e., the initial placement of the centroid of each cluster. Different runs give different results.
   Hierarchical clustering is deterministic and will always provide the same result with the same data.
   Cluster shape: K-means works best with spherical and evenly sized clusters. It might not do a good job if the clusters have irregular shapes, varying sizes, or densities.
   Hierarchical clustering does not have these assumptions.
   Finally, we opt for hierarchical clustering results because it can determine the number of clusters for you, whereas k-means doesn’t, and it’s up to us to choose them with such techniques as the elbow method.
   But in cases where we have too many data points, we can no longer rely on hierarchical clustering because it’s too inefficient. 
   With this analysis, it’s essential to note that this is the field of unsupervised machine learning where the correct answer isn’t known in advance.
   The ideal number of clusters heavily depends on the data, features used, distance measured, and the specific clustering algorithm. Hierarchical and k-means clustering are different techniques that may produce 
   different results. 
   And note that the ideal world has no empirical meaning—i.e., the perfect number of segments might be eight in our case but two for other applications.
