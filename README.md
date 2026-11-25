# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1. Import the required libraries and load the customer dataset.
2. Preprocess the data and select the required features for clustering.
3. Apply the K-Means Clustering algorithm by selecting the number of clusters (K).
4. Group customers into clusters and visualize the results using a scatter plot.
   

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Litya M
RegisterNumber:  212225230152
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
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="pink",label="cluster5")
plt.legend()
plt.title("Customer Segments")
```

## Output:
<img width="967" height="646" alt="Screenshot 2026-11-25 131727" src="https://github.com/user-attachments/assets/59d32f97-eda2-4341-89a5-016beed43868" />
<img width="933" height="287" alt="Screenshot 2026-11-25 131735" src="https://github.com/user-attachments/assets/cf9d7eb6-be0e-4549-9862-0ad22cb60e9d" />
<img width="907" height="611" alt="Screenshot 2026-11-25 131743" src="https://github.com/user-attachments/assets/4bf53abe-75c2-4158-8bfd-8f49568ddeb6" />
<img width="890" height="706" alt="Screenshot 2026-11-25 131751" src="https://github.com/user-attachments/assets/919790e5-bd36-4c67-becf-a7c96ed2ddce" />


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
