# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Load and preprocess data: Import data, inspect it, and handle missing values if any.
2. Determine optimal clusters: Use the Elbow Method to identify the number of clusters by plotting WCSS against cluster numbers.
3. Fit the K-Means model: Apply K-Means with the chosen number of clusters to the selected features.
4. Assign cluster labels to each data point.
5. Plot data points in a scatter plot, color-coded by cluster assignments for interpretation. 

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: MUKESH RAJ D
RegisterNumber:  212224100038
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv(r"C:\Users\admin\Downloads\Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++",n_init=10)
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters=5, n_init=10)
km.fit(data.iloc[:, 3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster1")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster2")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster4")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster5")
plt.legend()
plt.title("Customer Segments")
```

## Output:
<img width="757" height="275" alt="Screenshot 2026-02-25 154713" src="https://github.com/user-attachments/assets/add453f1-3cfd-4648-b4e2-14f9132e0939" />
<img width="634" height="334" alt="Screenshot 2026-02-25 154718" src="https://github.com/user-attachments/assets/c52b7980-2201-4938-b806-fe3a13444db7" />
<img width="428" height="188" alt="Screenshot 2026-02-25 154724" src="https://github.com/user-attachments/assets/ca5f8d95-444b-44ce-817e-3d9eccfa0a2f" />
<img width="1002" height="719" alt="Screenshot 2026-02-25 154731" src="https://github.com/user-attachments/assets/fd047f18-f842-4222-ab47-df2e84ba9b4f" />
<img width="861" height="247" alt="Screenshot 2026-02-25 154738" src="https://github.com/user-attachments/assets/2e3a64ad-3157-4a00-8f40-6f0fced5c595" />
<img width="863" height="606" alt="Screenshot 2026-02-25 154744" src="https://github.com/user-attachments/assets/85664e77-1b80-4708-846b-c47330561559" />



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
