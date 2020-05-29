---
title: Place Order
keywords: sample
summary: "This is api document reference for placing the order..."
sidebar: product1_sidebar
permalink: CreateOrder.html
folder: product1

---




## POST /placeOrder

place order request for the items added in the cart and ready for checkout and reviewed

## Resource URL

/api/rest/v1/ecom/integrations/placeOrder

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name              | Required      | Description                                                  | Default | Value               |
| ----------------- | ------------- | ------------------------------------------------------------ | ------- | ------------------- |
| firstName         | Optional      | First name of the user                                       | -       | Ram                 |
|                   |               |                                                              |         |                     |
| lastName          | Optional      | Last name of the user                                        | -       | Srini               |
| userName          | Semi Optional | username of the user(retrieved from channel of the chat bot) | -       | ram123              |
| uuid              | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -       | ram123@gmail.com    |
| interestType      | Yes           | identifier of the caller api for integrating backend client  | -       | orderStatus         |
| languageCode      | Yes           | Language of communication                                    | en-US   | en-US/en-AU/en-UK   |
| entityInfo        | Optional      | depends on the service to be called params for entityInfo should be provided |         | orderID=1234        |
| items             | Yes           | list of items/products that are added in cart and ready to be checked out and placing the order |         | shoes               |
| items.productId   | Yes           | unique SKU id of the product                                 |         | 12345               |
| items.quantity    | Yes           | number of quantities                                         | 1       | 4 nos               |
| items.categoryId  | Yes           | unique Category SKU id of the product                        |         | 1111(shoes)         |
| paymentInfo       | Yes           | includes a type of payment/amount/paymentMode                |         | creditCard/5000/emi |
| containerResponse | Yes           | Container response hold the order transaction information    |         |                     |



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
		"interestType": "createOrder",
		"parameters": {
			"params": {
				"entityInfo": {
					"items": [{
							"productId": "12345",
							"Quantity": "1",
							"categoryId": "11111"
						},
						{
							"productId": "24680",
							"Quantity": "5",
							"categoryId": "22222"
						}
					]
				},
				"paymentInfo": {
					"paymentType": "credit card",
					"amount": 50000,
					"paymentMode": "regular/emi/pay later"

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
		"responseType": "container",
		"responseId": "be49e7a0-8638-486b-899b-be42e3760b46-e15c53b8",
		"responseMessages": [{
			"containerResponse": {
				"responseText": "Order 23456 has been created. Transaction number is 86754.",
				"attributes": [{
						"name": "orderId",
						"value": "23456"
					},
					{
						"name": "transactionId",
						"value": "87456"
					},
					{
						"name": "orderStatus",
						"value": "Placed"
					}
				]
			}
		}]
	}
}
``````