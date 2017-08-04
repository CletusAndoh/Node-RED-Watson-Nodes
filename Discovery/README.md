# Discovery

### [Link to video](https://youtu.be/fxmO20uiL3k)

The Discovery node uses the IBM Watson discovery service to rapidly add a cognitive, search, and content analytics engine to applications to identify patterns, trends, and insights from unstructured data to drive better decision making. It cleans and normalizes the data. That normalized data is then indexed into a collection as part of an environment in the cloud. By doing this, it can understand data faster, create betetr hypothesis and deliver better outcomes. In summary, the node uses data analysis combined with cognitive intuition to take your unstructured data and enrich it so you can discover the information you need.

Check out the [demo](https://discovery-news-demo.mybluemix.net/) to get an idea of how it works

**NOTE:** Most of the instructions below can be accomplished through the web interface of the discovery service. I recommend using that as it is easier to understand follow

### Nodes Needed


### Instructions

1. Search for the discovery service in bluemix. Leave it unbound, choose the free plan and create the service. 
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/Service.png "Service")

2. Open your Node-RED application and drag out a discovery node. Double click on it and you will be required to enter a username and password. Head back over to bluemix, click on service credentials and view credentials. Copy the username and password into the discovery node in Node-RED.

3. There are ten methods in this node so lets go over the important ones.
* Create New Environment - this method creates a new environment for the instance of your discovery service. Requires an environment name, description and environment Size as input. 

* List Existing Environments - this method list all environment created for the instance of the discovery service. 

* Create New Collection - this method creates a new data collection in the specified environment. Requires an environment ID, collection name and configuration id as input. 

* Search in Collection - searches a data collection and can return entities, keywords, sentiment, etc

**Note:** Check out the info tab of the discovery node for details on all of the methods. They all essentially create, list and  retrieve details about environments, collections and configurations

4. Launch the service from bluemix. There should already be a Watson Discovery News data collection. The Watson Discovery News is a dataset of primarily English language news sources that is updated continuously, with approximately 300,000 new articles and blogs added daily.
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/Launch%20Tool.png "Launch Tool")
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/Watson%20Discovery%20News.png "Watson Discovery")

5. On the left hand side, under API information, you will see three very important things. The collection id, configuration id and environment id. You can also get these details through Node-RED by creating flows such as these:

**Environment ID**
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/List%20Env%20Flow.png "List Env Flow")
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/List%20Env%20Flow%20Result.png "Output")

**Collection ID - Requires an environment ID in the list collections node**
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/List%20Coll%20Flow.png "List Coll Flow")
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/List%20Coll%20Flow%20Result.png "Output")

**Configuration ID - Requires an environment ID and collection name in the list configurations node**
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/List%20Config%20Flow.png "List Config Flow")
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/List%20Config%20Flow%20Result.png "Output")


6. Now lets build a query with the discovery query builder node for the discovery node to use. Drag out a discovery query builder node and use the same credentials as you did for the discovery node. Build a flow that looks like this:
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/Query%20Flow.png "Query Flow")

7. We want to search through the Watson Discovery News data collection to three find documents that talk about IBM, have a positive sentitiment about IBM and an overall positive document sentiment. To do this, configure your discovery query builder node as such:
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/Query%20Builder%20Config.png "Query Builder")

And your configure discovery node like so:
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/Discovery%20Node%20Config.png "Discovery Node Config")

In the list of sections to return text field enter "text,entities.text,docSentiment.type,entities.sentiment.type"

8. After deploying your result should be similar to this. Expand the results objects until it shows the entity "IBM",the entity and document sentiment and the text.
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/Query%20Flow%20Result.png "Output")
![alt text](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery/images/Query%20Flow%20Result%20Expanded.png "Output Expanded")

### Click [here](https://github.ibm.com/L-Gamerman/NodeRedEducation/tree/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Language%20Translate%20and%20Identify%20Nodes) to go to the next topic



