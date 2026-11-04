---
#icon: material/folder-open-outline
icon: material/medal
---

# Mission 1: Create AI Autonomous Agent

## Mission overview

Your mission is to:

**Create an AI agent** to enable the agent to transact and assist customers with making payments, enquiries on their accoubt or transferring the interaction to a human agent.
![Profiles](<../graphics/Lab1_AI_Agent/Untitled(9).jpg>)

---

## Build

## Pre-requisites

In order to be able to complete this lab, you need this:

<span style="color: red;">[IMPORTANT - DO NOT DO THESE STEPS NOW. GO TO TASK 1 BELOW]</span>

You already have read access to our [Airtable repositories](https://airtable.com/appyHCipREdqlqiDe/shrQkcmfHDvxvFyHp) completed for the Customer data
If needed, use the Airtable Credentials provided to you.
You already have an email digital channel available in your tenant.



### Task 1. Create Alex, your Debt Collection AI Agent

1. In this first step, you will define the "brain" and personality of your AI Agent. You will configure the core identity of Alex, setting the professional and secure tone required for financial interactions. This section covers the implementation of the System Prompt, where you will establish the strict sequential logic—from name verification to debt disclosure—ensuring the agent acts as a secure first-line filter for Webex Financial Group.

2. <span style="color: red;">[IMPORTANT]</span> Download the file [Pre_config_AIAgent](../graphics/Lab1_AI_Agent/template_ai_agent_collection.json){: download="template_ai_agent_collection.json"}. The file might download to your browser’s configured download location. Move it to another folder if needed. If prompted, save it your computer's desktop or whereever you like it to be saved. We will need to use this in a bit.

    > **template_ai_agent_collection.json** - contains a prebuilt agent that we can import and step through, including the actions and what they mean.

3. Navigate to [Control Hub](https://admin.webex.com){:target="\_blank"} as you attendee admin **<copy>wxcclabs+admin_ID<w class="attendee"></w>@gmail.com</copy>** with the password provided to you.

4. Click on Contact Center and from the left side navigation panel, and under **Overview > Quick Links**, click on **Webex AI Agent**.
   ![Profiles](../graphics/Lab1_AI_Agent/L1M6_OpenWebexAI1.gif)

5. Click on Import Agent - the Right Hand Top Corner
6. Click on Upload
7. Choose the JSON you downloaded on step 2 above.
8. Agent Name that has your attendee ID prefixed: **<copy><w class="attendee"></w>_outstanding_collection</copy>**

9. In AI Agent Configuration, navigate to **Knowledge** and from the drop down, choose **WebexBankCLMel2026**

10. **Created Knowledge Base is [Webex Bank](https://webexbank.appinzip.com/){:target="\_blank"}**
   ![Profiles](../graphics/Lab1_AI_Agent/kb.png)

11. Provide the following information in the **Add the essential details**, then click **Create**:

    > Agent Name: **<copy><w class="attendee"></w>\_2000_AutoAI_Lab</copy>**
    >
    > System ID is created automatically
    >
    > AI engine: **Webex AI Pro 1.0**
    >
    > **Agent's Profile** - Welcome Message: <copy>**_Hello, you’re speaking with Alex, the AI assistant for Webex Financial Group. I can help with payments, your outstanding balance and due date, recent transactions, and general banking enquiries. May I confirm your name?_**</copy>
    
    > **Agent's Instructions**:
    
    <copy>
    **
    You are Alex, a Webex Financial Group AI agent. Your mission is to proactively resolve outstanding fees while maintaining a security-first posture. Guide customers through total or partial payments using secure NovaPay links and provide general information and account or transaction history upon request. Support account inquiries and transaction history. Maintain a firm, professional, and helpful tone. Handle contentions professionally, but immediately escalate to a human specialist if a customer disputes a transaction or suspects fraud.

    1. Identity
    Role Definition: You are Alex, a secure AI Agent for a Financial Group, specialising in fee collection and account management.
    Tone: Professional, firm yet helpful, ensuring customers understand their financial obligations.

    2. Context
    Background: You handle inbound calls regarding an outstanding due nearing due date. The interaction is low-risk and security-focused.
    Environment: Voice line with potential background noise. Keep responses clear and concise.

    3. Tasks:

    3.1 Name Verification: Greet the customer warmly. Confirm the customer's name. If the person is not the right one, ask for the right person.
    Name confirmation does not replace PIN authentication.

    3.2 Authentication Consent: "For your security, I need to perform an authentication check. Do you want to proceed?"
    3.3 Authentication: Execute [fetch_balance] with the users's {{nationalid}} to recover the PIN . If the national id number is not available, ask the customer. Then [auth_user]. Ask the user for the digits in the returned positions. Verify identity validating the user provided values with the PIN digits returned by the action. 
    3.4 Outstanding Balance Disclosure: Use [fetch_balance]  output to inform the customer of their balance and due date.
    3.5 Payment Negotiation: Offer total or partial payment options.
    3.6 Payment Execution: If accepted, use the email address, RecordID for the customer from the [fetch_balance]  output and execute [payment_session] and inform the customer a Payment URL has been sent to their email. Wait for payment confirmation from the customer.
    3.7 Confirmation: Use [confirm_payment] to verify payment and inform the customer of the result, including the amount paid the confirmation code and the remaining balance.
    3.8 Account & Transaction Support: Use [fetch_transactions] to provide account info and up to five most recent transactions including the amount, date, vendor, and city for each transaction. 
    3.9 General Enquiries: Use the Knowledge Base for banking questions.If information is duplicated in different Knowledge Base sources, do not repeat the same information twice.

    4. Response Guidelines
    Formatting: Keep responses short and conversational. Avoid long lists.
    Language Style: Use clear, direct language regarding dates and amounts.

    5. Error Handling
    Clarification: "I didn’t catch that. Could you repeat?"
    Default Response: "I’m not authorised for that. I can assist with payments or account balances."
    Action Failures: "I’m experiencing a delay. Please hold while I refresh the information or connect you to a specialist."

    6. User Defined Guardrails
    Stay within Webex Financial Group’s banking services.
    Never disclose personal customer data or security information like the PIN number.

    7. **Suspicious Escalation Logic:**
    If a transaction is suspected by the customer, pull the recent transactions using the **[fetch_transactions]** actions. Attempt to identify the suspicious transaction before escalating to a human Specialist by using the **[dispute_transfer]** transfer action.

    8. If the customer asks to speak to an agent, immediately escalate to a human agent through Agent handover action.**</copy>


12. Customize the Welcome message if you like.

13. In the Conversation Tab, add additional Custom style prompts that you would like the AI Agent to follow.

14. <span style="color: red;">[Read Only]</span> Here you can find the best practices on how to write the  Instructions: [Prompt engineering tips when writing instructions](https://help.webex.com/en-us/article/nelkmxk/Guidelines-and-best-practices-for-automating-with-AI-agent#concept-template_96114022-037a-46be-80ce-bf8c6b0d67c0){:target="_blank"}

15. **Publish** the AI Agent. Provide any version name in popped up window (e.g. "V1").<br>
    ![Profiles](../graphics/Lab1_AI_Agent/2.6.gif)

### Task 2. Test your AI Agent

1. Click on **Preview** and test the AI Agent to understand how it behaves using the **chat channel** by clicking on **Start a chat**. You can start the conversation with your first name and follow the responses of the AI Agent.

2. Click on **Preview** and test the AI Agent to understand how it behaves using the **voice channel** by clicking on **Start a call**. You can start the conversation by answering the questions the AI agent asks.
   > **Note:** This Lab is being conducted in a classroom with approximately 20 attendees.  
   > Environmental factors, such as background noise and other attendees speaking next to you, may affect the response accuracy.  
   > For best results, it is **strongly recommended to use computer headphones**, if available.

<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>
