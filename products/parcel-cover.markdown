---
layout: page
title: Parcel Cover
permalink: /products/parcel-cover
parent: Products
---

# Parcel Cover

Provides protection against all risks of physical loss or damage to goods from any external cause during shipping, whether by land, sea or air.

---

## Parameter Explanations

| Parameter    | Type   | Description |
|:-------------|:-------|:------------|
| `product`    | String | The product slug: "parcel" |
| `origin_country`    | String | The Alpha-2 code for the country where the goods begin their journey. Must be a value from the list supplied by product info |
| `destination_country`    | String | The Alpha-2 code for the country where the goods will end their journey. Must be a value from the list supplied by product info |
| `transport_mode`    | String | The transport method used to ship the goods, must be a value from the list supplied by product info |
| `items`    | String | An array of items to be insured, see below |
| `region`    | String | The state where the shipper of the goods resides |
| `name`    | String | The name of the person responsible for the policy |
| `email`    | String | The email address of the person responsible for the policy |
| `name_of_insured` (optional)   | String | The name of a business or another person who is the actual policy holder |

Each Item in the array of `items` must contain to the following parameters:

| Parameter    | Type   | Description |
|:-------------|:-------|:------------|
| `insured_item_category`    | String | The category of the item, the identifer of a value from the list of categories supplied by product info |
| `insured_item_description`    | String | A text description of the item |
| `insured_item_value`    | Number | The value of the item in dollars |

## Minimum Parameters to get a quote

```json
{
  "product": "parcel",
  "origin_country": "AU",
  "destination_country": "AU",
  "transport_mode": "LND",
  "items": [
    {
      "insured_item_category": "BOOK",
      "insured_item_description": "Rare books",
      "insured_item_value": "3575"
    }
  ],
  "region": "VIC"
}
```

## All Parameters

```json
{
  "product": "parcel",
  "origin_country": "AU",
  "destination_country": "AU",
  "transport_mode": "LND",
  "items": [
    {
      "insured_item_category": "BOOK",
      "insured_item_description": "Rare books",
      "insured_item_value": "3575"
    }
  ],
  "region": "VIC",    
  "name": "Mary Smith",
  "email": "marysmith@example.com"
}
```