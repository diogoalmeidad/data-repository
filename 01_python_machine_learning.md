# Theory ✍🏻
- [Clustering Algorithms](https://towardsdatascience.com/the-5-clustering-algorithms-data-scientists-need-to-know-a36d136ef68): Classify data points into specific groups based on similarity. It belongs to the unsupervised learning field.
- The algorithms available are:
- - K-Means Clustering:
    First: we select the number of groups to use (K);
    Second: we initialize the center points of the groups;
    Third: each datapoint is classified by calculating the distance from the point to each group center. It is assigned to the group to which it is the closets;
    Fourth: Based on the points assigned, recalculate the group center by taking the mean of all the vectors in the group;
    Fifth: Repeat for a set number of iterations
    Pros: Fast
    Cons: Selecting K | Having to randomize the center locations can lead to different locations
- DBSCAN (Density-Based Spatial Clustering of Applications with Noise):
    First: Begin arbitrarily by selecting a data point and assign who are the neighborhoods based on a distance epsilon;
    Second: If there are enough points, create a cluster. Else, it is labeled as noise;
    Third: A new unvisited point is processed, leading to a further cluster or noise.
    Pros: No pre-requisite of K | Identifies outliers
    Cons: If clusters are of varying density it doesn't work well
  Agglomerative Hierarchical Clustering:
    First: treat every data point as a single cluster;
    Second: Based on a distance metric measure distance between two clusters and combine the two closest clusters;
    Third: Repeat until we reach the root of the tree (one cluster with all data points)
    Fourth: Select how many clusters we want
  
