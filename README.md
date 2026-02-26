# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1. Load the customer dataset and select relevant features such as Annual Income and Spending Score.
2. Determine the optimal number of clusters using the Elbow Method by computing WCSS for different values of *k*.
3. Initialize the K-Means algorithm with the chosen number of clusters and fit it to the dataset.
4. Assign each customer to the nearest cluster centroid based on distance.
5. Visualize the formed clusters to analyze and interpret customer segments.


## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Jayasri L
RegisterNumber: 212224040136 
*/
```

```
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

data = pd.read_csv("/content/Mall_Customers.csv")

print(data.head())

print(data.info())

print(data.isnull().sum())

wcss = []

for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++", random_state=42)
    kmeans.fit(data.iloc[:, 3:5])   
    wcss.append(kmeans.inertia_)

plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()

km = KMeans(n_clusters=5, init="k-means++", random_state=42)
km.fit(data.iloc[:, 3:5])

y_pred = km.predict(data.iloc[:, 3:5])

data["cluster"] = y_pred

df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]

plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c="red", label="Cluster 0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c="black", label="Cluster 1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c="blue", label="Cluster 2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c="green", label="Cluster 3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c="magenta", label="Cluster 4")

plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.title("Customer Segments")
plt.legend()
plt.show()

```

## Output:
<img width="1220" height="540" alt="image" src="https://github.com/user-attachments/assets/836bd714-2de8-4a39-b430-f7be9bb74144" />

<img width="1019" height="935" alt="image" src="https://github.com/user-attachments/assets/14dc5be0-817b-44ff-b4c0-1b8d9dc5507d" />

<img width="1084" height="880" alt="image" src="https://github.com/user-attachments/assets/5020d34b-ed29-4c22-8af4-1b08c3cb4ad4" />

<img width="1283" height="452" alt="image" src="https://github.com/user-attachments/assets/14ca1e22-8359-4021-b9bb-fdf095e4ea18" />

<img width="1230" height="895" alt="image" src="https://github.com/user-attachments/assets/ab077288-ede6-475b-8587-ea1602cab54e" />





## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
