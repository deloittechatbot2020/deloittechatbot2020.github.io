---
title: Update User Password
keywords: sample
summary: "This is api document reference for update password..."
sidebar: product1_sidebar
permalink: UpdatePassword.html
folder: product1

---




## POST /updateUserChangePasswrod

updates the user contact information like email address and phone number

## Resource URL

/api/rest/v1/ecom/integrations/updateUserChangePasswrod

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name                        | Required      | Description                                                  | Default | Value             |
| --------------------------- | ------------- | ------------------------------------------------------------ | ------- | ----------------- |
| firstName                   | Optional      | First name of the user                                       |         | Ram               |
| lastName                    | Optional      | Last name of the user                                        | -       | Srini             |
| userName                    | Semi Optional | username of the user(retrieved from channel of the chat bot) | -       | ram123            |
| uuid                        | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -       | ram123@gmail.com  |
| interestType                | Yes           | identifier of the caller api for integrating backend client  | -       | cancel-order      |
| languageCode                | Yes           | Language of communication                                    | en-US   | en-US/en-AU/en-UK |
| responseType                | Yes           | type of response                                             | text    | text/card/media   |
| params                      | Yes           | parameters that required for the business to functionate     |         |                   |
| accountInfo.oldPassword     | Yes           | holds the current password of the user                       |         |                   |
| accountInfo.newPassword     | Yes           | holds the new password of the user                           |         | door # 123        |
| accountInfo.confirmPassword | Yes           | holds the confirm password of the user                       |         |                   |
| simpleResponse              | Semi Optional | simple text response if the responseType is "Text"           |         |                   |



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
		"interestType": "change-password",
		"parameters": {
			"params": {
				"accountInfo": {
					"oldPassword": "oldPassword",
					"newPassword": "password",
					"confirmPassword": "password"
				}
			}
		}
	}
}
``````

## Example Response

``````json
{
    "responseType": "text",
    "responseId": "be49e7a0-8638-486b-899b-be42e3760b46-e15c53b8",
    "responseMessages": [
        {
            "simpleResponse": {
                "responseText": "password changed successfully"
            }
        }
    ]
}
``````