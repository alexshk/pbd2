---
layout: page
title: /v1/quotes/:id/bind
permalink: /api/v1/quotes-id-bind
parent: API Reference
---

# POST /v1/quotes/:id/bind

This creates a policy from the quote, using the payment method you provide.

When a quote is completed, this endpoint is used to "bind" it, creating a policy using the information that has been supplied.

## Path params
\
`quote_id`{: .fs-5 } -- string, required param

The UUID of the quote being bound

## Body params
\
`RAW_BODY`{: .fs-5 } -- object

The parameters required to bind the quote

`read_and_understood`{: .fs-4 } -- boolean

Stipulates that the buyer has read and understood the relevant policy documents

`payment`{: .fs-4 } -- object

How will the policy be paid for?

`method`{: .fs-4 } -- string

The payment method being used to bind the policy. Either `stripe` or `deferred`. Availability of the deferred payment type depends on you agreement with Agile.

`token`{: .fs-4 } -- string

Token for the payment, if applicable

## Example Stripe payment

```json
{
  "read_and_agreed": true,
  "payment": {
    "method": "stripe",
    "token": "tok_123123123"
  }
}
```

## Example Deferred payment (if available)

```json
{
  "read_and_agreed": true,
  "payment": {
    "method": "deferred"
  }
}
```


## Response examples
\
`200 OK`{: .fs-5 }

```json
{
  "id": "3918b399-74b5-4f1b-9f1d-10412679c76a",
  "policy_number": "SAMPLE_W02B0003000E",
  "status": "active",
  "read_and_agreed": true,
  "created_at": "2019-05-23T01:32:44.257Z",
  "updated_at": "2019-05-23T01:32:44.257Z",
  "start_at": "2019-05-23T01:32:44.158Z",
  "end_at": "2020-05-23T01:32:44.160Z",
  "customer": {
    "id": "1fd10c81-73dc-444b-948a-03f53f11aaf6",
    "name": "Mary Smith",
    "email": "mary@example.com",
    "phone": null,
    "created_at": "2019-04-30T04:49:49.949Z",
    "updated_at": "2019-04-30T04:49:49.949Z"
  },
  "quote": {
    "id": "751831b7-079f-4b1b-9ac2-0fa5c1b7442s",
    "customer_id": "1fd10c81-73dc-444b-948a-03f53f11aaf6",
    "premium": 1500,
    "premium_sales_tax": 150,
    "stamp_duty": 82.5,
    "admin_fee": 152.27,
    "admin_fee_sales_tax": 15.23,
    "total_sales_tax": 165.23,
    "grand_total": 1900,
    "currency": "AUD",
    "sales_tax_label": "GST",
    "excess": 1000,
    "custom_field": null,
    "expires_at": "2019-06-22T23:59:59.999Z",
    "created_at": "2019-05-23T01:18:40.981Z",
    "updated_at": "2019-05-23T01:32:44.119Z",
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
      "region": "NSW",
      "business_type": "Accountant",
      "revenue": 135000,
      "name_of_insured": "Mary Smith Accounting Pty Ltd",
      "name": "Mary Smith ",
      "email": "mary@example.com",
      "plan_label": "Premium",
      "region_label": "New South Wales"
    }
  }
}
```
\
\
`422 Unprocessable Entity`{: .fs-5 }
```json
{
  "errors": {
    "read_and_agreed": [
      "must be accepted"
    ]
  }
}
```
