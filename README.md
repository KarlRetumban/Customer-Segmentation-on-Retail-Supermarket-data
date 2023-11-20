# Customer Segmentation on Retail Supermarket Purchase data

#### We apply the following techniques in Supermarket Purchase data.
* Customer Segmemtation
* Cluster Profiling
* Classify the segment of new data

### Description of the Use Case
Customer segmentation involves partitioning and categorizing a customer base into distinct groups based on similar characteristics, behaviors, or preferences. In the context of Retail Supermarket Purchase Data, segmentation enables retailers to identify and understand different customer segments with unique purchasing patterns. 

We will apply clustering algorithm, specifically K-means on features such as customer demographics, spendings and product purchases so that retailers can categorize customers into groups. Customer Segmentation allows retailers to tailor marketing strategies, optimize product offerings, and enhance the overall shopping experience for each segment. 

For instance, high-spending customers might receive personalized promotions, while occasional shoppers could be targeted with incentives to increase their purchases. Customer segmentation thus serves as a valuable tool for retailers to optimize resource allocation, improve customer satisfaction, and drive overall business growth.




#### Connect Python to Postgresql
* We import data from MongoDB to Python.


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

Below is the JSON data output.

![alt text](https://github.com/KarlRetumban/SampMG_SA_RS/blob/main/images/JSON.PNG)
