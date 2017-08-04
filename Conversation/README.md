# Watson Conversation
### [Link to video](https://youtu.be/UWbsEDmA9iw)

The Watson Conversation node uses the Watson conversation service to create virtual cognitive agents  that combine machine learning, natural language understanding, and integrated dialog scripting tools to provide outstanding customer engagements.

### Nodes Needed

* 2 http in nodes
* 2 http response nodes
* 2 function node
* 1 conversation node
* 1 template node

### Instructions

1. Head over to bluemix and search for "conversation" in the catalog. Click on it, leave it unbound, choose the free plan and create the service. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/Service.png "Service")

2. We need to create our conversation. We need to create a workspace, define some intents and entites and create a dialog. Launch the conversation tool.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/Launch%20Tool.png "Launch")

3. For the purposes of this tutorial, we are going to use the sample workspace that comes preloaded with the conversation service. Click on the car dashboard sample workspace. The service will populate the workspace with intents, entities and dialog. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/Workspace%20Homepage.png "Car Dash")

4. In Node-RED, drag out a http in node, a template node and a http response node. Wire them up. This first flow will serve as the homepage for you to interact with the conversation service. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/Template%20Flow.png "Template Flow")
5. Configure the http in node like so. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/First%20HTTP%20In.png "First HTTP In")

6. In the template node copy and paste in the code below
```
<html>
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>
	  My BOT
	</title>
	<link rel="stylesheet"
        type="text/css"
        href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" />
  </head>
  <body>

    <div class="container">
      <div id="no-script"class="bg-info">
        This application needs JavaScript enabled in your browser!
      </div>
      <div id="id_contextdump"></div>

      <h1>My BOT</h1>
      <div id=id_botchathistory>
	  </div>
	  
	  <div>
	      <form>
            <label for="id_chattext">Your Input: </label>
            <input type="text" name="chattext" id="id_chattext">
            <br/><br/>
	      </form>
	      <button onclick="javascript:onChatClick()">Send</button>
	  </div>
    </div>
    <script type="text/javascript" src="https://code.jquery.com/jquery-2.1.4.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>

    <script type="text/javascript">
    
      $(document).ready(function() {
          javascriptCheck();
          	$('#id_contextdump').hide();
      });

      // if javascript is enabled on the browser then can
      // remove the warning message
      function javascriptCheck() {
        $('#no-script').remove();
      }
      
      function createNewDiv(who, message) {
        console.log('002-001');  
        var txt = who + ' : ' + message;
        return $('<div></div>').text(txt);
      }

      function chat(person, txt) {
        $('#id_botchathistory').append(createNewDiv(person, txt));
      }    
      
      function processOK(response) {
        console.log('003-001');
        console.log(response);
        console.log(response.botresponse.messageout);
        console.log(response.botresponse.messageout.output.text);
        console.log(response.botresponse.messageout.context);
        chat('Bot', response.botresponse.messageout.output.text); 
        $('#id_contextdump').data('convContext', response.botresponse.messageout.context);
      }
      
      function processNotOK() {
        chat('Error', 'Error whilst attempting to talk to Bot');
      }
      
      function invokeAjax(message) {
        var contextdata = $('#id_contextdump').data('convContext');
        console.log('checking stashed context data');
        console.log(contextdata);
        
  
        //var ajaxData = "msgdata=" + message;
        var ajaxData = {};
        ajaxData.msgdata = message;
        if (contextdata) {
          ajaxData.context = contextdata;    
        }

        $.ajax({
          type: 'POST',
          url: 'botchat',
          data: ajaxData,
          success: processOK,
          error: processNotOK
        });
      }
          
      // User has entered some text.
      function onChatClick() {
        console.log('001-001');
        var txt = $('#id_chattext').val();
        chat('You', txt); 
        invokeAjax(txt);
        console.log('001-002');
      }
      
        
    </script>
  </body>
</html>
```

7. Next, drag out another http in node, two function nodes, a conversation node and a http response node. Wire them up.
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/Conversation%20Flow.png "Conversation Flow")

8. Configure the http in node like so
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/Second%20HTTP%20In.png "Second HTTP In")

9. Configure the first function node with the code below. All this node does is, it pulls out the text you input into the service and any conversation context information
```javascript
// stash away incoming data
msg.mydata = {};
msg.mydata.messagein = msg.req.body.msgdata;
msg.payload = msg.mydata.messagein;

msg.params = { "context": msg.req.body.context};

return msg;
```
10. In the conversation node, we need to enter a workspace ID. To get this ID, head back to your conversation service page. On the left hand side, click on the last icon to go back to your workspaces. Click the three ellipses on the car dashboard workspace and view details. Copy and paste the workspace ID it provides into your Node-RED conversation node. 
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/Workspace%20ID.png "Workspace ID") ![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/Workspace%20ID%202.png "Workspace ID")
**Note:** If the conversation node requires you to put in a username and password along with a workspace ID, you have to use the username and password specific to the car dashboard workspace. To get those credentials, go back to your car dashboard workspace home page and click on the deploy button
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/Service%20Credentials%20Button.png "Deploy Button")

Then click on the service credentials tab and copy and paste the credentials it provides in your conversation node in Node-RED
![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/Service%20Credentials.png "Serv Cred")

11. Configure the second function node with the code below. All this node does is, it builds a response, incorporating the conversation context and bot response.
```javascript
msg.mydata.messageout = msg.payload;

msg.payload = {};
msg.payload.botresponse = msg.mydata;

return msg;
```
12. Now we can test the flow. Deploy the flow. Copy your Node-RED URL and replace everything after "net/" with "bot". It should look something like this: http://xxxx.mybluemix.net/bot

13. If you want to know what kind of questions you can ask the bot, you can look back at the intents on your workspace homepage. **Very Important: DO NOT PRESS THE ENTER BUTTON WHEN YOU WANT TO SEND YOUR MESSAGE TO THE BOT. USE THE SEND BUTTON LOCATED UNDER THE TEXT FIELD**

![picture alt](https://github.ibm.com/L-Gamerman/NodeRedEducation/blob/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversation/images/Bot%20Output.png "Output")

14. Free feel to add more functionalities to the workspace by adding more intents, entities and dialog options


### Click [here](https://github.ibm.com/L-Gamerman/NodeRedEducation/tree/master/Chapter%205%20-%20Watson%20%26%20Cognitive%20API%20Nodes/Conversion) to go to the next topic

**Note:** [Source](https://github.com/watson-developer-cloud/node-red-labs/tree/master/basic_examples/conversation) when creating this tutorial


