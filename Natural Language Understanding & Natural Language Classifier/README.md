# Natural Language Understanding
### [Link to Video](https://youtu.be/fgkJjIi8CaY)


The Natural Language Understanding node can analyze semantic features of text input, including - categories, concepts, emotion, entities, keywords, metadata, relations, semantic roles, and sentiment.

* Categories - categorize content into a taxonomy.
* Concepts - identify high-level concepts that aren't necessarily directly referenced in the text.
* Emotion - analyze emotion conveyed by specific target phrases or by the document as a whole. You can also enable emotion analysis for entities and keywords
* Entities - identify people, companies, organizations, cities, geographic features, and other typed entities.
* Keywords - search your content for relevant keywords. .
* Metadata - identify author name, title, RSS/ATOM feeds, publication date, etc.
* Relations - recognize when two entities are related, and identify the type of relation.
* Semantic Roles - parse out sentences into subject, action, and object form.


### Nodes Needed

* 2 inject node
* 1 natural language understanding node
* 1 debug node

### Instructions

1. Head over to bluemix and search for "natural language understanding" in the catalog. Click on it, leave it unbound, choose the standard plan and create the service. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/NLU%20Service.png "Service")

2. Open your Node-RED application and drag out a natural language understanding node. Double click on it and you will be required to enter an API key. Head back over to bluemix, click on service credentials and view credentials. Copy the API key into the natural language understanding node in Node-RED.

3. Configure the natural language understanding node as such 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/NLU%20Config.png "Config")

4. Double click the first inject node, change the payload to string and enter the text located here: [link](https://raw.github.ibm.com/L-Gamerman/NodeRedEducation/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/Ginni%20Speech.txt?token=AAGE98hmiU0p6rCeStii6EfXw67W7fMQks5Zf5eWwA%3D%3D)

5. Change the output of the debug node from msg.payload to msg.features

6. Deploy and your output should be similar to this:
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Result1.png "R1") ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Result2.png "R2") ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Result3.png "R3")

7. Double click the second inject node, change the payload to string and enter the url of any website you want to analyze. Configure the natural language understanding as you wish and deploy.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/URL%20Output.png "URL Output")



# Natural Language Classifier
### [Link to video](https://youtu.be/UsTVfGhW62g)

The Natural Language Classifier node uses machine learning algorithms to return the top matching predefined classes for short text input. You create and train a classifier to connect predefined classes to example texts so that the service can apply those classes to new inputs. 


### Nodes Needed

* 6 inject node
* 4 natural language classifier nodes
* 4 debug node
* 1 dropbox node

### Instructions

1. Head over to bluemix and search for "natural language classifier" in the catalog. Click on it, leave it unbound, choose the standard plan and create the service. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Service.png "Service")

2. Open your Node Red application and drag out a natural language classifier node. Double click on it and you will be required to enter a username and password. Head back over to bluemix, click on service credentials and view credentials. Copy the username and password into the natural language classifier node in Node Red.

3. Next, we need to feed the service some training data. To do this, we will input a [csv](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/weather_data_train.csv) file from dropbox. To setup box in node red, refer to this [link](https://github.com/watson-developer-cloud/node-red-labs/tree/master/utilities/dropbox_setup).

**Note:** You can also you Box as your file sharing input

4. Once you have either dropbox or box setup, download the respective nodes in node red. Click on the menu button, manage palette, install and search for either box or dropbox. Install the one you will be using. For the purposes of this tutorial, I will be using dropbox as its free. Although the steps for box are very similar.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Dropbox%20Install.png "DB Install")

5. Once dropbox has finish, drag out the dropbox node with connectors on both sides. It should look like this. To configure this node, double click on it, and click the pen button next to dropdown menu. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Dropbox%20Node.png "DB Node")

6. Enter your app key, app secret and access token which you obtained from step 3.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Dropbox%20Config.png "DB Config")

7. Aftering entering the credentials,, click done and enter the file name. The file should be "weather_data_train.csv".
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Dropbox%20Filename.png "Filename")

8. Drag out an inject and debug node and wire them together with the natural language classfier and dropbox nodes. Set the mode of your natural language classifier node to train. Your flow should look like this. Deploy and click on the button next to the inject node.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Training%20Flow.png "Train Flow")

9. You should have a message similar to this in your debug tab. This means that the natural language classifer service is being trained. This takes sometime depending on the file size.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Training%20Output.png "Output") 

10.  To check the progress, open up the natural language classifer service you created on bluemix and click on "access the beta toolkit"
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Beta%20Kit.png "Beta Kit") ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Training%20Status.png "Training Status")

11. Once your data has finished train, drag out five inject nodes, three classifier nodes and three debug nodes. Wire them like so
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Testing%20Flow.png "Testing Flow")

12. Change the mode of the first classifier node to list and the second to classify. Leave the payload of the first inject node as a timestamp. Change the second inject node's payload to a string and enter "Is it hot outside?". Repeat the same for the third and fourth inject nodes but enter "What is the expected high for today?" and "Will there be a storm today?" respectively.

13. Clicking the button next to the first inject node will list all the classifiers you have created with the natural language classifier service.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/List%20Output.png "List Output")

14. Clicking the button next to the second to fourth inject nodes will tell you where the question you asked was about temperature or conditions.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Classify%20Output.png "Classify Output")

15. To remove a classifier, input the classifier id in the payload of the inject, change the mode of the classifier node to remove and deploy.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier/images/Remove%20Config.png "Remove Config")

### Click [here](https://github.ibm.com/L-Gamerman/NodeRedEducation/tree/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech) to go to the next topic
