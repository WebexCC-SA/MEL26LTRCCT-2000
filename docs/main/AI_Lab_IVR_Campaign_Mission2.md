---
#icon: material/folder-open-outline
icon: material/medal
---

## Mission Details

Your mission is to create a new campaign that will deliver call to your cellphone number. When you answer the call, you will be connected to the Blossom AI Agent for interaction.

### Task 1. Create Flow for the Campaign

1. Login to [Control Hub](https://admin.webex.com){:target="\_blank"}.

2. Go to Contact Center > Flows, click on **Create Flow**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.3.png)

3. Click on **Start Fresh**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.4.png)

4. Name the flow as **<copy>OutDial*Flow_2000*<w class="attendee"></w></copy>** and click **Create Flow**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.5.png)

5. In the Main Flow, add **End Flow** block and connect **New Phone Contact** block to the **End Flow** block.
   ![Profiles](../graphics/Lab1_AI_Agent/8.6.gif)

6. Click on the **Event Flows**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.7.png)
7. Add **GoTo** node and connect it to **Outbound Campaign** node.
   ![Profiles](../graphics/Lab1_AI_Agent/8.8.gif)

8. Click on **GoTo** node and configure it with the Flow that you created in earlier labs for AI agent. It could have the name Flow: **<copy>AutonomousAI*Flow_2000*<w class="attendee"></w></copy>** and click **Create Flow** if you completed all the previous lab. If you just started from this lab, then you need to create another flow with your Virual Agent.

9. **Validate** and **Publish** the Flow.
   ![Profiles](../graphics/Lab1_AI_Agent/8.9.gif)

### Task 2. Create Outdial Channel for the Campaign

1. Click on **Channels** then click on **Create Channel**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.10.png)

2. Name the Channle as **<copy><w class="attendee"></w>\_2000_Channel_Outdial</copy>**. Select **Type** as **Outbound Telephony**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.11.png)

3. Configure **Service Level Threshold** with **300** seconds, select the flow that you have created in the previous Task, add a music on hold and select the Outdial Queue with name **<copy>2000_Campaign_Q</copy>**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.42.png)

### Task 3. Configure new Campaign

1. Login to [Webex Campaign Manager](https://traininglab.wxcc.webexcampaign.us/nextgen){:target="\_blank"} using the Chrome Profile that you created in the previous Mission.
   ![Profiles](../graphics/Lab1_AI_Agent/8.44.png)

2. Click on **Campaign groups** and select **2000_Campaign_Group**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.43.png)

3. Click on **Create campaign**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.13.png)

4. Click on Dialer **Configuration**. Select the Channel (Entry Point) that you have created in the previous Task. Dialer mode select as **Progressive IVR**. Then, click on **Save changes**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.14.png)

5. Click on **Contact list source**, select **Manual file upload**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.45.png)

6. Select preconfigured field mapping with name **2000_Lab**. Select expiration value to **30** days. Then click on **Save changes**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.16.png)

7. Select **Daily schedule**. Configure the start day and active hours during the day. Then **Save changes**
   ![Profiles](../graphics/Lab1_AI_Agent/8.46.png)

8. Click on **Schedule exclusion dates** and just **Save changes**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.18.png)

9. Select **Contact attempt strategy** and click on **Configure**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.19.png)

10. Change the Cycle interval to **1** minute and click on **Save**.
    ![Profiles](../graphics/Lab1_AI_Agent/8.20.png)

11. Once the attempts strategy is configured, click on **Save changes**.
    ![Profiles](../graphics/Lab1_AI_Agent/8.21.png)

12. Click on **Suppression rule sets**. Then select **Suppression rule not required** option. **Save changes**.
    ![Profiles](../graphics/Lab1_AI_Agent/8.22.png)

13. Confirm that you would like to **Continue without suppression rules**.
    ![Profiles](../graphics/Lab1_AI_Agent/8.23.png)

14. Click on **Save & exit** the Campaign configuration.
    ![Profiles](../graphics/Lab1_AI_Agent/8.47.png)

15. Name the Campaign as **<copy><w class="attendee"></w>\_2000_Campaign</copy>**. For **P&L**, from the list, select **TrainingAB_PL_17748776940323**. For **Purpose**, select from the list **Sales**, and click on **Save campaign**.
    ![Profiles](../graphics/Lab1_AI_Agent/8.26.png)

16. You will see your campaign will show up in the **DRAFT** status.
    ![Profiles](../graphics/Lab1_AI_Agent/8.27.png)

### Task 4. Upload Contact List

1. Click on [Customers_List_sample](https://drive.google.com/file/d/1fvHfKhbtPtU6uBmRa7ngEN5bfDHUX7Cz/view?usp=sharing){:target="\_blank"} to download the sample file.

2. On the next page, click on **Download**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.28.png)

3. Open the file and change the number to your 10 digits cellphone number.
   ![Profiles](../graphics/Lab1_AI_Agent/8.29.gif)

4. Go back to Webex Campaign Manger, find your campaign and click on Manage contact lists.
   ![Profiles](../graphics/Lab1_AI_Agent/8.30.png)

5. Click on **Upload file to create contact list**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.31.png)

6. Click on **Browse**, select your file and then click on **Save and Proceed**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.32.png)

7. If you click on **Refresh** you should see the contact list is **Active**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.33.gif)

8. **Close** the **Manage contact list** page.
   ![Profiles](../graphics/Lab1_AI_Agent/8.34.png)

9. Find your Campaign and make it **Active**.
   ![Profiles](../graphics/Lab1_AI_Agent/8.35.png)

10. On the next page, click on **Confirm**.
    ![Profiles](../graphics/Lab1_AI_Agent/8.36.png)

11. Click on **Refresh**, you should see that you campaign is **Running**.
    ![Profiles](../graphics/Lab1_AI_Agent/8.37.gif)

12. Initially, the contact will be in the **Eligible Open** status. Wait until the contact transitions to **Sent to Dialer - Awaiting Outcome**. At that point, you should receive a call. When you answer, please say "Hello" to allow the system to detect a live voice. Once detected, you will begin the conversation with the AI Agent.
    ![Profiles](../graphics/Lab1_AI_Agent/8.39.png)

13. Open up your flow, and you can trace this call.
    ![Profiles](../graphics/Lab1_AI_Agent/8.40.png)

14. If you need to upload the new list, first **Pause** the campaign. (DO NOT Stop the Campaign)
    ![Profiles](../graphics/Lab1_AI_Agent/8.48.png)

15. Upload the new contacts.
    ![Profiles](../graphics/Lab1_AI_Agent/8.49.png)

16. Resume the Campaign.
    ![Profiles](../graphics/Lab1_AI_Agent/8.50.png)

<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>
