---
title: Update User Contact
keywords: sample
summary: "This is api document reference for update user contact..."
sidebar: product1_sidebar
permalink: UpdateUserContact.html
folder: product1

---




## POST /updateUserContactDetails

updates the user contact information like email address and phone number

## Resource URL

/api/rest/v1/ecom/integrations/updateUserContactDetails

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name                    | Required      | Description                                                  | Default | Value             |
| ----------------------- | ------------- | ------------------------------------------------------------ | ------- | ----------------- |
| firstName               | Optional      | First name of the user                                       |         | Ram               |
| lastName                | Optional      | Last name of the user                                        | -       | Srini             |
| userName                | Semi Optional | username of the user(retrieved from channel of the chat bot) | -       | ram123            |
| uuid                    | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -       | ram123@gmail.com  |
| interestType            | Yes           | identifier of the caller api for integrating backend client  | -       | cancel-order      |
| languageCode            | Yes           | Language of communication                                    | en-US   | en-US/en-AU/en-UK |
| responseType            | Yes           | type of response                                             | text    | text/card/media   |
| params                  | Yes           | parameters that required for the business to functionate     |         |                   |
| accountInfo.userContact | Yes           | holds the user contact info in this format phoneNumber,emailId |         |                   |
| userContact.phoneNumber | Yes           | holds the phone number of the user                           |         | door # 123        |
| userContact.emailId     | Yes           | holds the email address of the user                          |         |                   |
| simpleResponse          | Semi Optional | simple text response if the responseType is "Text"           |         |                   |



## Example Request

``````json
{
	"response": {},
	"conversationRequest": {
		"userInfo": {
			"uid": "$uid",
			"last_name": "$lastName",
			"first_name": "$firstName",
			"username": "$userName"
		},
		"channel": "$platForm"
	},
	"languageCode": "languageCode",
	"queryInfo": {
		"interestType": "update-address",
		"parameters": {
			"params": {
				"accountInfo": {
					"userContact": {
						"phoneNumber": "$phoneNumber",
						"emailId": "$emailId"
					}
				}
			}
		}
	}
}
``````

## Example Response

``````json
{"responseType": "text",
    "responseId": "be49e7a0-8638-486b-899b-be42e3760b46-e15c53b8",
    "responseMessages": [
      {
        "simpleResponse": {
          "responseText": "User Contact details updated successfully "
        }
      }]
     
}
``````