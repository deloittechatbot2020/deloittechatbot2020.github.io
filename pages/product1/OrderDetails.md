---
title: Order Details
keywords: sample
summary: "This is api document reference for order details..."
sidebar: product1_sidebar
permalink: OrderDetails.html
folder: product1

---




## POST /getOrderDetails

Returns the order details of the placed order

## Resource URL

/api/rest/v1/ecom/integrations/getOrderDetails

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name           | Required      | Description                                                  | Default | Value             |
| -------------- | ------------- | ------------------------------------------------------------ | ------- | ----------------- |
| firstName      | Optional      | First name of the user                                       | -       | Ram               |
|                |               |                                                              |         |                   |
| lastName       | Optional      | Last name of the user                                        | -       | Srini             |
| userName       | Semi Optional | username of the user(retrieved from channel of the chat bot) | -       | ram123            |
| uuid           | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -       | ram123@gmail.com  |
| interestType   | Yes           | identifier of the caller api for integrating backend client  | -       | order-details     |
| languageCode   | Yes           | Language of communication                                    | en-US   | en-US/en-AU/en-UK |
| responseType   | Yes           | type of response                                             | text    | text/card/media   |
| simpleResponse | Semi Optional | simple text response if the responseType is "Text"           |         |                   |
| basicCard      | Semi Optional | card response if the responseType is "card"                  |         |                   |
| mediaResponse  | Semi Optional | media response if the responseType is "media"                |         |                   |



## Example Request



``````json
{
  "conversationRequest": {
  "channel": "TELEGRAM",
    "userInfo": {
      "first_name": "Ravi",
      "last_name": "R",
      "uid": "51342",
      "username": "ravir"
    }
  },
  "queryInfo": {
    "interestType": "order-details",
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
          "responseText": "Order 748596 has been shipped"
        }
      },
      {
        "basicCard": {
          "title": "Product Detail",
          "subtitle": "This is a subtitle",
          "formattedText": "This is a basic card.  Text in a basic card can include \"quotes\" and\n    most other unicode characters including emojis",
          "image": {
            "url": "https://storage.googleapis.com/logo_assistant.png",
            "accessibilityText": "Image alternate text"
          }
        },
        "mediaResponse": {
          "mediaType": "AUDIO",
          "mediaObjects": [
            {
              "contentUrl": "https://storage.googleapis.com/Jazz_In_Paris.mp3",
              "description": "A funky Jazz tune",
              "icon": {
                "url": "https://storage.googleapis.com/album_art.jpg",
                "accessibilityText": "Album cover of an ocean view"
              },
              "name": "Jazz in Paris"
            }
          ]
        }
      }
    ]
  }
``````