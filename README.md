# Implementation-of-K-Means-Clustering-for-Customer-Segmentation
## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.
## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook
## Algorithm
```
step 1:start
step 2:Import the necessary packages using import statement.
step 3:Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().
step 4:Import KMeans and use for loop to cluster the data.
step 5:Predict the cluster and plot data graphs.
step 6:Print the outputs and end the program
step 7:End
```
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: MONISH S
RegisterNumber:  212223040115
*/
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("C:/Users/ANANDAN S/Documents/ML labs/Mall_Customers.csv")
data.head()
data.tail()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = []#within cluster sum of squares
#it is the sum of squared distance between each point &the centroid in a cluster
for i in range (1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
    
    
plt.plot(range(1,11),wcss)
plt.xlabel("No.of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```
## Output:
```
Elbow method:
```
![Screenshot 2024-09-30 111548](https://github.com/user-attachments/assets/8a954dfb-308e-4f2d-8704-185975e16699)
```
y_pred value:
```
![Screenshot 2024-09-30 111556](https://github.com/user-attachments/assets/0850cab4-9dde-4582-9d25-102cedc92ca6)
```
scatter plot of cluster:
```
![Screenshot 2024-09-30 111608](https://github.com/user-attachments/assets/47de30d4-7d61-4d27-bbbc-66c781e7ae50)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
