---
title: Update User Address Topic (Product 1)
keywords: sample
summary: "This is just a sample topic..."
sidebar: product1_sidebar
permalink: UpdateUserAddress.html
folder: product1

---




## POST /updateUserAddressDetails

updates the user address information

## Resource URL

/api/rest/v1/ecom/integrations/updateUserAddressDetails

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name                    | Required      | Description                                                  | Default | Value             |
| ----------------------- | ------------- | ------------------------------------------------------------ | ------- | ----------------- |
| firstName               | Optional      | First name of the user                                       | -       | Ram               |
| lastName                | Optional      | Last name of the user                                        | -       | Srini             |
| userName                | Semi Optional | username of the user(retrieved from channel of the chat bot) | -       | ram123            |
| uuid                    | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -       | ram123@gmail.com  |
| interestType            | Yes           | identifier of the caller api for integrating backend client  | -       | cancel-order      |
| languageCode            | Yes           | Language of communication                                    | en-US   | en-US/en-AU/en-UK |
| responseType            | Yes           | type of response                                             | text    | text/card/media   |
| params                  | Yes           | parameters that required for the business to functionate     |         |                   |
| accountInfo.userAddress | Yes           | holds the user address in this format addr1,addr2,city,state,country,zip |         |                   |
| userAddress.addr1       | Yes           | holds the address line 1                                     |         | door # 123        |
| userAddress.addr2       | Yes           | holds the address line 1                                     |         |                   |
| userAddress.city        | Yes           | holds the city name                                          |         |                   |
| userAddress.state       | Yes           | holds the state name                                         |         |                   |
| userAddress.country     | Yes           | holds the country name                                       |         |                   |
| userAddress.zip         | Yes           | holds the pincode/zip code                                   |         |                   |
| simpleResponse          | Semi Optional | simple text response if the responseType is "Text"           |         |                   |



## Example Request

``````json
{
	"conversationRequest": {
		"userInfo": {
			"uid": "$uid",
			"last_name": "$lastName",
			"first_name": "$firstName",
			"username": "$userName"
		},
		"channel": "$platForm"
	},
	"queryInfo": {
		"response": {},
		"interestType": "update-address",
		"languageCode": "languageCode",
		"parameters": {
			"params": {
				"accountInfo": {
					"userAddress": {
						"zip": "$pincode",
						"country": "$country",
						"addr2": "$addressNo2",
						"addr1": "$addressNo1",
						"city": "$city",
						"state": "$state"
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
          "responseText": "User Address details updated successfully "
        }
      }]
     
}
``````