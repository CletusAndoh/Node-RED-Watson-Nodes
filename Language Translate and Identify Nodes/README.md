# Language Translator

### [Link to Video](https://youtu.be/c3Qov2B486o)

### Nodes Needed
* 1 inject node
* 1 language translator node
* 1 debug

The Language Translator node lets you translate text from one language to another.

To get started you need to create a language translator service in bluemix and connect it to Node-RED. The easiest way to do 
this is to connect the service to your Node-RED application when you create the service. This way you wont need to enter 
credentials when you go to use the node. 

1. Head over to Bluemix, click the catalog and search for "language translator"
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Language%20Translate%20and%20Identify%20Nodes/images/Catalog%20Search.png "Catalog Search")
2. Connect the service to your exisiting Node-RED application and restage the app when it promotes you to do so.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Language%20Translate%20and%20Identify%20Nodes/images/Connect%20to%20NR.png "Connect")
3. Head back into Node-RED. Drag out the an inject, language translator and debug node and wire them together.
Flow pic goes here
4. Double click the inject node, change the payload to string and enter "Hello, this is a test"
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Language%20Translate%20and%20Identify%20Nodes/images/Hello%20test.png "Hello")
5. Double click the language translator node and setup it up as such
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Language%20Translate%20and%20Identify%20Nodes/images/Language%20Translator%20Node%20HT.png "Config")
6. Head over to the debug tab and this should be your result
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Language%20Translate%20and%20Identify%20Nodes/images/Result%20for%20Hello%20Test.png "Hello Result")

As you may have noticed, there are multiple domains that support different languages

* The News domain - targeted at news articles and transcripts, it translates English to and from French, Spanish, Portuguese or Arabic.
* The Conversational domain - targeted at conversational colloquialisms, it translates English to and from French, Spanish, Portuguese or Arabic.
* The Patent domain - targeted at technical and legal terminology, it translates Spanish, Portuguese, Chinese, or Korean to English.

**Note:** Watch the video above for more examples

# Language Identify
### [Link to Video](https://youtu.be/e9XPryCWta0)

### Nodes Needed
* 1 inject node
* 1 language identify node
* 1 debug

The Language Identifier node lets you identify the language text is written in. It uses the language translator service about so if you completed the steps above, no set up is required.

# Instructions
1. Drag out the an inject, language identify and debug node and wire them together.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Language%20Translate%20and%20Identify%20Nodes/images/Flow.png "Flow")
2. Double click the inject node, change the payload to string and enter the following string: "The boy had a red water bottle"
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Language%20Translate%20and%20Identify%20Nodes/images/Inject.png "Inject")
3. Double click the debug node and change the payload from msg.payload to msg.lang. This will return the language with the highest confidence score
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Language%20Translate%20and%20Identify%20Nodes/images/Debug.png "Debug")
4. Head over to the debug tab and this should be your result.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Language%20Translate%20and%20Identify%20Nodes/images/Output.png "Output")

**Note:** Play around with the inject node and try entering text in various languages. Watch the video above for more examples

### Click [here](https://github.ibm.com/L-Gamerman/NodeRedEducation/tree/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Natural%20Language%20Understanding%20%26%20Natural%20Language%20Classifier) to go to the next topic


