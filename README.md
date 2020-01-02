# Clustering-water-treatment-data


###### 1. Clean up the data set, which includes filling up the missing values and normalizing all the data items
###### 2. Perform K-means algorithm on data set, propose a specific termination condition for the modified k-means when searching the true k-value
###### 3. Implement the modified k-means algorithm with the proposed termination condition and run the algorithm on water treatment data
###### 4. First, apply the PCA method to this dataset and then apply the implemented modified k-means method above to this reduced data set 
###### 5. Comparision of results between both the clusterings done(3 & 4)
###### Note: Files for 1,2,3 & 4 are different. 



# 1
As we are dealing with attributes only the first column, day and date of data is dropped.
Firstly, we will find the missing values in data this is because many packages do not support converting or avoiding ‘?’ (what we have as missing value) while applying algorithm.
To do this we will replace ‘?’ in our data with NaN (depends on package being used) 
For imputation I have used KNN with missingpy package. 
![1](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/1.png)


For normalization now, the above imputed data with all values is passed and the formula mentioned in the description file is applied to each column, with a function defined.
In this, the dataset minmax gets all the max and min vales from the data and then passes it to the function normalize.
 ![2](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/2.png)


# 2
So, to find out the true k-value to perform k-means, I used the elbow method which is quite common and accurate.
In K-mean to determine optimal number of clusters k, we can make use of elbow method which is a graphical tool to estimate the clusters, in this we notice that when k increases, the cluster within, what we call distortion decreases. Which is because the samples are closer from their centroids.
Below I have passed the input which has no missing values and is completely normalized.
![3](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/3.png)
 
In our case, first we set the range till 15 and we can see already that it gives probable values between 6 to 9.
![4](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/4.png)
 
Even, if we take the range further, we get some similar results.
Hence, this criterion can well be our termination condition we can visualize the clusters between 6 to 9, to see which gives out accurate results(We will do this in question 3).
 
 
 # 3
 
To implement the K-means we will follow the range which we got in the previous question which was 6 to 9.
We pass the input which has no missing values and is completely normalized.
First, we will see K means for 6 clusters with 200 iteration to get the most accurate results of all.
![5](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/5.png)
 
 
The output of passing 6 clusters to our dataset results in the clusters overlapping, as well as the centroids of all clusters are very close to each other(closer than their all datapoints).
Let us try, K means for 9 clusters with same numbe of iteration to get the most accurate results of all.
![6](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/6.png)

![7](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/7.png)

Here, we get the same results as the previous ones, i.e overlapping and centroids(big red dots) are closer again.
Let us go out of the way and try 3 clusters to see if our k-means outputs cleaner visual data.
 
![8](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/8.png)

The overlapping and centroids being too close still persists with 3 clusters.

# 4

After Imputation:

![9](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/9.png) 
Before we apply PCA to our data we will use Minmax scalar by sklearn to normalize the imputed data.
 
![10](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/10.png)
After that we will apply PCA to the rescaled data:

![11](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/11.png)
 

Here, we set the variance to be 90%, and we scatter plot the first two components.
And then just to make sure we will see explained variance for our components:
 
![12](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/12.png)
Variance for the first two components results to be the highest.
We will now again check the optimal number of clusters with the elbow method by taking to ranges:
 

![13](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/13.png)

 
With if both the range, we get some similar results i.e. range of optimal clusters between 4 to 6.
Again, we will see visualization of the range we got in the K-means.
First is plot with 4 clusters:


![14](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/14.png) 

And then with 6 clusters:

![15](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/15.png)

In 6 clusters, they overlap, also some of the clusters are not visible but centroids are.
But in 6 clusters, the 4th and 6th cluster centroids are very close to each other.
So, the best will be to choose 4 clusters for our dataset.

 # 5 
 Question5.
In questions 3, the result what we got by applying k-means had the centroid of clusters near each other as well as overlapping.
But in question 4 we got some better results i.e. not much overlapping and not close centroids compared to question 3 after applying PCA before K-means.
Firstly, PCA reduces dimensionality and doesn’t change the number of observations you have. Neither it changes the order of the data. 
if we compare both of their elbow method plots: 
![16](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/16.png)

![17](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/17.png)

 

We observe that the ranges of clusters of k-means and PCA with k-means were similar.
But in the plots our selected clusters for both have a huge difference:
![18](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/18.png)

![19](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/19.png)


The above plot in which PCA is applied first, we can see that by retaining 2 highest variance components, the clusters which were not visible in k-means without PCA, are visible now and also their centroids are distant as compared to the first plot.
This means that with PCA with clustering we successfully retained/revealed some of the cluster information and for this particular dataset PCA before clustering gives accurate results.

 
 
 
