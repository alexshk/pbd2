---
layout: page
title: /v1/products/:product_slug
permalink: /api/v1/products-product-slug/
parent: API Reference
---

# GET /v1/products/:product_slug

This endpoint will return data that can be used to construct a form for requesting a quote. This includes information about the product in general, and rates and loadings that are required to generate a valid quotation.

Each product consists of a number of parameters, both required and optional, that can be used to generate a quote.

## Path params
\
`product_slug`{: .fs-5 } -- string, required param

When providing one of the of the parameters to get a quote, use the identifier property. For instance, from the example response above, to specify that the mode of transport the insured goods are taking is "Land", the relevant value in the JSON object you POST to the quotes endpoint would be:

```json
{
  "transport_mode": "LND"
}
```


{% codetabs %}

{% codetab cURL %}
```shell
curl --request GET \
  --url https://api.staging-agileaperture.com/v1/products/cargo \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJwYXJ0bmVyX2lkIjoiMTIzMzIzNjgtMjcwNS00ZTNiLWI3OTUtY2Y3YWUwOGRlZWE3IiwiaWF0IjoxNTU4NTY5MzY1fQ.q0_oulKwggDw1yQcM877OXhOm2X6sVOhUNnu7_jUzmg' \
  --header 'Content-Type: application/json'
```
{% endcodetab %}

{% codetab Node %}
```js
const fetch = require('node-fetch');

const url = 'https://api.staging-agileaperture.com/v1/products/cargo';

const options = {
  method: 'GET',
  headers: {
    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJwYXJ0bmVyX2lkIjoiMTIzMzIzNjgtMjcwNS00ZTNiLWI3OTUtY2Y3YWUwOGRlZWE3IiwiaWF0IjoxNTU4NTY5MzY1fQ.q0_oulKwggDw1yQcM877OXhOm2X6sVOhUNnu7_jUzmg',
    'Content-Type': 'application/json'
  }
};

fetch(url, options)
  .then(res => res.json())
  .then(json => console.log(json))
  .catch(err => console.error('error:' + err));
```
{% endcodetab %}

{% codetab Ruby %}
```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://api.staging-agileaperture.com/v1/products/cargo")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Get.new(url)
request["Authorization"] = 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJwYXJ0bmVyX2lkIjoiMTIzMzIzNjgtMjcwNS00ZTNiLWI3OTUtY2Y3YWUwOGRlZWE3IiwiaWF0IjoxNTU4NTY5MzY1fQ.q0_oulKwggDw1yQcM877OXhOm2X6sVOhUNnu7_jUzmg'
request["Content-Type"] = 'application/json'

response = http.request(request)
puts response.read_body
```
{% endcodetab %}

{% codetab Javascript %}
```js
const options = {
  method: 'GET',
  headers: {
    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJwYXJ0bmVyX2lkIjoiMTIzMzIzNjgtMjcwNS00ZTNiLWI3OTUtY2Y3YWUwOGRlZWE3IiwiaWF0IjoxNTU4NTY5MzY1fQ.q0_oulKwggDw1yQcM877OXhOm2X6sVOhUNnu7_jUzmg',
    'Content-Type': 'application/json'
  }
};

fetch('https://api.staging-agileaperture.com/v1/products/cargo', options)
  .then(response => console.log(response))
  .catch(err => console.error(err));
```
{% endcodetab %}

{% codetab Python %}
```python
import requests

url = "https://api.staging-agileaperture.com/v1/products/cargo"

headers = {
    "Authorization": "Bearer eyJhbGciOiJIUzI1NiJ9.eyJwYXJ0bmVyX2lkIjoiMTIzMzIzNjgtMjcwNS00ZTNiLWI3OTUtY2Y3YWUwOGRlZWE3IiwiaWF0IjoxNTU4NTY5MzY1fQ.q0_oulKwggDw1yQcM877OXhOm2X6sVOhUNnu7_jUzmg",
    "Content-Type": "application/json"
}

response = requests.request("GET", url, headers=headers)

print(response.text)
```
{% endcodetab %}

{% endcodetabs %}

## Responses examples
\
`200 OK`{: .fs-5 }

```json
{
	"name": "Cargo Cover",
	"pds_url": "https://herokuapp.com/products/cargo/Agile-Cargo-Cover-PDS.pdf",
	"max_insured_value": 500000,
	"benefits": [
		{
			"title": "To your door",
			"description": "This insurance attaches from the time the goods are first moved in the warehouse or at the place of storage for the purpose of the immediate loading into or onto the Conveyance for the commencement of Transit, continues during the ordinary course of transit and terminates on completion of unloading from the Conveyance in or at the final destination as nominated by You."
		},
		{
			"title": "Loss or damage",
			"description": "Subject to the terms, Conditions of Cover and exclusions of this Policy, We will insure You up to the Sum Insured for loss of or damage to the Goods occurring whilst in Transit during the Period of Insurance caused by Accidental Damage."
		}
	],
	"selectors": {
		"insured_items_category": [
			{
				"identifier": "ACID",
				"label": "Acids"
			},
			{
				"identifier": "AGRI",
				"label": "Agricultural Products - bagged"
			}
		],
		"country": [
			{
				"identifier": "AO",
				"label": "Angola"
			},
			{
				"identifier": "AT",
				"label": "Austria"
			},
			{
				"identifier": "SN",
				"label": "Senegal"
			}
		],
		"transport_mode": [
			{
				"identifier": "AIR",
				"label": "Air"
			},
			{
				"identifier": "LND",
				"label": "Land"
			},
			{
				"identifier": "SEA",
				"label": "Sea"
			},
			{
				"identifier": "CMB",
				"label": "Combination"
			}
		]
	}
}
```