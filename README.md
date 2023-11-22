# UNSUPERVISED LEARNING ALGORITHMS

## Some Common Terminologies

**Supervised vs. Unsupervised Learning:** The main difference between supervised and unsupervised learning is their goals. Supervised learning needs concrete, ground-truth labels to train models that answer very specific questions. Unsupervised learning differs in that the task it is trying to accomplish is much less well-defined - it can usually be summed up as "are there any natural patterns in this data that are recognizable?"

**The curse of dimensionality** is a general mathematical problem relating to the exploding size of space as you continue to add additional dimensions. This can be particularly problematic when dealing with large datasets. The more features you have, the more data you have about the scenario, but the more difficult it might be to exhaustively explore combinations of these features.

## Unsupervised Learning Techniques

**Clustering:** Clustering groups data into homogeneous groups, where members share common traits. One common use case for clustering is market segmentation. In market segmentation, you would try to decompose an audience into subsets for more precise targeting for business purposes, such as advertising. Even though there's no way to verify that these groups are correct, in practice it usually does quite well, often providing useful subgroups which can then be individually examined.

**Dimensionality Reduction:** attempts to reduce the overall number of features of a dataset while preserving as much information as possible. The most common dimensionality reduction algorithm is **Principal Component Analysis (PCA)**. Dimensionality reduction algorithms work by projecting data from its current n-dimensional subspace into a smaller subspace, while losing as little information as possible in the process. Dimensionality reduction algorithms still lose some information, but you can quantify this information loss to make an informed decision about the number of dimensions reduced versus the overall information lost. The curse of dimensionality is a key concept as datasets scale. In short, as the number of features in a dataset increases, the processing power and search space required to optimize a given machine learning algorithm explodes exponentially. Because this often creates intractable computational problems, dimensionality reduction techniques such as PCA can be an essential preprocessing technique.

# PRINCIPAL COMPONENT ANALYSIS
PCA is an unsupervised learning technique that does not require labeled data.
It is also a dimensionality reduction technique that can be used to compress data and experiment with its effects on machine learning algorithms as a preprocessing step.
There are four steps to conducting PCA:
  - Center each feature by subtracting the feature mean
  - Calculate the covariance matrix for your normalized dataset
  - Calculate the eigenvectors/eigenvalues for the covariance matrix
     -  Reorder your eigenvectors based on their accompanying eigenvalues (in descending order of the eigenvalues)
  - Take the dot product of the transpose of the eigenvectors with the transpose of the normalized data

![image](https://github.com/MarvinAgumba/UNSUPERVISED-LEARNING-TECHNIQUES-WALKTHROUGH/assets/122484885/c24afe01-70e4-4655-ba6e-93a263ecaaae)

Datasets used for PCA illustrations (Iris; Otto & Food USA Datasets)

# CLUSTERING
**Clustering techniques** are very powerful when you want to group data with similar characteristics together, but have no pre-specified labels. The main goal of clustering is to create clusters that have a high similarity between the data belonging to one cluster while aiming for the minimal similarity between clusters. Most popular and widely-used clustering algorithms, **`K-means clustering`**, **`hierarchical agglomerative clustering`**, **`Semi-Supervised Learning and Look-Alike Models`**

**K-Means Advantages**: Very easy to implement; With many features, k-means is usually faster than HAC; Objects are locked into the cluster they are first assigned to and can change as the centroids move around; Clusters are often tighter than those formed by HAC

**K-Means Disadvantages**: The quality of results depends on picking the right value for $k$, This can be a problem when we don't know how many clusters to expect in our dataset; Scaling our dataset will completely change the results; Initial start of points of each centroid has a very strong impact on our final results. A bad start point can cause sub-optimal clusters

**HAC Advantages**: It produces an ordered relationship between clusters, which can be useful when visualized; Smaller clusters are created. This allows us to get a very granular understanding of our dataset, and zoom in at the level where the clusters make the most sense to us

**HAC Disadvantages**: Results are usually dependent upon the distance metric used; Objects can be grouped 'incorrectly' early on, with no way to relocate them. For instance, consider two points that belong to separate clusters, but are both nearer to each other than the center of the cluster they actually belong to (both are near the "boundary" between their cluster and the opposing cluster). These will be incorrectly grouped as a cluster, which will throw off the clustering of the groups they actually belong to, as well

K-Means Clustering Sample Model
![image](https://github.com/MarvinAgumba/UNSUPERVISED-LEARNING-TECHNIQUES-WALKTHROUGH/assets/122484885/da6f3473-b713-477e-aeef-0599d435d8c7)

Hierarchical Agglomerative Clustering Dendogram Sample
![image](https://github.com/MarvinAgumba/UNSUPERVISED-LEARNING-TECHNIQUES-WALKTHROUGH/assets/122484885/e05dda30-346c-485d-b443-ec4d107bba8e)

# CHECKING MODEL PERFORMANCE PARAMETERS SCORES

**Adjusted Rand Index** computes a similarity measure between two different clusterings by considering all pairs of samples and counting pairs that are assigned in the same or different clusters predicted, and the true clusterings, before adjusting for random chance. Note that the true labels must be known for this metric to be used. The Adjusted Rand index is bounded between -1 and 1. Closer to 1 is good, while closer to -1 is bad.

**Fowlkes-Mallows score** measures the similarity for two clusters as a set of points by calculating the geometric mean between precision and recall. Note that the true labels must be known for this metric to be used. This score is bounded between 0 and 1. Closer to 1 is better.

**Calinski-Harabasz Index** variance ratio measurement which measures the ratio between within-cluster dispersion and between-cluster dispersion. You'll often hear this metric referred to as "variance ratio". This score is not bounded. The higher, the better.

**Silhouette coefficient** calculated using the mean intra-cluster distance, as well as the mean distance to the nearest cluster for each sample in the dataset. Note that the function below returns the mean Silhouette score for all samples, but you can also use it to get the Silhouette coefficient for a single point, in case you want to judge the fit of a single point in a cluster. This metric is bounded between -1 and 1. Closer to -1 suggests incorrect clustering, while closer to +1 shows that each cluster is very dense.


