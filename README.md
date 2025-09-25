### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 23-09-2025
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program 1:
python
import pandas as pd
df = pd.read_csv("/clustervisitor.csv")
print(df)
cluster = {"Young": (df['Age'] <= 30), "Middle": ((df['Age'] > 30) & (df['Age'] <= 50)), "Old": (df['Age'] > 50)}
count = []
for g, c in cluster.items():
  visitors = df[c]
  count.append(len(visitors))
  print(f"Visitors in {g} Group")
  print(visitors)
  print(count)



### Output:
![WhatsApp Image 2025-09-25 at 15 24 55_af3d3ab9](https://github.com/user-attachments/assets/37b5c687-fa12-4c8e-ae55-2eacfdc80825)




### Visualization:
python
import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.bar(cluster.keys(), count, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()

### Output:
![WhatsApp Image 2025-09-25 at 15 24 55_0cb9fe66](https://github.com/user-attachments/assets/2277c567-66c0-4ddc-8a60-1d662af86a96)



## Program 2:
python
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
df=pd.read_csv("/clustervisitor (Salary).csv")
df
sc=StandardScaler()
df1=df['Age']
df2=df['Salary']
df3=pd.concat([df1,df2],axis=1)
newdf=sc.fit_transform(df3)
newdf
newdf=sc.fit_transform(df[['Age','Salary']])
newdf
kmeans=KMeans(n_clusters=3,random_state=42)
df3['cluster']=kmeans.fit_predict(newdf)
df3

## Output:
![WhatsApp Image 2025-09-25 at 15 24 56_8045daae](https://github.com/user-attachments/assets/fd2d990e-8823-4c18-8539-23425a57d412)



## Visualisation:
python
plt.scatter(df3['Age'],df3['Salary'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Salary in thousands')
plt.show()

## Output:
![WhatsApp Image 2025-09-25 at 15 24 55_1d2f2b93](https://github.com/user-attachments/assets/04c89367-1d37-4658-b445-e88696e5c5f5)



### Result:

Thus the Implementation of Cluster and visitor segmentation for Navigation patterns is executed successfully.
