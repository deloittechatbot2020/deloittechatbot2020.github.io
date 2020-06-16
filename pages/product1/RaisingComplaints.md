---
title: Raising Complaints
keywords: sample
summary: "This is api document reference for raising complaints against order..."
sidebar: product1_sidebar
permalink: RaisingComplaints.html
folder: product1

---




## POST /raiseComplaintsAgainstOrder

Raising the complaint against an/the orders respectively

## Resource URL

/api/rest/v1/ecom/integrations/raiseComplaintsAgainstOrder

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name               | Required      | Description                                                  | Default          | Value                         |
| ------------------ | ------------- | ------------------------------------------------------------ | ---------------- | ----------------------------- |
| firstName          | Optional      | First name of the user                                       | -                | Ram                           |
|                    |               |                                                              |                  |                               |
| lastName           | Optional      | Last name of the user                                        | -                | Srini                         |
| userName           | Semi Optional | username of the user(retrieved from channel of the chat bot) | -                | ram123                        |
| uuid               | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -                | ram123@gmail.com              |
| interestType       | Yes           | identifier of the caller api for integrating backend client  | -                | raise-complaints              |
| languageCode       | Yes           | Language of communication                                    | en-US            | en-US/en-AU/en-UK             |
| entityInfo.orderId | Optional      | order Id required to raise complaints                        |                  | 12345                         |
| responseType       | Yes           | type of response                                             | text             | text/card/media               |
| simpleResponse     | Semi Optional | simple text response if the responseType is "Text"           |                  |                               |
| attributes         | Yes           | expects the attributes required in return with respect to the interest type | key-value (pair) | name:complaintId,value:123456 |



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
		"interestType": "productComplaint",
		"parameters": {
			"params": {
				"entityInfo": {
					"orderId": "748596",
					"problemStatment": "Product Not working. Need to service.",
					"category": "product-related"
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
		"responseType": "container",
		"responseId": "be49e7a0-8638-486b-899b-be42e3760b46-e15c53b8",
		"responseMessages": [{
			"containerResponse": {
				"responseText": "Your complaint is registered. Raised a complaint Number 12345 to track.",
				"attributes": [{
						"name": "orderId",
						"value": "748596"
					},
					{
						"name": "complaintId",
						"value": "12345"
					},
					{
						"name": "Category",
						"value": "products-related"
					}
				]
			}
		}]
	}
}
``````