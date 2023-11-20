# Customer Segmentation on Retail Supermarket data

#### We apply the following techniques in Supermarket Purchase data.
* Customer Segmemtation
* Cluster Profiling
* Classify the segment of new data

### Description of the Use Case
Customer segmentation involves partitioning and categorizing a customer base into distinct groups based on similar characteristics, behaviors, or preferences. In the context of Retail Supermarket Purchase Data, segmentation enables retailers to identify and understand different customer segments with unique purchasing patterns. 

We will apply clustering algorithm, specifically K-means on features such as customer demographics, spendings and product purchases so that retailers can categorize customers into groups. Customer Segmentation allows retailers to tailor marketing strategies, optimize product offerings, and enhance the overall shopping experience for each segment. 

For instance, high-spending customers might receive personalized promotions, while occasional shoppers could be targeted with incentives to increase their purchases. Customer segmentation thus serves as a valuable tool for retailers to optimize resource allocation, improve customer satisfaction, and drive overall business growth.




#### Connect Python to Postgresql
* We import data from Postgresql to Python.


~~~ python
import pymongo

# Connect to MongoDB Compass.
client = pymongo.MongoClient('localhost', 27017)

# Get the Reviews database.
db = client['Reviews']

# Get the rentedclothing_reviews collection.
collection = db['rentedclothing_reviews']

# Show the first few documents in the rentedclothing_reviews collection.
for document in collection.find().limit(2):
    print(document)
~~~

Below is the  Retail Supermarket Purchase data output.

![alt text](https://github.com/KarlRetumban/CS/blob/main/images/data.JPG)

### Standardizing or Scaling Data
The customer groceries retail purchase data is preprocessed by standardizing the features through data scaling. Utilizing the StandardScaler from scikit-learn, the data is transformed to have a mean of 0 and a standard deviation of 1, ensuring that features with varying scales contribute equally. This preprocessing step is crucial for the effectiveness of clustering algorithms, such as K-means, as it ensures that all variables are on a comparable scale.

~~~ python
# Data Scaling
scaler = StandardScaler()
scaler.fit(groceries_dta)
groceries_scaled = pd.DataFrame(scaler.transform(groceries_dta),columns= ds.columns )
print("The data is successfulluy scaled")
~~~

![alt text](https://github.com/KarlRetumban/CS/blob/main/images/scaled.JPG)



### Determine optimal number of cluster
The optimal number of clusters for customer segmentation is determined through the K-means Elbow method. By employing the KElbowVisualizer from the Yellowbrick library, the algorithm is fitted to the data with varying cluster numbers. The resulting visualization allows for the identification of the "elbow" point, indicating the optimal number of clusters. This crucial step aids in selecting a meaningful value for 'k' that captures inherent patterns in the data.

~~~ python
# Determine the optimal number of clusters using the K-means Elbow method
print('Elbow Method to determine the number of clusters to be formed:')
Elbow_M = KElbowVisualizer(KMeans(), k=8)
Elbow_M.fit(groceries_scaled)
Elbow_M.show()
~~~

![alt text](https://github.com/KarlRetumban/CS/blob/main/images/elbow.JPG)



### Segmenting the data using K-means Algorithm
Applying the K-means clustering algorithm with the determined optimal number of clusters, the customer data is partitioned into distinct segments. The KMeans algorithm assigns each customer to one of the clusters based on their deographics and purchasing behavior. The assigned clusters are then added to the original data, providing a comprehensive overview of customer segments. This step is fundamental for subsequent customer profiling and targeted marketing strategies.

~~~ python
# K-means Algorithm
from sklearn.cluster import KMeans

k = 5
kmeans = KMeans(n_clusters=k)
y_clusters = kmeans.fit_predict(groceries_scaled)

#Add the assigned clusters to the data
groceries["Clusters"] = y_clusters
~~~

![alt text](https://github.com/KarlRetumban/CS/blob/main/images/clusters.JPG)


### Customer Profiling
With the clustered data, customer profiling involves gaining insights into each segment's characteristics. By analyzing the spending patterns, preferred product categories, or any other relevant features within each cluster, retailers can tailor marketing efforts and enhance customer engagement. This process facilitates the creation of targeted strategies, such as personalized promotions or product recommendations, maximizing customer satisfaction and overall retail performance.


![alt text](https://github.com/KarlRetumban/CS/blob/main/images/clusters.PNG)

