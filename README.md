# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1. Choose the number of clusters (K).
   
2.Initialize cluster centroids.

3.Assign data points to clusters.

4.Update cluster centroids.

5.Repeat steps 3 and 4.

6.Evaluate the clustering results.

7.Select the best clustering solution.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: T.LISIANA
RegisterNumber: 212222240053 
*/


import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
  kmeans = KMeans(n_clusters = i, init = "k-means++")
  kmeans.fit(data.iloc[:, 3:])
  wcss.append(kmeans.inertia_)
  
plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])

y_pred = km.predict(data.iloc[:, 3:])
y_pred

data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c = "red", label = "cluster0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c = "black", label = "cluster1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c = "blue", label = "cluster2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c = "green", label = "cluster3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c = "magenta", label = "cluster4")
plt.legend()
plt.title("Customer Segments")

```

## Output:
## data.head():
![image](https://github.com/lisianathiruselvan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119389971/a99b007f-412b-4184-8c46-311d2306d1e1)


## data.info():
![image](https://github.com/lisianathiruselvan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119389971/405d5672-72b9-47f3-895f-80afdd51f4c9)

## NULL VALUES:
![image](https://github.com/lisianathiruselvan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119389971/619af637-1984-4b86-ac02-6fec79d96a98)


## ELBOW GRAPH:
![image](https://github.com/lisianathiruselvan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119389971/2a8e6709-389a-4e22-bf29-ff0ae8d640d6)


## CLUSTER FORMATION:
![image](https://github.com/lisianathiruselvan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119389971/6ebd4ea0-949e-4baa-bc20-53c6175b85ab)


## PREDICICTED VALUE:
![image](https://github.com/lisianathiruselvan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119389971/a0ef4355-0258-45ba-961f-d345a2fc44c1)


## FINAL GRAPH(D/O):
![image](https://github.com/lisianathiruselvan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119389971/ba759730-129b-4022-a064-4133acedca37)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
