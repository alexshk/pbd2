---
layout: page
title: CyberCare
permalink: /products/cyber-care
parent: Products
---

# CyberCare

Cyberattacks and data breach protection

---

## Parameter Explanations

| Parameter    | Type   | Description |
|:-------------|:-------|:------------|
| `product`    | String | The product slug: "cybercare" |
| `plan`    | String | The identifier of the plan that has been chosen, from the list provided in the product info response |
| `name_of_insured`    | String | The name of the business being covered |
| `business_type`    | String | The identifier of the selected business type, from the list provided in the product info response |
| `revenue`    | Number | The revenue for last year, in dollars |
| `region`    | String | The state the business is based in |
| `name`    | String | The name of the person responsible for the policy |
| `email`    | String | The email address of the person responsible for the policy |

## Minimum Parameters to get a quote

```json
{
  "product": "cybercare",
  "plan": "premium_0"
}
```

## All Parameters

```json
{
  "product": "cybercare",
  "plan": "premium_0",
  "name_of_insured": "My Business Pty Ltd",
  "name": "Mary Smith",
  "email": "marysmith@example.com",
  "business_type": "consultant",
  "revenue": "130000",
  "region": "VIC"
}
```