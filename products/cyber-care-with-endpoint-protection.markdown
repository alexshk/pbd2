---
layout: page
title: CyberCare with End Point Protection
permalink: /products/cyber-care-with-endpoint-protection
parent: Products
---

# CyberCare with End Point Protection

Cyberattacks and data breach protection

---

## Parameter Explanations

| Parameter    | Type   | Description |
|:-------------|:-------|:------------|
| `product`    | String | The product slug: "cybercareau" |
| `aggregate_limit`    | String | The identifier for the limit amount selected |
| `business_type`    | String | The identifier of the selected business type, from the list provided in the product info response |
| `revenue_value`    | Integer | The revenue for last year, in dollars |
| `protected_end_points_count`    | Integer | The number of end points to be covered by Cyber Indemnity Solutions. Between 0 and 40. 0 means no protection required. Above 40 requires referral. |
| `region`    | String | The state the business is based in |
| `policy_start_date`    | String | Optional, see [Products page](/products/#common-parameters--optional) for more info |
| `policy_end_date`    | String | Optional, same format as start date. The shortest length for a policy is 8 months, the longest is 18 months. Leave blank to for the default duration of 12 months. |
| `name_of_insured`    | String | The name of the business being covered |
| `name`    | String | The name of the person responsible for the policy |
| `email`    | String | The email address of the person responsible for the policy |

## Minimum Parameters to get a quote

```json
{
  "product": "cybercareau",
  "business_type": "payroll_services_provider",
  "aggregate_limit": "aggregate_limit_1",
  "revenue_value": 1250000,
  "protected_end_points_count": 5,
  "region": "VIC"
}
```

## All Parameters

```json
{
  "product": "cybercareau",
  "business_type": "payroll_services_provider",
  "aggregate_limit": "aggregate_limit_1",
  "revenue_value": 1250000,
  "protected_end_points_count": 5,
  "region": "VIC",
  "name_of_insured": "My Business Pty Ltd",
  "name": "Mary Smith",
  "email": "marysmith@example.com"
}
```