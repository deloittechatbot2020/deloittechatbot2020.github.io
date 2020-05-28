---
title: User Detail Topic
keywords: sample
summary: "This is api document reference for getting user information..."
sidebar: product1_sidebar
permalink: UserDetails.html
folder: product1

---




## GET /getUserInfo

Receives the user detail information for the queried user

## Resource URL

/api/rest/v1/ecom/integrations/getUserInfo?uuid=rama1234@gmail.com

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name                    | Required      | Description                                                  | Default | Value             |
| ----------------------- | ------------- | ------------------------------------------------------------ | ------- | ----------------- |
| firstName               | Optional      | First name of the user                                       | -       | Ram               |
|                         |               |                                                              |         |                   |
| lastName                | Optional      | Last name of the user                                        | -       | Srini             |
| userName                | Semi Optional | username of the user(retrieved from channel of the chat bot) | -       | ram123            |
| uuid                    | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -       | ram123@gmail.com  |
| interestType            | Yes           | identifier of the caller api for integrating backend client  | -       | cancel-order      |
| languageCode            | Yes           | Language of communication                                    | en-US   | en-US/en-AU/en-UK |
| responseType            | Yes           | type of response                                             | text    | text/card/media   |
| params                  | Yes           | parameters that required for the business to functionate     |         |                   |
| userAccount.userAddress | Yes           | holds the user address in this format addr1,addr2,city,state,country,zip |         |                   |
| userAccount.userContact | Yes           | holds the user contact information like email and phone number in format emailId and phoneNumber |         |                   |
| simpleResponse          | Semi Optional | simple text response if the responseType is "Text"           |         |                   |



## Example Endpoint 

``````json
https://localhost:8080/api/rest/v1/ecom/integrations/getUserInfo?uuid=rama1234@gmail.com
``````

## Example Response

``````json
{
    "responseType": "text",
    "responseId": "be49e7a0-8638-486b-899b-be42e3760b46-e15c53b8",
    "responseMessages": [
        {
            "simpleResponse": {
                "responseText": "Account info fetched successfully"
            }
        },
        {
            "userAccount": {
                "userName": "Ram Srini",
                "userAddress": {
                    "addr1": "NO:4/47 Door NO:F1, Bala Sai Darshan",
                    "addr2": "13 th Main Road Vijayanagar,Velacherry",
                    "state": "Tamil Nadu",
                    "city": "Chennai",
                    "country": "India",
                    "zip": "600042"
                },
                "userContact": {
                    "emailId": "rsrinvasan@deloitte.com",
                    "phoneNumber": "+91-986542786"
                }
            }
        }
    ]
}
``````