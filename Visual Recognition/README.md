# Visual Recognition
### [Link to Video](https://youtu.be/9NoxljNbovM)


The Visual Recognition node uses the Watson Visual Recognition service to identify scenes, objects, faces, and text in images you upload to the service. You can create and train a custom classifier to identify subjects that suit your needs.



### Instructions

1. Head over to bluemix and search for "visual recognition" in the catalog. Click on it, leave it unbound, choose the standard plan and create the service. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition/images/Service.png "Service")

2. Open your Node-RED application and drag out a visual recognition node. Double click on it and you will be required to enter an API key. Head back over to bluemix, click on service credentials and view credentials. Copy the API key into the visual recognition node in Node-RED.

3. Configure the visual recognition node as such 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition/images/VR%20Config.png "Config")

**At this point there are two paths you can take. Trying both ways is recommended. The first is a basic flow using the visual recognition node. The second adds a "face" or a webpage to the service which makes it easier to interact with**

### Basic use of Visual Recognition Node
### Nodes Needed

* 1 inject node
* 1 visual recognition node
* 1 debug node

4. Drag out an inject node and a debug node and wire the flows together like this 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition/images/Basic%20Flow.png "BFlow")

5. Copy and paste the following image URL in the inject node: https://visual-recognition-demo.mybluemix.net/images/samples/3.jpg
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition/images/Inject%20Config.png "Inject")

6. Double click on the debug node and change the payload from msg.payload to msg.result.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition/images/Debug%20Config.png "Debug Config")

7. After you deploy you should a result similar to this. Expand the message in the debug tab to view the result visual recognition provides you.


![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition/images/Result.png "Result")

### Second Way
### Nodes Needed

* 1 http in node
* 1 switch node
* 1 change node
* 2 template nodes
* 1 function node
* 1 visual recognition node
* 1 http response
* 1 debug node

4. Copy this [code](https://raw.github.ibm.com/L-Gamerman/NodeRedEducation/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition/Web%20Page%20Flow.json?token=AAGE93dNW3YPw6m8zRz04gAg6lXTBhHBks5ZizaIwA%3D%3D). In Node-RED, head over to the menu button, select import and then clipboard. Paste the code and select import. Your flow workspace should now look like this. When this flow is deployed and loaded it will display a simple Web page with a text field to input an image's URL, then submit it to Watson Visual Recognition, and output the labels that have been found.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition/images/Import%20Code.png "Import")
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition/images/Webpage%20Flow.png "WP Flow")

Purpose of each node
* HTTP in node configured with a /reco URL to launch webpage
* Switch node which will test for the presence of the imageurl query parameter
* "Get Image URL" template node which is configured to output an HTML input field and suggest a few selected images taken from the main Watson Visual Recognition demo web page
* Change node to extract the imageurl query parameter from the web request and assign it to the payload to be provided as input to the Visual Recognition node
* Visual Recognition node to use the visual recognition service
* "Report" template node connected to a http response node which will format the output returned from the Visual Recognition node into an HTML table for easier reading

### Results

To run the web page, copy the URL of your Node-RED application and add a /reco to the end. It should look something like this: http://xxxx.mybluemix.net/reco. Enter the URL of some image. The URL of the pre-selected images can be copied to clipboard and pasted into the text field.

The Watson Visual Recognition API will return an array with the recognized features, which will be formatted in a HTML 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition/images/Webpage%20Home.png "WP Home")
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition/images/Webpage%20Output.png "WP Output")

**Note:** Source when creating this tutorial [link](https://github.com/watson-developer-cloud/node-red-labs/tree/master/basic_examples/visual_recognition) 


### Click [here](https://github.ibm.com/L-Gamerman/NodeRedEducation/tree/master/Chapter%206%20-%20Databases) to go to the next chapter
