---
#icon: material/folder-open-outline
icon: material/medal
---

### Mission Details

Your mission is to review preconfigured Scripted AI Agent for tracking existing order. If you would like to build it by yourself there are BONUS Missions 3,4,5 and 6 of this lab. 

### Build

#### Task 1. Review the Configurations in AI Studio to track an order. 

1. Go to AI Studio and open AI Agent with name ***<copy>180_Scripted_AI_Agent</copy>***. 
**Please do not making any changes to this agent, as this lab is for review purposes only for the entire group.**

    ![Profiles](../graphics/Lab1_AI_Agent/6.69.png) 


2. Below is the diagram for tracking order flow. If the caller asking to track an order, **track_order** intent should be used as it has utterances like **Can you track my order** and others. This intent is configured to collect required **Entity**, for this the interaction will be moved to the interim response with name **order_number**.  
    ![Profiles](../graphics/Lab1_AI_Agent/6.68.png) 

3. Open up ***<copy>180_Scripted_AI_Agent</copy>***
 AI agent. Click on **Script > Intents** and then open up **track_order** intent. 
     ![Profiles](../graphics/Lab1_AI_Agent/6.70.png) 

4. If this intent is triggered (customer request matches the Utterances), then system will initiate the response **order number** until the required entity is filled or the number of retries is exceeded.
     ![Profiles](../graphics/Lab1_AI_Agent/6.71.png) 

5. Once the entity is filled, the system initiates the final response for this intent. In this case, it is **track_order**.
     ![Profiles](../graphics/Lab1_AI_Agent/6.72.png) 

6. Click on Entities and review **order_number** Entity configuration. 
     ![Profiles](../graphics/Lab1_AI_Agent/6.73.gif) 

7. Click on **Responses** and seach for **order_number** response and review it for response message  
     ![Profiles](../graphics/Lab1_AI_Agent/scriptedOrdernumber6.91.gif) 

#### Task 2. Send the data from AI Agent to Voice Flow​.

1. Click on **Responses** and open up response with name **track_order**
     ![Profiles](../graphics/Lab1_AI_Agent/6.74.png) 

2. Review the response configuration after clicking the **Voice** channel
     ![Profiles](../graphics/Lab1_AI_Agent/6.75.png) 

3. Go to [Control Hub](https://admin.webex.com){:target="_blank"} > Contact Center. Click on **Flows** and open the flow with name ***Autonomous_Scripted_Flow_2000_180***<span class="copy-static" title="Click to copy!" data-copy-text="Autonomous_Scripted_Flow_2000_180"><span class="copy"></span></span>.
     ![Profiles](../graphics/Lab1_AI_Agent/6.76.gif) 

4. Click on the lower VirtualAgentV2 block. You will see the Activity Output Variables. The Entity value can be found in VirtualAgentV2.MetaData. 
     ![Profiles](../graphics/Lab1_AI_Agent/6.77.png) 

5. Click on the next **SetVariable** block and you can see that we just assigned the value from Activity Output Variable from the previous **VirtualAgentV2** block to the flow variable with name **MetaData_Scripted_Agent**. This is an optional step. 
     ![Profiles](../graphics/Lab1_AI_Agent/6.78.png) 

6. Click on **Parse** block. It is configured to parse data from **MetaData_Scripted_Agent** variable using JSON path **$.ordernumber** and assign the respon to the flow variable with name **order_id**.
     ![Profiles](../graphics/Lab1_AI_Agent/6.79.png) 

7. Open up **HTTP Request** block. It is configured to send **GET** request with the parameter as the order_id value to retrive the response specifically for this order. 
     ![Profiles](../graphics/Lab1_AI_Agent/6.80.png) 

8. If we would do the same request from Postman for the order Id 17, here is the information we would get. 
     ![Profiles](../graphics/Lab1_AI_Agent/6.81.png) 

9. While on **HTTP Request** node, scroll down and you will see the configurations to parse the data from the response. It is configured to use JSON path **$.[0].status** and assign the response to the variable with name **order_status**.
     ![Profiles](../graphics/Lab1_AI_Agent/6.82.png) 

10. For example if I would need to parse the status of the order 17 using this JSON path, the result would be "new".
     ![Profiles](../graphics/Lab1_AI_Agent/6.83.png) 

#### Task 3. Send the data from Voice Flow to AI Agent. 

1. To send data back to AI Studio we need to use one more VirtualAgentV2 block. Click on it to review configurations. You can see that we use the same Scripted AI agent **180_Scripted_AI_Agent**, but we also configured the **State Event**. The **Event Name** will refer to the response on AI Studio. And the **Event Data** contains the result of the **order_status** that can be retrieved in the AI Studio.
     ![Profiles](../graphics/Lab1_AI_Agent/6.84.png) 

2. Go to AI Studio and open AI Agent with name ***180_Scripted_AI_Agent***<span class="copy-static" title="Click to copy!" data-copy-text="180_Scripted_AI_Agent"><span class="copy"></span></span>. **Please do not make any changes to this agent, as this lab is for review purposes only for the entire group.**
    ![Profiles](../graphics/Lab1_AI_Agent/6.69.png) 

3. Open the response with the name **order_status**. The same name was specified in the VirtualAgentV2 block as the **Event Name**. 
     ![Profiles](../graphics/Lab1_AI_Agent/6.85.png) 

4. Open up the response and you can see that data will be returned using the following format: **${eventStore.status}**.
     ![Profiles](../graphics/Lab1_AI_Agent/6.86.png) 

#### Task 4. Place test call and review the trace. 

1. Call the number +15206603129 that is configured to deliver the call to the flow **Autonomous_Scripted_Flow_2000_180**.
     ![Profiles](../graphics/Lab1_AI_Agent/6.87.png) 

2. Press 2 to go to the Scripted AI agent. Ask to track your order. Provide the order number as 17 or any other order that you created earlier. You should hear the response that the order status is "new".

3. Open up Debug mode in the flow **Autonomous_Scripted_Flow_2000_180**.
     ![Profiles](../graphics/Lab1_AI_Agent/6.88.gif)

4. Review the trace. 
     ![Profiles](../graphics/Lab1_AI_Agent/6.89.png) 

5. In the AI Agent Studio, go to Sessions and review the traces. 
     ![Profiles](../graphics/Lab1_AI_Agent/6.90.png) 

<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>