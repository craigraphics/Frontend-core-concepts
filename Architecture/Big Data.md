## Big Data
### Characteristics
  - Volume - refers to the quantity of data that we need to process, store and analyze.
  - In Big Data, we are talking about large quantities of data.
  - Variety - we can have a large variety of unstructured data from multiple sources, for that we have Data Fusion that helps in finding hidden patterns and insights for our organization.
  - Velocity - we have a continuous stream of data that comes to our system at a very high rate.
### Insights
  - Can provide a significant advantage over our competitors
  - Visualization is a powerful tool that allows humans to makes sense of meaningless data.
  - Querying capabilities allows us to run ad-hoc analysis on that data and helps us find those patterns that were not obvious before.
  - Predictive Analysis - we can build algorithms or Machine Learning models to predict behavior of our users and suggest products that they will likely purchase. We can also detect anomalies in the system by analyzing logs from servers.

## Batch Processing
### Advantages
- Easy to implement
- High availability
- Better efficient
- Higher fault tolerance
### Drawback
- Long delay between incoming data and result.
- We don't get a real-time view of the data coming in.
- We can't respond to the platform fast enough.
## Real-Time Processing
### Advantages
 - We can analyze and respond to data as it comes into our system immediately
 - We don't have to wait for a job to process it.
### Drawback
- It's hard to do any complex analysis in real-time.
- We don't get much insight into our system.
- Doing data-fusion is impossible.

## Lambda Architecture
- It attempts to find a balance between High Fault Tolerance and comprehensive analysis of data (Batch Processing)

### Batch Layer
- Manage dataset and be a system of records.
- Precompute batch views
- ### Speed Layer
- Compensates for the high latency in the Batch Layer
- Operates only on the most recent data
- Doesn't attempt to provide a complete view.
### Serving Layer
- Is to respond to ad-hoc queries and merge the data from both the batch layer and the speed layer.
