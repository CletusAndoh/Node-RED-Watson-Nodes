# Speech to Text
### [Link to Video](https://youtu.be/f-PQMjRJBvU)

The speech to text node coverts human voice into written text. It can be used anywhere voice-interactivity is needed. The service is great for transcribing media files, call centre transcriptions, voice control of embedded systems, or converting sound to text to then make data searchable. Supported languages include:

US English | US Great Britain | French | Spanish | Japanese | Brazilian Portuguese | Mandarin | Arabic

              
### Nodes Needed
* 1 inject node
* 1 speech to text node
* 1 microphone node
* 1 debug node

### Instructions
**Note:** You will need to connect the speech to text service from Bluemix to Node-RED for the node to work.

1. Head over to bluemix and search for "speech to text" in the catalog. Click on it, leave it unbound, choose the standard plan and create the service.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Catalog%20Search.png "Catalog")
2. Open your Node-RED application and drag out a speech to text node. Double click on it and you will be required to enter a username and password. Head back over to bluemix, click on service credentials and view credentials. Copy the username and password into the speech to text node in Node-RED.
3. Configure the speech to text node as such
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/S2T%20Config.png "S2T Config")
4. Now at this point there are two ways to enter some human speech into Node-RED. 
    1. You can download a microphone node and use your computer microphone to input speech  
    
        Steps:
        1. Head over to the menu button and click on manage palette.
        ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Manage%20Palette.png "Manage Palette")
        2. Click on the install tab and search for "microphone"
        3. Install "node-red-contrib-browser-utils"
        ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Mic%20Package.png "Mic Package")
        4. When its finished installing, you should have a new node that looks like this:
        ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Mic%20Node.png "Mic Node")
        5. First lets test the microphone node. Wire together a microphone, speech to text and debug node. Change the debug's node payload from msg.payload to msg.transcription. Deploy the flow and test it out. Click on the button next to the mic node to start recording. Click the button again when your'e done speaking.
        ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Mic%20Flow.png "Mic Flow") ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Debug%20Config.png "Debug Config")
         
         **Note:** The browser will ask to use your microphone, click share selected device and the microphone node will begin recording
        
 
    
    2. You can put the url of a .wav file into the payload of an inject node and go from there
    
        Steps:
        1. Drag out an inject node, change the payload to string and enter this url "http://sd-2.archive-host.com/membres/up/102033098234604628/SpaceShuttle.wav"
        
        ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Inject%20Config.png "Inject Config")
        
         2. Deploy the flow and click on the button next to the inject node and the audio will be converted to text. Your result should look like this
         
         ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Url%20Output.png "Url Output")



# Text to Speech
### [Link to Video](https://youtu.be/f-PQMjRJBvU) 
**Note:** Skip to 5:30 in the video for the beginning of the text to speech node

The text to speech node converts text to audio speech

### Nodes Needed

* 1 inject node
* 1 text to speech node
* 1 play audio node

### Instructions
1. Head over to bluemix and search for "text to speech in the catalog. Click on it, leave it unbound, choose the standard plan and create the service.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Text%20to%20Speech%20Service.png "Service")
2. Open your Node-RED application and drag out a text to speech node. Double click on it and you will be required to enter a username and password. Head back over to bluemix, click on service credentials and view credentials. Copy the username and password into the text to speech node in Node-RED.
3. Configure the text to speech node as such
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Text%20to%20Speech%20Config.png "T2S Config")
4. This flow uses an play audio node to output the given text. To install that, head over to the menu button and click on manage palette
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Manage%20Palette.png "Manage Palette")
5. Click the install tab and search for audio. Download node-red-contrib-play-audio. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Play%20Audio%20Package.png "Package")

When its finished installing you should have a new node that looks like this
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Play%20Audio%20Node.png "Node")

6. Drag out an inject and play audio node and wire them together with the text to speech node.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Inject%20Config.png "Inject Config")
7. Change the inject node's payload to string and enter "Hello we are learning how to use text to speech in Node-RED"
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Speech%20to%20Text%20-%20Text%20to%20Speech/images/Inject%20Config.png "Inject Config")
8. Deploy and click on the butto next to the inject node to listen to your text.

**Note:** To learn how to save the audio, reference the steps at this [link](https://github.com/watson-developer-cloud/node-red-labs/tree/master/basic_examples/text_to_speech)

### Click [here](https://github.ibm.com/L-Gamerman/NodeRedEducation/tree/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights) to go to the next topic
