# Basic Implementation of the DBSCAN clustering algorithm.

DBSCAN has been a popular clustering algorithm that has stood the test of time. Introduced in 1996, its density-based approach to clustering compared to other methods like k-means has ensured it's continued relevance.

## What is clustering?

To understand the significance of DBSCAN, a solid grasp of clustering problems is required. Clustering refers to methods that look at data points and group them in some manner. A common and intuitive approach to this problem is to use centroid-based clustering. This algorthim can be easily understood with the figure below which depicts a popular clustering algorithm called "K-Means". At the basic level, centroid clustering works by guessing many groups the points fall into, and then letting a computer group points by minimizing the distance between each point and the center of its cluster (the centroid). 

# Figure 1: How does K-Means work

The above examples was taken from an article that provides an in-depth explanation of k-means centroid clustering https://towardsdatascience.com/k-means-clustering-algorithm-applications-evaluation-methods-and-drawbacks-aa03e644b48a

Unfortunately, methods like these have a few shortcomings. For example, what happens if you don't know how many clusters there should be? What happens if the points follow a pattern that can't be made using centroids? What about outliers that shouldn't be placed in a cluster? The figure below illustrates a few different patterns where K-means succeeds or fails to create good clusters.

# Figure 2: Performance of K-Means on different patterns

K-means fails with the concentric circle example (top row) because centroid clustering algorithms cannot handle patterns where clusters can't be linearly separated. There is no series of lines that can separate the two circles. This means we need a fundementally different approach if we want to cluster these types of patterns.  Enter DBSCAN.

## The DBSCAN Algorithm

Instead of using the distance between points and centroids, DBSCAN uses the distances between the points themselves. How does it work?  

 - Pick an arbitrary starting point and looks for neighboring points. 
 
 - If there are very few or no nearby points, then that point is labeled as noise. 
  
 - If there are many nearby points, then mark the group as a cluster. 
   
 - Check each nearby point and sees if they have neighboors. 
 
 - If they do have neighbors, then the cluster is expanded. 
  
 - Repeatedly grow the cluster until there are no more neighbors. 
 
 - Then choose a different starting point and repeat the process.


So how effective is DBSCAN? Let's see how it handles the same patterns we test K-means on.
# Figure 3: Performance of K-Means and DBSCAN
^ maybe move this down?

By using these basic steps, DBSCAN is able to handle non-linear boundaries between clusters. Of course, there's still one important consideration, what's the threshold for whether or not a point has enough neigbhors to be considered a cluster?

To answer this, the user provides 2 parameters, epsilon and a minimum number of points. Epsilon is the max distance 2 points can be away from each other. The higher the value, the more spread out points can be and still count as a cluster. Minimum number of points is simply the threshold for how many connections are needed for a point to grow a cluster. A higher value here means that points more neighbors to count as a cluster.

Basically, DBSCAN looks at point density to determine whether or not to create and grow a cluster. Density has 2 components, the amount of stuff in a space and the size of the space.  Epsilon represents the size of the space. So a high epsilon means a low density requirement. The minimum point threshold represents the amount of stuff. A high threshold means a high density requirement.

Lastly, an important consideration that hasn't been explicitly mentioned are outliers or noise data. In contrast to the K-Means algorithm, the DBSCAN algorithm does NOT try to assign every data point a cluster. This means that noisy data or data with outliers can be easily handled by DBSCAN

### Implementation considerations

Now that you understand the algorithm, what's there to stop you from writing your own DBSCAN?

Things are easy for small data sets. But efficiency becomes a very big problem for moderate and large data sets.


### When to use
NOISE

be careful of high dimentionality or be prepared to combat the curse of dimentionality. Perhaps consider using non-euclidean distance measures 
