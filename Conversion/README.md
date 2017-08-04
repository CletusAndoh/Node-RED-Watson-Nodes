# Document Conversion
### [Link to Video](https://youtu.be/Yj851KqQIfI)

The Document Conversion node converts a single HTML, PDF, or Microsoft Word document. The input document is transformed into normalized HTML, plain text, or a set of JSON-formatted Answer units that can be used with other Watson services, like the Watson Retrieve and Rank Service.


Lets convert a PDF file to normalizaed text.

### Nodes Needed

* 1 inject node
* 1 function node
* 1 conversion node
* 1 debug node

### Instructions

1. Head over to bluemix and search for "document conversion" in the catalog. Click on it, leave it unbound, choose the standard plan and create the service. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversion/images/Service.png "Service")

2. Open your Node-RED application and drag out a convert node. Double click on it and you will be required to enter a username and password. Head back over to bluemix, click on service credentials and view credentials. Copy the username and password into the convert node in Node-RED.

3. Configure the conversion node like this
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversion/images/Conversion%20Config.png "CConfig")

4. Configure the function node with the code below:
```javascript
msg = {
    payload: 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/document-conversion/sample.pdf?cm_mc_uid=92906461259714997912150&cm_mc_sid_50200000=&cm_mc_sid_52640000=',
    "pdf": {
        "heading": {
            "fonts": [
                {"level": 1, "min_size": 24},
                {"level": 2, "min_size": 18, "max_size": 23, "bold": true},
                {"level": 3, "min_size": 14, "max_size": 17, "italic": false},
                {"level": 4, "min_size": 12, "max_size": 13, "name": "Times New Roman"}
            ]
        }
    }
}

return msg;
```
5. The flow should look like this
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversion/images/Flow.png "Flow")

6. Your result should be similar to this. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversion/images/PDF%20Result.png "Result")


To convert an HTML page to plain text, copy and paste the URL of the page in an inject node. Wire the node with a convert and debug node as so. Set the target of the convert node, Either normalized text, normalized HTML or answer units(JSON)

![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversion/images/Inject%20Config.png "IConfig") ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversion/images/HTML%20Result.png "Result") 

### Click [here](https://github.ibm.com/L-Gamerman/NodeRedEducation/tree/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Discovery) to go to the next topic
