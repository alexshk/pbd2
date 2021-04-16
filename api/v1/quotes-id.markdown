---
layout: page
title: /v1/quotes/:id
permalink: /api/v1/quotes-id/
parent: API Reference
---

# PATCH /v1/quotes/:id

If needed, the quote can be updated with changed or extra parameter. Each product has a minimum set of parameters requited to create a quote, but the may be extra parameters needed to bind the quote. If you didn't provide all the parameters when creating the quote, you can provide them with this endpoint.

Once a quote has been created, the parameters can be modified. This may be required if the quote that was created has missing required fields.

## Path params
\
`quote_id`{: .fs-5 } -- string, required param

The UUID of the quote to be updated

## Body params
\
`RAW_BODY`{: .fs-5 } -- object

The data that is needed to get a quote. The requirements vary per product, see the reference guide for specific product instructions and information

`product`{: .fs-4 } -- string

The product for which the quote is being created

`plan`{: .fs-4 } -- string

The identifier for the required plan. The available plans are listed in the product info endpoint response

`name_of_insured`{: .fs-4 } -- string

The name of the business that is being insured

`business_type`{: .fs-4 } -- string

The type of business being insured. Please see list in the Cybercare documentation

`revenue`{: .fs-4 } -- float

The business revenue for last year

`region`{: .fs-4 } -- string

The State where the business is based

`name`{: .fs-4 } -- string

The name of the person responsible for getting the quote

`email`{: .fs-4 } -- string

The email address of the person getting the quote

There are certain parameters that are required to calculate the price, and these are all that is required to generate the quote. However, the quote cannot be bound until all parameters are supplied. If you don't provide all the parameters when you create the quote, then you can use the update quote endpoint. The response will let you know which parameters are still required with an array of keys in the missing_required_fields attribute on the response (see example above).

See the guide for details about which parameters are required for each product.

## Example quote request body

```json
{
  "product": "cybercare",
  "plan": "premium_1",
  "name_of_insured": "Mary Smith Accounting Pty Ltd",
  "business_type": "Architect",
  "revenue": 135000,
  "region": "NSW",
  "name": "Mary Smith ",
  "email": "mary@example.com"
}
```

## Response examples
\
`200 OK`{: .fs-5 }

```json
{
  "id": "751831b7-079f-4b1b-9ac2-0fa5c1b7442s",
  "customer_id": null,
  "premium": 1500.0,
  "premium_sales_tax": 150.0,
  "stamp_duty": 165.0,
  "admin_fee": 77.27,
  "admin_fee_sales_tax": 7.73,
  "total_sales_tax": 157.73,
  "grand_total": 1900.0,
  "currency": "AUD",
  "sales_tax_label": "GST",
  "excess": 1000.0,
  "custom_field": null,
  "expires_at": "2019-06-22T23:59:59.999Z",
  "created_at": "2019-05-23T01:08:54.907Z",
  "updated_at": "2019-05-23T01:08:54.907Z",
  "benefits": [
    {
      "title": "List of benefits",
      "description": "Explanation of each benefit..."
    }
  ],
  "product": {
    "name": "CyberCare",
    "pds_url": "http://aperture.pdev/products/cybercare/Agile-CyberCare-PDS.pdf",
    "min_insured_value": 250000,
    "max_insured_value": 10000000,
    "duty_of_disclosure": "# Duty of Disclosure\n## What You must tell Us\nWe will ask You various questions when You apply for cover. When You answer those questions, You must be honest and You have a duty under law to tell Us anything known to You, and which a reasonable person in the circumstances, would include in answer to the question. We will use the answers in deciding whether to insure You, and anyone else to be insured under the Policy, and on what terms. You have this same duty to disclose those matters to Us before You renew, extend, vary or reinstate Your Policy.\n## If You do not tell us\nIf You do not answer Our questions in this way, We may reduce Our liability under contract in respect of a claim or refuse to pay a claim, or cancel the Policy. If You answer Our questions fraudulently, We may refuse to pay a claim and treat the Policy as never having commenced."
  },
  "parameters": {
    "plan": "premium_1",
    "region": "VIC",
    "business_type": "Architect",
    "revenue": 135000.0,
    "name_of_insured": "Mary Smith Accounting Pty Ltd",
    "name": "Mary Smith ",
    "email": "mary@example.com",
    "plan_label": "Premium",
    "region_label": "Victoria"
  }
}
```
\
\
`422 Unprocessable Entity`{: .fs-5 }
```json
{
  "errors": {
    "plan": [
      "can't be blank"
    ]
  }
}
```