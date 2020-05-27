| Name                            | Required     | Description                                                  | Default Value | Example                                                      |
| ------------------------------- | ------------ | ------------------------------------------------------------ | ------------- | ------------------------------------------------------------ |
| userInfo.firstName              | Optional     | Frist name of the user                                       |               | Johnny                                                       |
| userInfo.lastName               | Optional     | Last name of the user                                        |               | Depp                                                         |
| userInfo.uid                    | Yes          | User Id or Customer Id of the user for which order related queries will be carried out |               | John451/ 4578122/ xyz@gmail.com                              |
| userInfo.userName               | Optional     | Username of the user                                         |               |                                                              |
| queryInfo.interestType          | Yes          | Used to identify the request type                            |               | orderDetails,orderStatus,trackingDetails                     |
| entityInfo.orderId              | Yes/Optional | To get the order related information need to pass the orderId, for other questions no need to pass orderId |               | 457852256/8574961EDCF21                                      |
| languageCode                    | Yes          | To identify the language                                     | en            | en, gr, fr                                                   |
|                                 |              |                                                              |               |                                                              |
| response.responseType           | Yes          | Specifies the type of response                               | text          | text, card, media                                            |
| responseMessages.simpleResponse | Optional     | If the response type is set to "text" then the respective text response should be appened here |               | "simpleResponse": {        "responseText": "My response"       } |
| responseMessages.basicCard      | Optional     | If the response type is set to "card" then the respective card response should be appened here |               | "basicCard": {        "title": "Product Detail",        "subtitle": "This is a subtitle",        "formattedText": "This is a basic card. Text in a basic card can include \"quotes\" and\n  most other unicode characters including emojis. Basic cards also support",        "image": {         "url": "https://storage.googleapis.com/actionsresources/logo_assistant_2x_64dp.png",         "accessibilityText": "Image alternate text"        }       } |
| responseMessages.mediaResponse  | Optional     | If the response type is set to "media" then the respective media response should be appened here. |               | "mediaResponse": {        "mediaType": "AUDIO",        "mediaObjects": [         {          "contentUrl": "https://storage.googleapis.com/Jazz_Paris.mp3",          "description": "A funky Jazz tune",          "icon": {           "url": "https://storage.googleapis.com/album_art.jpg",           "accessibilityText": "Album ocean view"          },          "name": "Jazz in Paris"         }        ]       } |



| Sample Request and Response                   |
| --------------------------------------------- |
| **Endpoint : /api/rest/v1/ecom/integrations** |



```
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
    "interestType": "cancelOrder",
    "parameters": {
      "params": {
        "entityInfo": {
          "orderId": "748596"
        }
      }
    }
  },
  "languageCode": "en",
  "response": {
    "responseType": "text",
    "responseId": "be49e7a0-8638-486b-899b-be42e3760b46-e15c53b8",
    "responseMessages": [
      {
        "simpleResponse": {
          "responseText": "Order 748596 cancelled"
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
}
```

