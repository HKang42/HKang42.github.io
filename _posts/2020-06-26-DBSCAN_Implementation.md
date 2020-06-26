---
layout: post
title: DBSCAN Clustering
subtitle: What is it and how does it work?
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
bigimg: https://www.uclaextension.edu/sites/default/files/styles/certificate_hero/public/2018-06/data-science-fos-header.jpg?itok=g7dXCLdQ
tags: [DBSCAN]
comments: true
---

DBSCAN has been a popular clustering algorithm that has stood the test of time. Introduced in 1996, its density-based approach to clustering compared to other methods like k-means has ensured it's continued relevance.

&nbsp;

## What is clustering?

To understand the significance of DBSCAN, a solid grasp of clustering problems is required. Clustering refers to methods that look at data points and group them in some manner. A common and intuitive approach to this problem is to use centroid-based clustering. This algorthim can be easily understood with the figure below which depicts a popular clustering algorithm called "K-Means". At the basic level, centroid clustering works by guessing many groups the points fall into, and then letting a computer group points by minimizing the distance between each point and the center of its cluster (the centroid). 

![KMeans_Example](/img/DBSCAN_Figure_1.png){: .center-block :}

<font size="2"> *The above examples was taken from an article that provides an in-depth explanation of k-means centroid clustering, [K-means Clustering: Algorithm, Applications, Evaluation Methods, and Drawbacks](https://towardsdatascience.com/k-means-clustering-algorithm-applications-evaluation-methods-and-drawbacks-aa03e644b48a).</font>

Unfortunately, methods like these have a few shortcomings. For example, what happens if you don't know how many clusters there should be? What happens if the points follow a pattern that can't be made using centroids? What about outliers that shouldn't be placed in a cluster? The figure below illustrates a few different patterns where K-means succeeds or fails to create good clusters.

![KMeans_Patterns](/img/DBSCAN_Figure_2.png){: .center-block :}

K-means fails with the concentric circle example (top row) because centroid clustering algorithms cannot handle patterns where clusters can't be linearly separated. There is no series of lines that can separate the two circles. This means we need a fundementally different approach if we want to cluster these types of patterns.  Enter DBSCAN.
&nbsp;

## The DBSCAN Algorithm

Instead of using the distance between points and centroids, DBSCAN uses the distances between the points themselves. How does it work?  

 - Pick an arbitrary starting point and looks for neighboring points. 
 
 - If there are very few or no nearby points, then that point is labeled as noise. 
  
 - If there are many nearby points, then mark the group as a cluster. 
   
 - Check each nearby point and sees if they have neighboors. 
 
 - If they do have neighbors, then the cluster is expanded. 
  
 - Repeatedly grow the cluster until there are no more neighbors. 
 
 - Then choose a different starting point and repeat the process.

Below is an image depicting the DBSCAN algorithm on a small data set with 1 cluster of points and 1 noise point. Notice that regardless of which point the cluster starts from, it will continually expand until it reaches points B and C. What do you think the circles represent?

![DBSCAN_Algorithm](https://en.wikipedia.org/wiki/DBSCAN#/media/File:DBSCAN-Illustration.svg)

The steps outlined above contain almost everything you need to implement a DBSCAN algorithm. The final piece of information needed is to define what "many nearby points" means. In other words, what's the threshold for whether or not a point has enough neigbhors to be considered a cluster?

To answer this question the 2 parameters are used, epsilon and a minimum number of points. Epsilon is the max distance 2 points can be away from each other. The higher the value, the more spread out points can be and still count as a cluster. Minimum number of points is simply the threshold for how many connections are needed for a point to grow a cluster. A higher value here means that points more neighbors to count as a cluster.

Basically, DBSCAN looks at point density to determine whether or not to create and grow a cluster. Density has 2 components, the amount of stuff in a space and the size of the space.  Epsilon represents the size of the space. So a high epsilon means a low density requirement. The minimum point threshold represents the amount of stuff. A high threshold means a high density requirement.

Lastly, an important consideration that hasn't been explicitly mentioned are outliers or noise data. In contrast to the K-Means algorithm, the DBSCAN algorithm does NOT try to assign every data point a cluster. This means that noisy data or data with outliers can be easily handled by DBSCAN


So how effective is DBSCAN? Let's see how it handles the same patterns we tested K-means on.

![DBSCAN_Comparison](/img/DBSCAN_Figure_4.png){: .center-block :}


### Implementation considerations

Now that you understand the algorithm, what's there to stop you from writing your own DBSCAN?

Things are easy for small data sets. But efficiency becomes a very big problem for moderate and large data sets.


### When to use
NOISE

be careful of high dimentionality or be prepared to combat the curse of dimentionality. Perhaps consider using non-euclidean distance measures 

[Here's a link to the code I used to generate the plots](https://github.com/HKang42/DS-Unit-1-Build/blob/master/COVID_19_Project.ipynb)
