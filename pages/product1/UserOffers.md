---
title: User Offers
keywords: sample
summary: "This is api document reference for getting user offers..."
sidebar: product1_sidebar
permalink: UserOffers.html
folder: product1

---




## GET /getUserOffersByUserId

Receives the user detail information for the queried user

## Resource URL

/api/rest/v1/ecom/integrations/getUserOffersByUserId?uuid=rsrinivasan@deloitte.com

## Resource Information

| Type                     | Value |
| ------------------------ | ----- |
| Response formats         | JSON  |
| Requires authentication? | Yes   |

## Parameters

| Name         | Required      | Description                                                  | Default | Value                    |
| ------------ | ------------- | ------------------------------------------------------------ | ------- | ------------------------ |
| firstName    | Optional      | First name of the user                                       | -       | Ram                      |
|              |               |                                                              |         |                          |
| lastName     | Optional      | Last name of the user                                        | -       | Srini                    |
| userName     | Semi Optional | username of the user(retrieved from channel of the chat bot) | -       | ram123                   |
| uuid         | Yes           | unique identifier of the user to communicate with the client,could be email id of the user/chat id etc | -       | rsrinivasan@deloitte.com |
| interestType | Yes           | identifier of the caller api for integrating backend client  | -       | user-offers              |
| languageCode | Yes           | Language of communication                                    | en-US   | en-US/en-AU/en-UK        |
| responseType | Yes           | type of response                                             | text    | text/card/media          |
| params       | Yes           | parameters that required for the business to functionate     |         |                          |
| offersList   | Semi Optional | this is the response in array data structure for user's offers | list    | list                     |



## Example Endpoint 

``````json
https://localhost:8080/api/rest/v1/ecom/integrations/getUserOffersByUserId?uuid=rama1234@gmail.com
``````

## Example Response

``````json
{
	"responseType": "text",
	"responseId": "be49e7a0-8638-486b-899b-be42e3760b46-e15c53b8",
	"responseMessages": [{
		"offersList": [{
				"offerId": 1,
				"name": "Mega Laptop mela",
				"offerType": "product",
				"imageUrl": "https://nurserylive.com/images/stories/virtuemart/category/nurserylive-off.png",
				"isSeasonalOffer": false,
				"offerDescription": "Up to 40% off with Back to College Offer on Laptops",
				"validity": "45 days"
			},
			{
				"offerId": 2,
				"name": "Diwali bonaza",
				"offerType": "user",
				"imageUrl": "https://nurserylive.com/images/stories/virtuemart/category/nurserylive-off.png",
				"isSeasonalOffer": true,
				"offerDescription": "Buy one get one on all HDFC card users",
				"validity": "15 days"
			}
		]
	}]
}
``````