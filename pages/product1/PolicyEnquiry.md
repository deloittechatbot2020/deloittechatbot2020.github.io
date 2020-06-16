---
title: Policy Enquiry
keywords: sample
summary: "This is api document reference for enquiring about the policy of particulars by categories..."
sidebar: product1_sidebar
permalink: PolicyEnquiry.html
folder: product1

---




## POST /policyEnquiryByCategory

Enquiring about the policy of any particulars by category

## Resource URL

/api/rest/v1/ecom/integrations/policyEnquiryByCategory

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name                | Required      | Description                                                  | Default | Value                         |
| ------------------- | ------------- | ------------------------------------------------------------ | ------- | ----------------------------- |
| firstName           | Optional      | First name of the user                                       | -       | Ram                           |
|                     |               |                                                              |         |                               |
| lastName            | Optional      | Last name of the user                                        | -       | Srini                         |
| userName            | Semi Optional | username of the user(retrieved from channel of the chat bot) | -       | ram123                        |
| uuid                | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -       | ram123@gmail.com              |
| interestType        | Yes           | identifier of the caller api for integrating backend client  | -       | policy-enquiry                |
| languageCode        | Yes           | Language of communication                                    | en-US   | en-US/en-AU/en-UK             |
| entityInfo.enquiry  | Yes           | enquiry statement                                            |         | what is the refund statement? |
| entityInfo.category |               | type of policy category                                      |         | refund                        |
| responseType        | Yes           | type of response                                             | text    | text/card/media               |
| simpleResponse      | Semi Optional | simple text response if the responseType is "Text"           |         |                               |
| listResponse        | Yes           | if the response has one to many statements to happen/answer  | list    | "list":{"abc","123"}          |



## Example Request



``````json
{
	"conversationRequest": {
		"channel": "TELEGRAM",
		"userInfo": {
			"first_name": "Vignesh",
			"last_name": "M",
			"uid": "39987",
			"username": "vigneshm"
		}
	},
	"queryInfo": {
		"interestType": "policy-enquiry",
		"parameters": {
			"params": {
				"entityInfo": {
					"enquiry": "What is the default refund policy",
					"category": "refund"
				}
			}
		}
	},
	"languageCode": "en"
}
``````

## Example Response

``````json
{
	"response": {
		"responseType": "text",
		"responseId": "be49e7a0-8638-486b-899b-be42e3760b46-e15c53b8",
		"responseMessages": [{
				"simpleResponse": {
					"responseText": "Below are the refund policy : 1. Default refund mode is through wallet.2. Refund will be provided within 72 hours from refund initiation."
				}
			},
			{
				"listResponse": {
					"list": ["Default refund mode is through wallet", "Refund will be provided within 72 hours from refund initiation."]
				}
			}
		]
	}
}
``````