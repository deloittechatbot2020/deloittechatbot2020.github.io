---
title: Browse/Show Products
keywords: sample
summary: "This is api document reference for browsing the catalogs/products..."
sidebar: product1_sidebar
permalink: BrowseProducts.html
folder: product1

---




## POST /showProducts

fetch the available products based on the query for browsing

## Resource URL

/api/rest/v1/ecom/integrations/showProducts

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name                      | Required      | Description                                                  | Default | Value             |
| ------------------------- | ------------- | ------------------------------------------------------------ | ------- | ----------------- |
| firstName                 | Optional      | First name of the user                                       | -       | Ram               |
|                           |               |                                                              |         |                   |
| lastName                  | Optional      | Last name of the user                                        | -       | Srini             |
| userName                  | Semi Optional | username of the user(retrieved from channel of the chat bot) | -       | ram123            |
| uuid                      | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -       | ram123@gmail.com  |
| interestType              | Yes           | identifier of the caller api for integrating backend client  | -       | orderStatus       |
| languageCode              | Yes           | Language of communication                                    | en-US   | en-US/en-AU/en-UK |
| entityInfo                | Optional      | depends on the service to be called params for entityInfo should be provided |         | orderID=1234      |
| category                  | Yes           | type of category                                             |         | shoes             |
| category.lookup           | Yes           | emerging category like latest trends etc                     |         |                   |
| category.filter           | Optional      | filter by price/type/color                                   |         |                   |
| category.filter.attribute | Optional      | can be price/type/color                                      |         | color             |
| category.filter.value     | Optional      | depends on the attribute type "category.filter.value" is mandatory |         | yellow            |
| catalogResponse           | Yes           | Calatlog response that contains the list of products with assigned filters along with their details with image url |         |                   |



## Example Request



``````json
{
  "conversationRequest": {
  "channel": "TELEGRAM",
    "userInfo": {
      "first_name": "vignesh",
      "last_name": "m",
      "uid": "vigneshm@deloitte.com",
      "username": "vigneshm"
    }
  },
  "queryInfo": {
    "interestType": "showProducts",
    "parameters": {
      "params": {
        "entityInfo": {
          "category": "Shoes",
                               "lookUp" : "latest trending shoes",
                               "filter" : [
                                {
                                   "attribute" : "price range",
                                             "value" : ">2000"
                                },
                                {
                                   "attribute" : "type",
                                             "value" : "causal"
                                },
                                {
                                   "attribute" : "color",
                                             "value" : "any"
                                }
                                ]
        }
      }
    }
  },
  "languageCode": "en",
  "response": {}
}

``````

## Example Response

``````json
{
	"response": {
		"responseType": "catalogue",
		"responseId": "be49e7a0-8638-486b-899b-be42e3760b46-e15c53b8",
		"responseMessages": [{
			"catalogResponse": {
				"items": [{
						"productId": "12345",
						"categoryId": "11111",
						"title": "Test 1",
						"description": "Desc 2",
						"category": "Category1",
						"image": {
							"url": "[some url]",
							"imageText": "productName1"
						},
						"openUrlAction": {
							"url": "[some url]"
						},
						"price": {
							"priceType": "INR",
							"value": "150"
						},
						"stock": {
							"stockLevel": "100",
							"stockStatus": "InStock"
						}
					},
					{
						"productId": "24680",
						"categoryId": "22222",
						"title": "Test 2",
						"description": "Desc 2",
						"category": "Category2",
						"image": {
							"url": "[some url]",
							"imageText": "productName2"
						},
						"openUrlAction": {
							"url": "[some url]"
						},
						"price": {
							"priceType": "INR",
							"value": "5000"
						},
						"stock": {
							"stockLevel": "5",
							"stockStatus": "InStock"
						}
					}
				],
				"filter": [{
						"attribute": "price range",
						"value": ">2000"
					},
					{
						"attribute": "type",
						"value": "causal"
					},
					{
						"attribute": "color",
						"value": "any"
					}
				]
			}
		}]
	}
}
``````