---
title: Tracking Complaints
keywords: sample
summary: "This is api document reference for tracking complaints details..."
sidebar: product1_sidebar
permalink: TrackingComplaintsDetails.html
folder: product1

---




## POST /getComplaintsTrackingDetails

Returns the tracking details of the complaint raised based on the type of complaints(products/order/account etc)

## Resource URL

/api/rest/v1/ecom/integrations/getComplaintsTrackingDetails

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name                   | Required      | Description                                                  | Default | Value               |
| ---------------------- | ------------- | ------------------------------------------------------------ | ------- | ------------------- |
| firstName              | Optional      | First name of the user                                       | -       | Ram                 |
|                        |               |                                                              |         |                     |
| lastName               | Optional      | Last name of the user                                        | -       | Srini               |
| userName               | Semi Optional | username of the user(retrieved from channel of the chat bot) | -       | ram123              |
| uuid                   | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -       | ram123@gmail.com    |
| interestType           | Yes           | identifier of the caller api for integrating backend client  | -       | tracking-complaints |
| languageCode           | Yes           | Language of communication                                    | en-US   | en-US/en-AU/en-UK   |
| entityInfo.orderId     | Optional      | order Id required to track the order                         |         | 12345               |
| entityInfo.complaintId | Yes           | complaint Id required to track the raised complaints         |         | 1111                |
| responseType           | Yes           | type of response                                             | text    | text/card/media     |
| simpleResponse         | Semi Optional | simple text response if the responseType is "Text"           |         |                     |



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
		"interestType": "trackComplaint",
		"parameters": {
			"params": {
				"entityInfo": {
					"orderId": "748596",
					"complaintId": "12345"
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
				"responseText": "Your patience is appreciated. Your complaint number 22 is being worked on. It will be resolved within 24 hours. For further queries kindly contact our customer service"
			}
		}]
	}
}
``````