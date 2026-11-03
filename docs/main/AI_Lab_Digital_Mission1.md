---
#icon: material/folder-open-outline
icon: material/medal
---

## Mission Objective

In this mission, you need to complete web chat configuration tasks, including creating a Chat Asset, linking it to a Channel, and test website.

## Build

### Task 1. Find your Service

1. Login to Webex Connect Portal.
   Go to **Services** and look for the service that you have created earlier. The name should be **<copy><w class="attendee"></w>\_2000_Service</copy>**
   ![Profiles](../graphics/Lab1_AI_Agent/4.1.png)

### Task 2. Configure and Register Chat Asset

1. While on Webex Connect portal, go to **Assets** -> **Apps**, press **Configure New App** and select **Mobile / Web** option.
   ![Profiles](../graphics/Lab1_AI_Agent/4.2.png)

2. Input **_Name_** as **<copy>Chat*App*<w class="attendee"></w>\_2000</copy>**.

3. Toggle/enable **_Live Chat / In-AppMessaging_** to **_ON_** and choose **_Primary Transport Protocol_** as **`MQTT`** & **_Secondary Transport Protocol_** as **`Web Socket`** then tick **_Use Secured Port_** checkbox and press **_Save_** button.
   ![Profiles](../graphics/Lab1_AI_Agent/4.3.png)

   > **Note**: If there is an error that your request cannot be processed, please press **_Save_** button one more time.

4. Once asset is saved, press **_Register To Webex Engage_** at the top.
   ![Profiles](../graphics/Lab1_AI_Agent/4.4.png)

5. Choose **<copy><w class="attendee"></w>\_2000_Service</copy>** from the drop-down list and press **_Register_** button.
   ![Profiles](../graphics/Lab1_AI_Agent/4.5.png)

6. Check and make sure the asset has been succesfully registered to the service and **_Register To Webex Engage_** button has been greyed out.
   ![Profiles](../graphics/Lab1_AI_Agent/4.6.png)

7. Return to **_Assets_** -> **_Apps_**, find **_ChatAsset_**, copy **_App ID_**, paste it into the text file and save. We will use it when configuring chat flow later.
   ![Profiles](../graphics/Lab1_AI_Agent/4.7.png)

### Task 3. Create Entry Point for Chat

1. Login to Control Hub and go to Channels and click on **Create Channel**.
   ![Profiles](../graphics/Lab1_AI_Agent/4.8.png)

2. Input **_Name_** as **<copy><w class="attendee"></w>\_2000_Chat_Channel</copy>**
   ![Profiles](../graphics/Lab1_AI_Agent/4.9.png)

3. Select **Chat** from the **_Channel Type_** drop-down list. Select **<copy>Chat*App*<w class="attendee"></w>\_2000</copy>** as an **_Asset Name_**. Set **_Service Level Threshold_** as **`360`** and click on **Save**.
   ![Profiles](../graphics/Lab1_AI_Agent/4.10.png)

### Task 4. Create Queue for Chat

1.  While on the **Control Hub** portal, go to Queues and click on **Create a queue**.
    ![Profiles](../graphics/Lab1_AI_Agent/4.11.png)

2.  Input **_Name_** as **<copy><w class="attendee"></w>\_2000_Chat_Queue</copy>**. Also select **`Chat`** in the **_Channel Type_** section.
    ![Profiles](../graphics/Lab1_AI_Agent/4.12.png)

3.  Scroll down to **Chat Distribution** click on **_Add Group_** and select **<copy><w class="attendee"></w>\_2000_Team</copy>**
    ![Profiles](../graphics/Lab1_AI_Agent/4.13.gif)

4.  Set **_Service Level Threshold_** as **`7200`** seconds (2 hours). Set **_Maximum Time in Queue_** as **`10800`** seconds (3 hours). Click on **_Save_** after comparing your values with the screenshot below.
    ![Profiles](../graphics/Lab1_AI_Agent/4.14.png)

### Task 5. Website Widget Configuration

1.  Login to Webex Engage Portal from Control Hub.
    ![Profiles](../graphics/Lab1_AI_Agent/4.15.gif)

2.  Go to **_Assets_** -> search and edit **<copy>Chat*App*<w class="attendee"></w>\_2000</copy>** which you have created in Connect Portal.
    ![Profiles](../graphics/Lab1_AI_Agent/4.16.gif)

3.  Scroll down and click on **_Save Changes_** button.
    ![Profiles](../graphics/Lab1_AI_Agent/4.17.gif)

4.  Scroll to top of the page and choose **_Websites_** tab. Click on **_ADD Website_**.
    ![Profiles](../graphics/Lab1_AI_Agent/4.18.gif)

5.  Fill in the respective fields as per the table below:

    | **Parameter Name**            | **Parameter Value**        |
    | ----------------------------- | -------------------------- |
    | Chat Widget Language          | English-US                 |
    | Display Name                  | Flower Shop                |
    | Byline Text                   |                            |
    | Button Text                   | Start Chat                 |
    | First message                 | Hello! Welcome to the chat |
    | PCI Compliance Banner Message | This chat is PCI compliant |
    | Domain                        | \*.w3schools.com           |
    | Set wait time                 | Disabled                   |
    | Set Chat Announcement         | Enabled                    |

6.  Review the configuration and then **Save changes**.

7.  Scroll up, select **_Appearance_** and change the settings:

    > \[Optional\] Widget Color <br/>
    > \[Optional\] Widget Button Type <br/>
    > \[Optional\[ Logo <br/>
    > Enable Emojis <br/>
    > Enable Attachments <br/>

Press **_Save changes_** button at the bottom of the page.
![Profiles](../graphics/Lab1_AI_Agent/4.20.gif)

8.  Scroll up, select **_Widget Visibility_** tab and make sure that **_Force Turn Off Widget_** switch is disabled. Then select **_Widget Visibility_** as **_Show without any restrictions_** and save changes.
    ![Profiles](../graphics/Lab1_AI_Agent/4.21.gif)

9.  Now click on **_<_** arrow near **_Website Settings_** and go-back to edit your chat asset.
    ![Profiles](../graphics/Lab1_AI_Agent/4.22.gif)

10. Select **_Installation_**, then click on **_Copy_** to copy the chat script to clipboard.
    ![Profiles](../graphics/Lab1_AI_Agent/4.23.gif)

### Task 6. Paste the script to the test website

1. Open up [https://www.w3schools.com](https://www.w3schools.com) and click on HTML.
   ![Profiles](../graphics/Lab1_AI_Agent/4.46.gif)

2. Scroll down and click on **Try it Yourself**.
   ![Profiles](../graphics/Lab1_AI_Agent/4.48.gif)

3. Delete the current HTML document details and paste the HTML script that you saved to the clipboard. Then click on "RUN". You should see the chat bubble shows up on the right down corner.
   ![Profiles](../graphics/Lab1_AI_Agent/4.47.gif)

<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>
