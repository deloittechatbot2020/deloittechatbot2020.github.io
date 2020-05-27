```
---
title: Order status Topic (Product 1)
keywords: sample
summary: "This is just a sample topic..."
sidebar: product1_sidebar
permalink: OrderStatus.html
folder: product1

---
```



## POST /getOrderStatus

Returns the order status of the placed order

## Resource URL

/api/rest/v1/ecom/integrations/getOrderStatus

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name           | Required      | Description                                                  | Default Value                                                | Example                                                      |
| :------------- | :------------ | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| firstName      | Optional      | First name of  the user                                      |                                                              | Ram                                                          |
| lastName       | Optional      | Last name of the user                                        |                                                              | Srini                                                        |
| userName       | Optional      | Full/User name of the user depends on the channel            |                                                              | ramcassini                                                   |
| uuid           | Yes           | The user ID of the user who owns the list being requested by a `slug`. |                                                              | John451/ 4578122/ xyz@gmail.com                              |
| interestType   | Yes           | Used to identify the request type                            |                                                              | orderDetails,orderStatus,trackingDetails                     |
| languageCode   | semi-optional | To identify the language                                     | en-US                                                        | en-US,en-AU,en-UK                                            |
| responseType   | Yes           | Specifies the type of response                               | text                                                         | text, card, media                                            |
| simpleResponse | Yes           | If the response type is set to "text" then the respective text response should be appened here | ``                                                           | ```"simpleResponse": {        "responseText": "My response"       }``` |
| basicCard      | Optional      | If the response type is set to "card" then the respective card response should be appened here |                                                              |                                                              |
| mediaResponse  | Optional      |                                                              | If the response type is set to "media" then the respective media response should be appened here. |                                                              |



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
    "interestType": "orderStatus",
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