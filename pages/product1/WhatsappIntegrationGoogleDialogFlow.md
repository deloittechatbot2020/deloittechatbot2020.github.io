---
title: Whatsapp Integration - Google Dialog Flow
keywords: sample
summary: "This is api document reference for integrating whatsapp platform with chatbot via google dialogdflow..."
sidebar: product1_sidebar
permalink: WhatsappIntegrationGoogleDialogFlow.html
folder: product1

---

``````

``````

Step 1: Twilio
------------------------------

Username: xxxx
Password: yyy

Login Twilio -> Click Three dot icon -> Programmable SMS -> WhatsApp Beta -> Sandbox -> Copy the URL from "WHEN A MESSAGE COMES IN"

https://bots.dialogflow.com/twilio/96762b7a-9689-4122-8d26-7269ee7093db/sms 

From the Twilio dashboard get the Account SID and Auth Token:

Account SID - xxxxxxxxxxxxxxxx
Auth Token  - yyyyyyyyyyyyy


Step 2: Google DialogFlow
--------------------------------

Username: XXXXXXX

Password: YYYYY


Login to dialogflow console -> Integrations -> Twilio (Text Messaging) -> Provide the Account Token, Auth Token and Request URL which are taken from the Twilio and your mobile number -> Click Start


Step 3: WhatsApp
---------------------------------

Save the number +1 415 523 8886 and type **join reader-told**	

All configurations are completed, Now start messaging.