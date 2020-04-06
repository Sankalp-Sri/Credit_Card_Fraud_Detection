# Credit_Card_Fraud_Detection
In this particular use case I've used the Self Organizing Map (SOM) technique to filter out the Fraud prone customers.

The given dataset contains the application of the customers applied for the credit card. The dataset has 16 features the features are named Anonymously for the sake of confidentiality apart from the customer ID feature which we will be using to filter out the fraud applicants.
Google drive link for the dataset: https://drive.google.com/open?id=1sDqn2b5e9xUttf4DH5lBcSqKpi-Z9oA8


The Self Organizing Map technique is an unsupervised learning method. Where we map the multi-dimentional input vector to a 2-dimensional map which is containing several layers like in color images we have RGB layers.

To start the process we first need to separate the feature class from the dataset which indicates which application have been approved and which have not.

So with remaining 15 features we first perform feature scaling to bring all the feature values to a specified range as we need to use distance based method in further proceedings and high scale features may introduce bias.

Now we will use the Minisom class to create an object 'som' of this class and using this som object we will first randomly initialize the weights for connecting each input feature to the 10x10 nodes of SOM for each training example.

Now based on these weight we will calculate Mean Inter-Neuron Distance by summing up the square of difference between each input value and weight. And then the node which results in minimum MID will be choosen as Best Matching Unit (BMU).

This process is then repeated for all the training examples and corresponding BMUs found and the mapping is done accordingly.

Now depending upon the training example we have found the corresponding BMU's having MIDs between 0 & 1 and the map is color coded as per the individual training example. 

Also the nearby nodes covered within the defined radius of the minimum MID Node are also alloted the similar color gradually decaying in intensity as we move away from the node.

Thus a Self organised map is obtained, we can visualize the outlier node(white in this case) and that node is basically treated as suspicious applications.

Now we would allot markers to the individual nodes as per their target class in training example & if the wrong marker is attached to any of the SOM node we will extract the entries assigned to that node and store them to retreive fraud applicants.




