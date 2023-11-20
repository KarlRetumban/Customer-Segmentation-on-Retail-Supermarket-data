# Customer Segmentation on Grocery Purhcase data
#### We apply the following techniques in Grocery Purhcase data.
* Customer Segmemtation
* Cluster Profiling
* Classify the segment of new data

### Description of the Use Case
We analyze the Renttherunway Clothing Fit data. The dataset contains information about rented attires for certain occassions. It also includes the ratings given by the renters. The user feedback or user review is also included in the data as well as information about the user and the attire.

We conduct exploratory data analysis providing descriptive statistics and data visualizatiuon so we can have a good idea of the data and identify patterns and relationships among the variables.

We will apply Sentiment Analysis to the clothing fit review data and determine the customer sentiments regarding the rented attire. We can also determine the level of satisfaction of customers, whether it is positive, negative or neutral out of their feedback reviews. We will also determine the consistensy of sentiments with respect to the ratuings given and check if the two customer feedback align.

We then build a Recommender System that will suggest the next most likely items or attire category the customer will avail in the future using the users historical preference.



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
