---
#icon: material/folder-open-outline
icon: material/medal
---

# Mission 3: Configure Fulfillment Action and create an order using **Voice Flow**. 

**<details><summary>What is fulfilment Action? <span style="color: orange;"></span></summary>**

Fulfillment Action is a task that an AI agent performs by understanding user intents and completes by connecting to external systems over API. 


## </details>

## Mission overview


In this Mission you will be using the Voice flow to execute the API call to create teh order in order to complete the AI Agent Fulfillment. 

![Profiles](../graphics/Lab1_AI_Agent/Fulfilment.png)

---

## Build


### Task 1. Configure Action in the AI Studio

1. Go to **Webex AI Agent AI** Studio Portal.
   ![Profiles](../graphics/Lab1_AI_Agent/2.14.gif)

2. Select your AI agent with name **<copy><w class="attendee"></w>\_2000_AutoAI_Lab</copy>** that you created earlier and go to **Actions**. You will see one Action is already created by default for the Agent Handover. We will now create few more actions.
   ![Profiles](../graphics/Lab1_AI_Agent/2.17.gif)

3. Click on create <b>New Action</b>. From the drop-down option, select **Fulfillment**.
   ![Profiles](../graphics/Lab1_AI_Agent/2.18.png)

4. Configure it with name **_<copy>Create_New_Order</copy>_** and the Action description **_<copy>Collect order details, delivery address, total and response with the id number once the order is completed. The request will contain the order details. From the order details let the customer know the order ID.</copy>_**. In the Action score select <b>Slot filling and fulfillment</b>.
   ![Profiles](../graphics/Lab1_AI_Agent/2.18a.gif)

5. Scroll down and click to create **New input entity**. Fill up the table with the following and then click on **Add**. <br>
   > Entity Name: **_<copy>address</copy>_** <br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Collect the customer's delivery address</copy>_**<br>
   > Example: **_<copy>548 Catalina Drive, Cary, NC 27515</copy>_** <br>
   > Required: <b>Yes</b>
   ![Profiles](../graphics/Lab1_AI_Agent/2.19.gif)

6. By following the same pattern, create an entity that specifies whether the customer requires delivery. <br>
   > Entity Name: **_<copy>delivery</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Check if the customer needs delivery or not. Event if they want to proceed with order without specifying the delivery details. If the customer wants to confirm the order but didn't specify if they need delivery or not, ask one more time if they need the delivery or not.</copy>_**<br>
   > Example: **_<copy>Yes</copy>_**<br>
   > Example: **_<copy>No</copy>_**<br>
   > Required: <b>Yes</b>

7. By following the same pattern, create an entity to collect the customer's phone number.<br>
   > Entity Name: **_<copy>phoneNumber</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Collect customer's phone number. Before the customer complete the order, ask if they would like to receive confirmation over the SMS. If so, collect the phone number.</copy>_**<br>
   > Example: **_<copy>3477579861</copy>_**<br>
   > Required: <b>Yes</b>

8. By following the same pattern, create an entity to collect the customer's order details.<br>
   > Entity Name: **_<copy>orderDetails</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Collect the flowers and bouquets information that customer orders. Make sure to do correct math. If one rose is 20 dollars and the customer would like buy 9 roses then the price should be 180 dollars. Don't use double quotes (") in the generated responses.</copy>_**<br>
   > Example: **_<copy>Romantic Roses standard bouquet and one more bouquet with 9 roses</copy>_**<br>
   > Required: <b>Yes</b>

9. By following the same pattern, create an entity to store the total price information of the order.<br>
   > Entity Name: **_<copy>orderTotal</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>After the customer inform if they need delivery or not, and confirm that they would like to proceed with completing the order, collect the Total information and assigned it to this slot. Always use the number for the total. For example use 500 $ but not five hundred dollars.</copy>_**<br>
   > Example: **_<copy>150 dollars, 70 dollars</copy>_**<br>
   > Required: <b>Yes</b>

10. By following the same pattern, create an entity to store the order status information.<br>
   > Entity Name: **_<copy>status</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Always create it as "new"</copy>_**<br>
   > Example: **_<copy>new</copy>_**<br>
   > Required: <b>Yes</b>

11. At this point you should see 6 created entities. Please double check that your configuration matches the screenshot below.
    ![Profiles](../graphics/Lab1_AI_Agent/2.61.png)


12. Scroll down and for the **Fulfillment** option select **Manage in the source flow (voice only). Click **Save**
   ![Profiles](../graphics/Lab1_AI_Agent/19.2.png)

13. **Publish** your AI Agent. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.33.gif)

### Task 3. Configure fulfillment logic in the Voice flow. 

1. In **Control Hub** got to Flows and open you flow with name **<copy>AutonomousAI_Flow_2000_<w class="attendee"></w></copy>**. Click on **Edit**.
   ![Profiles](../graphics/Lab1_AI_Agent/19.3.gif)

2. Remove **DisconnectContact** node. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.4.gif)

3. Create flow string variable with name **<copy>event_name</copy>** and empty default value.
   ![Profiles](../graphics/Lab1_AI_Agent/19.5.gif) 

4. Create flow string variable with name **<copy>order_request_details</copy>** and empty default value.
   ![Profiles](../graphics/Lab1_AI_Agent/19.6.gif) 

5. Add **SetVariable** node from the left side of flow designer to the field. Connect **VirtualAgentV2** node to the **SetVariable** node. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.7.gif) 

6. Click on the **SetVariable** that you just created and configure your **event_name** variable to be assigned with **VirtualAgentV2....StateEventName** variable. </br>
   **Note:** *This event name will be the same as your Action name from the AI Agent Studio that is used for the fulfillment.*
   ![Profiles](../graphics/Lab1_AI_Agent/19.8.gif)

7. Add one more **SetVariable** node and connect them in series.
   ![Profiles](../graphics/Lab1_AI_Agent/19.9.gif) 

8. We will need to assign the metadata from AI agent to the **order_request_details** string variable. To do so click on **VirtualAgentV2** node, on the right side scroll down until you will see Activity output variable. Copy the name of the variable related to MetaData. Go to your second SetVariable node and configure **order_request_details** with value of the Metadata that you copy inside of the {{}}. See the gif below. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.10.gif) 

9. Add **Case** node and connect **SetVariable** node to the **Case** node.  
   ![Profiles](../graphics/Lab1_AI_Agent/19.11.gif) 

10. Add **Disconnect Contact** and assign the **Default** output on **Case** node to the **Disconnect Contact**
   ![Profiles](../graphics/Lab1_AI_Agent/19.12.gif) 

11. Click on **Case** node. Select **event_name** as the Case Variable. Remove the second Link Description. Keep only one Link Description, as for now you have only one action for fulfillment. In the Link Description provide the name of your action: **<copy>Create_New_Order</copy>**.
   **Note:** *If you add more actions later, the Case node is used as the distribution logic for different fulfillment requests.*
   ![Profiles](../graphics/Lab1_AI_Agent/19.13.gif)

12. Add **HTTP Request** node and connect the **Case** output link to the **HTTP Request** node.
   ![Profiles](../graphics/Lab1_AI_Agent/19.14.gif)

13. Configure the **HTTP Request** with the following:

    - Use authenticated endpoint: **Off**
    - Request URL: **<copy>https://67e9aa0bbdcaa2b7f5b9ed62.mockapi.io/customerOrder</copy>**
    - Method: **POST**
    - Content type: **Application/JSON**
    - Request body: **<copy>{{order_request_details}}</copy>**
       ![Profiles](../graphics/Lab1_AI_Agent/19.15.gif)

14. Connect **HTTP Request** node to **VirtuaAgentV2** node.
   ![Profiles](../graphics/Lab1_AI_Agent/19.16.gif)

15. Click on **VirtualAgentV2** node, open **State Event** and configure the **Event Name** as **<copy>{{event_name}}</copy>**. In this case when the interaction returns to the AI agent it stays in the same session and AI agent continue the conversation accordingly. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.17.gif)

16. Next you need to bring the API call results back to your AI agent. For this, click on the **HTTP Request** node, scroll down on the right side and copy the name of the HTTPRequest...ResponseBody. Then go do **VirtualAgentV2** node, open the **State Events** insert the Http body response to the **Event Data** inside of the {{}}. See the steps on the gif below. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.17_.gif)


17. Enable decryption in the flow so you can monitor your further test calls details. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.19.gif)


18. **Validate** and **Publish** the flow with the **Latest** tag. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.18.gif)

18. Place test call to your test number. Ask to order flowers, provide the requested information. You should hear that the order was completed successfully. Trace the call in the voice flow to make sure HTTP request was successful. Click on HTTP Request node, decrypt the results to make sure you got 201 status result. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.20.gif)

### Task 4. Report the order details to Analyzer.

1. Add Global Variable with name <copy>**Flower_order_details**</copy> to the flow. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.21.gif)

2. Add **SetVariable** node and connect it between **HTTP Request** node and **VirtualAgentV2** nodes. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.22.gif)

3. Click on **Http Request** node. On the right side scroll down to the Activity output variables, and copy the name that is related to Response Body. Then go to the **SetVariable** block and configure it with Variable **Flower_order_details** and the value that you copied from HTTP Request node inside of the {{}}. See the gif below. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.23.gif)

4. Validate and publish the flow. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.24.gif)

5. Place one more test call and order flowers. 

6. Open the prebuilt [Analyzer Report](https://analyzer-v2.wxcc-us1.cisco.com/analyzer/view/visualization?tId=e56f00d4-98d8-4b62-a165-d05a41243d98&rId=303296){:target="_blank"}. You might need to enter your admin login credentials. Once logged in, you should see your call in the list. 
   ![Profiles](../graphics/Lab1_AI_Agent/19.25.png)

### Task 5. Configure SMS Confirmation.

1. In the flow add one more **HTTP Request** node and connect it between **SetVariable** node and **VirtualAgentV2** nodes.
   ![Profiles](../graphics/Lab1_AI_Agent/19.26.gif)

2. Configure the **HTTP Request** with the following:
    - Use authenticated endpoint: **Off**
    - Request URL: **<copy>https://hooks.us.webexconnect.io/events/93VKZM1N24</copy>**
    - Method: **POST**
    - Content type: **Application/JSON**
    - Request body: Body output variable from HTTP request node that you use to create order. The same one that you was using for **SetVariable** node to post the data to Analyzer. See the gif below. **Put it inside of {{}}**.
       ![Profiles](../graphics/Lab1_AI_Agent/19.27.gif)


3. Validate and Publish the flow. 
       ![Profiles](../graphics/Lab1_AI_Agent/19.33.gif)

4. Place test call, create order with a number for SMS confirmation and you should receive the SMS. 

       ![Profiles](../graphics/Lab1_AI_Agent/19.33a.png)


### Task 6. (<span style="color: red;"><strong>Read Only</strong></span>). Understand SMS configuration.

We have preconfigured the SMS flow in this lab that can be triggered using Webhook. To understand the configuration:

1. From **Control Hub**, go to **Contact Center** > **Overview** > **Webex Connect**.
       ![Profiles](../graphics/Lab1_AI_Agent/19.28.gif)

2. Open up Service **<copy>180_2000_Service_</copy>** > **Flows**. This is lab proctor Service where Webhook was configured to trigger the SMS. 
       ![Profiles](../graphics/Lab1_AI_Agent/19.29.gif)

3. Open the Flow **SMS_Webhook**. Please don't do any changes as everybody on this lab are using this flow. This Task is read only, no configurations are needed. 
       ![Profiles](../graphics/Lab1_AI_Agent/19.30.gif)

4. Double click on **Configure Webhook** node. You can see the Webhook URL that we configured in our voice flow and the variables that we are expecting in the body request. 
       ![Profiles](../graphics/Lab1_AI_Agent/19.31.png)

5. Double click on **SMS** node. You will see that the number is carried on from **Webhook** as well as other variables in the **Message** section. The **From Number** 12066478712 is the PSTN provisioned number for SMS. 
       ![Profiles](../graphics/Lab1_AI_Agent/19.32.png)

<p style="text-align:center"><strong>Congratulations, you have officially completed the Autonomous AI Agent lab! 🎉🎉 </strong></p>
