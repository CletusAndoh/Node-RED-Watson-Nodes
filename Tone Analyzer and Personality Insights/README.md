# Tone Analyzer
### [Link to Video](https://youtu.be/NBkndOtCEEc)

The tone analyzer node uses linguistic analysis to detect and interpret emotions, social tendencies, and language style cues found in text. For each category, the service returns a score in the range 0 - 1 that indicates the probability that the tone exists in the content.

Emotional Tone  | Social Tone | Language Tone
:-------------: | :-------------: | :------------:
Joy  | Openness | Analytical
Fear  | Conscientiousness  | Confidence
Disgust | Extraversion | Tentative
Sadness | Agreeableness | 
Anger | Emotional Range

To get a more in depth understanding of your tone and/or tone scores check out this [link](https://www.ibm.com/watson/developercloud/doc/tone-analyzer/understand-tone.html)

It can analyze short-form text like tweets and reviews, or longer documents like articles and blog posts. The service can also be used to understand conversations and communications, and then respond to customers appropriately at scale. This can be done through the Customer Engagement Endpoint 


### Nodes Needed
* 1 inject node
* 1 tone analyzer node
* 1 debug node

### Instructions
**Note:** You will need to connect the speech to text service from Bluemix to Node-RED for the node to work.

1. Head over to bluemix and search for "tone analyzer" in the catalog. Click on it, leave it unbound, choose the standard plan and create the service.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/Service.png "Service")
2. Open your Node-RED application and drag out a tone analyzer node. Double click on it and you will be required to enter a username and password. Head back over to bluemix, click on service credentials and view credentials. Copy the username and password into the tone analyzer node in Node-RED.
3. Configure the tone analyzer node as such
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/Tone%20Analyzer%20Config.png "TA Config")

4. Drag out an inject node and a debug node and wire the flows together like this
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/Flow.png "Flow")

5. Click on the black triangle to expand the reviews. In Node-RED double click the inject node, change the payload to a string and enter the first review below: 
<details>
  <summary>Reviews</summary>
    <p>"Absolute garbage. Had the television less than a month and it's stuck in an endless cycle of freezing and rebooting."
 </p>
 <p>"Great price, very light weight, really easy to install, nice picture quality, good sound and I love that there is one remote for everything! Couldn't be more pleased with this purchase." </p>
</details>

![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/Inject%20Config.png "Inject Config")

6. Double click on the debug node and change the payload from msg.payload to msg.response
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/Debug%20Config.png "Debug Config")
7. Your result should look something like this. Tone Analyzer provides you with a wealth of information that can be used to respond to customers appropriately or just to gain insight
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/Initial%20Results.png "Initial Results")

8. Expand both the document tone object and sentences tone array and keep expanding until you see the scores for each of the tones.

![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/Expanded%20Results.png "Expanded Results")

9. If you want to solely focus on one tone category, head back into the tone analyzer node and select the one you want. You can also to choose sentence analysis off by setting it to false.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/Individual%20Config.png "Individual Config")

10. Now do the same steps with the second review from step 5 and compare the two results. They should be very different.

# Personality Insights
### [Link to Video](https://youtu.be/pkXowYsUgeo)

The Personality Insights node uses linguistic analytics to extract personality characteristics based on how a person writes. The service infers personality characteristics based on three models: **The Big 5, Needs, Values **

The **Big 5 Personality Traits** are the same five traits in the social tone category of the tone analyzer node: Agreeableness, Conscientiousness, Extraversion, Emotional range and Openness.

**Needs** describe which aspects of a product will resonate with a person. The model includes twelve characteristic needs: Excitement, Harmony, Curiosity, Ideal, Closeness, Self-expression, Liberty, Love, Practicality, Stability, Challenge, and Structure.

**Values** describe motivating factors that influence a person's decision making. The model includes five values: Self-transcendence / Helping others, Conservation / Tradition, Hedonism / Taking pleasure in life, Self-enhancement / Achieving success, and Open to change / Excitement.

To get further details on each of these models, check out this [link](https://www.ibm.com/watson/developercloud/doc/personality-insights/models.html)

### Nodes Needed
* 1 inject node
* 1 personality insights node
* 1 debug node

### Instructions
**Note:** You will need to connect the speech to text service from Bluemix to Node-RED for the node to work.

1. Head over to bluemix and search for "personality insights" in the catalog. Click on it, leave it unbound, choose the standard plan and create the service.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/PSService.png "Service")
2. Open your Node-RED application and drag out a personality insights node. Double click on it and you will be required to enter a username and password. Head back over to bluemix, click on service credentials and view credentials. Copy the username and password into the personality insights node in Node-RED.
3. Configure the personality insights node as such
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/PS%20Config.png "PS Config")

4. Drag out an inject node and a debug node and wire the flows together like this
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/PS%20Flow.png "Flow")

5. Double click the inject node, change the payload to a string and enter the sample text [here](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%2C%20Personality%20Insights%20%26%20Visual%20Recognition/Ginni%20Speech.txt): 

![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/PS%20Inject%20Config.png "Inject Config")

6. Double click on the debug node and change the payload from msg.payload to msg.insights
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/PS%20Debug%20Config.png "Debug Config")
7. Your result should look something like this. Tone Analyzer provides you with a wealth of information that can be used to respond to customers appropriately or just to gain insight
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Tone%20Analyzer%20and%20Personality%20Insights/images/PS%20Initial%20Result.png "Initial Results")

### Click [here](https://github.ibm.com/L-Gamerman/NodeRedEducation/tree/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Visual%20Recognition) to go to the next topic
