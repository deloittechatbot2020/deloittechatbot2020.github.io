---
title: Cancel Order Topic (Product 1)
keywords: sample
summary: "This is just a sample topic..."
sidebar: product1_sidebar
permalink: CancelOrder.html
folder: product1

---




## POST /cancelOrder

performs cancelling the order

## Resource URL

/api/rest/v1/ecom/integrations/cancelOrder

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name               | Required      | Description                                                  | Default | Value             |
| ------------------ | ------------- | ------------------------------------------------------------ | ------- | ----------------- |
| firstName          | Optional      | First name of the user                                       | -       | Ram               |
|                    |               |                                                              |         |                   |
| lastName           | Optional      | Last name of the user                                        | -       | Srini             |
| userName           | Semi Optional | username of the user(retrieved from channel of the chat bot) | -       | ram123            |
| uuid               | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -       | ram123@gmail.com  |
| interestType       | Yes           | identifier of the caller api for integrating backend client  | -       | cancel-order      |
| languageCode       | Yes           | Language of communication                                    | en-US   | en-US/en-AU/en-UK |
| responseType       | Yes           | type of response                                             | text    | text/card/media   |
| params             | Yes           | parameters that required for the business to functionate     |         |                   |
| entityInfo.orderID | Yes           | order id value required to cancel the order                  |         | 12345             |
| simpleResponse     | Semi Optional | simple text response if the responseType is "Text"           |         |                   |



## Example Request



``````json
{
  "conversationRequest": {
  "channel": "telegram",
    "userInfo": {
      "first_name": "Ravi",
      "last_name": "R",
      "uid": "51342",
      "username": "ravir"
    }
  },
  "queryInfo": {
    "interestType": "cancel-order",
    "parameters": {
      "params": {
        "entityInfo": {
          "orderId": "748596"
        }
      }
    }
  },
  "languageCode": "en",
}
``````

## Example Response

``````json
{ "response": {
    "responseType": "text",
    "responseId": "be49e7a0-8638-486b-899b-be42e3760b46-e15c53b8",
    "responseMessages": [
      {
        "simpleResponse": {
          "responseText": "Order 748596 has been cancelled"
        }
      }
    ]
  }
``````