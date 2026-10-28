### AI Autonomous Agent Overview

The Autonomous AI Agent can handle various tasks, including:

- Natural Language Processing (NLP) — Understand and respond to human language in a natural and conversational manner.
- Decision making — Make informed choices based on available information and predefined rules.
- Automation — Automate repetitive or time-consuming tasks.
</details>

## Story

In this lab, you will connect inbound callers to Alex, an autonomous AI Agent for Webex Financial Group. Alex is not just a chatbot; it is a specialized financial assistant designed to handle the sensitive process of fee collection, account inquiries, and fraud detection. This lab will guide you through configuring the AI's persona, its strict security protocols and its ability to execute real-time financial actions.</br></br>
Remember, **customers will trust the AI Agent only when they truly believe it can assist them effectively**. That’s exactly what you’ll be working to achieve in this lab!

## Lab Objective

The purpose of this lab is to transform a standard call into a secure, automated financial transaction. You will configure the AI Agent to automate the debt collection process.

Key objectives include:

Persona Implementation: Configuring the AI Agent persona to be professional, firm, and helpful.
Automated Fee Payment: Use the NovaPay service to Create a payment session for the customer to realise the payment.
Customer Enquiry: Incorporate Knowledge for Alex to properly respond to customer enquiries. We will use the URL injection for this.
Risk Management: Implementing escalation logic that identifies fraudulent or suspicious transactions and triggers a hand-off to a human specialist with all relevant transaction context.


## Lab Outcome
By the end of the lab, you will have a fully operational AI Agent integrated into your flow. The agent will be capable of:

Secure Verification: Confirming the identity of the recipient and obtaining consent for an authentication check.
Debt Resolution: Informing customers of their balance and maturity dates, then negotiating total or partial payments.
Financial Execution: Creating real-time payment sessions via NovaPay and confirming completion to update the Debt Database.
Account Support: Providing transaction histories and general account details (Balance, etc.) upon request.
