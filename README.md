# KNN-Search-Techniques-in-High-Dimension


Mainly Consists:
  1) Brute Force Search
  2) K-d Tree Search 
  3) Ball-Tree Search


(which WORKS BETTER)

LOW DIMENSION DATA: Ball-Tree Search > K-d Tree Search > Brute Force Search 
HIGH DIMESION DATA: Brute Force Search > Ball-Tree Search > K-d Tree Search 







Brute Force Search :

 It is an explicit search teachnique & takes very long to execute. Basic Nearest Neighbour Search is "Lazy Learner" & execute all distances while testing.
 No calculations while Training Time. This technique has a worst case Time Complexity Of O(ND^2) , where N= number of examples in training data, D= dimension of my data.( so to say no of features).
 TO OVERCOME THIS SLOW TECHNIQUE, K-D TREE IS BETTER. IT takes less time. TIME complexity O( D x Nlog(N) ). 











KD-Tree algorithm and the Ball algorithm are both binary algorithms to build such a tree. Binary means in this context, that each parent node only has two child nodes. Typically the algorithms are applied in Nearest Neighbour Search.









K-d Tree :

The KD Tree Algorithm is one of the most commonly used Nearest Neighbor Algorithms. The data points are split at each node into two sets. Like the previous algorithm, the KD Tree is also a binary tree algorithm always ending in a maximum of two nodes. The split criteria chosen are often the median. On the right side of the image below, you can see the exact position of the data points, on the left side the spatial position of them.






Ball-Tree:

The Ball Tree Algorithm can be contemplated as a metric tree. Metric trees organize and structure data points considering the metric space in which the points are located. Using metrics the points do not need to be finite-dimensional or in vectors (Kumar, Zhang & Nayar, 2008).
The algorithm divides the data points into two clusters. Each cluster is encompassed by a circle(2D) or a sphere(3D). The sphere is often called a hypersphere.

From the sphere form of the cluster, the name Ball tree algorithm is derived. Each cluster represents a node of the tree. Let’s see how the algorithm is executed.
The children are chosen to have maximum distance between them, typically using the following construction at each level of the tree.
First, the centroid of the whole cloud of data points is set. The point with the maximum distance to the centroid is selected as the center of the first cluster and child node. The point furthest away from the center of the first cluster is chosen as the center point of the second cluster. All other data points are then assigned to the node and cluster to the closest center, either being cluster 1 or cluster 2. Any point can only be a member of one cluster. The sphere lines can intersect each other, but the points must be clearly assigned to one cluster. If a point is exactly in the middle of both centers and has followingly the same distance to both sides, it has to be assigned to one cluster. The clusters can be unbalanced. That is basically the concept behind the Ball Tree Algorithm. The process of dividing the data points into two clusters/spheres is repeated within each cluster until a defined depth is reached. This leads to a nested cluster containing more and more circles.












COMPARISON & SUMMERY :

Brute Force may be the most accurate method due to the consideration of all data points. Hence, no data point is assigned to a false cluster. For small data sets, Brute Force is justifiable, however, for increasing data the KD or Ball Tree is better alternatives due to their speed and efficiency.
The KD-tree and its variants can be termed “projective trees,” meaning that they categorize points based on their projection into some lower-dimensional space. (Kumar, Zhang & Nayar, 2008)
For low-dimensional data, the KD Tree Algorithm might be the best solution. As seen above, the node divisions of the KD Tree are axis-aligned and cannot take a different shape. So the distribution might not be correctly mapped, leading to poor performance.
For a high-dimensional space, the Ball Tree Algorithm might be the best solution. Its performance depends on the amount of training data, the dimensionality, and the structure of the data. Having many data points that are noise can also lead to a bad performance due to no clear structure.



BUT IN HIGH DIMENSION(ABOVE 60) :

ALL THESE CONCEPTS IS BASICALLY NOT VALID. IN HIGH DIMENSION, BRUTE FORCE SEARCH WORKS FAR BETTER THAN OTHER.

HERE COMES WHY & HOW ?

Modern days , computers have multicore processors, which are capable to computing multiple tasks in parallel.
LETS OUR DATASET DIMENSION IS 100. D=100
THINK : BRUTE FORCE ABLE TO CALCULATE say, 100 distances in parallel ( single iteration) where as earlier it was calculating 100 different diatances for single iteration.
        Now it takes way less time.
        
THEN WHY NOT BALL-TREE & K-D TREE ?

these are binary search techniques, they first seperate the dimension into regions & then calculate distances in those smaller regions.
with multicore also, they cant directly compute distances.

This makes K-d tree, ball tree slow in high dimension.
