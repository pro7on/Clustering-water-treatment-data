# Clustering-water-treatment-data





As we are dealing with attributes only the first column, day and date of data is dropped.
Firstly, we will find the missing values in data this is because many packages do not support converting or avoiding ‘?’ (what we have as missing value) while applying algorithm.
To do this we will replace ‘?’ in our data with NaN (depends on package being used) 
For imputation I have used KNN with missingpy package. 
![1](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/1.png)


For normalization now, the above imputed data with all values is passed and the formula mentioned in the description file is applied to each column, with a function defined.
In this, the dataset minmax gets all the max and min vales from the data and then passes it to the function normalize.
 ![2](https://github.com/pro7on/Clustering-water-treatment-data/blob/master/images/2.png)
