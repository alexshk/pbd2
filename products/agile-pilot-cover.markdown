---
layout: page
title: AgilePilotCover
permalink: /products/agile-pilot-cover
parent: Products
---

# AgilePilotCover

This policy pays a Death Benefit in the event of accidental death whilst operating an Australian registered aircraft.

---

## Parameter Explanations

| Parameter    | Type   | Description |
|:-------------|:-------|:------------|
| `product`    | String | The product slug: "agilepilotcover" |
| `plan`    | String | The identifier of the plan that has been chosen, from the list provided in the product info response. See explanation below of the plan identifiers |
| `name_of_insured`    | String | The name of the life to be insured |
| `licence_number`    | String | The licence number of the person being insured |
| `next_of_kin_name`    | String | The name of the person to contact in an emergency |
| `next_of_kin_phone`    | String | The phone number of the person to be contacted |
| `region`    | String | The state the business is based in |
| `name`    | String | The name of the person responsible for the policy |
| `email`    | String | The email address of the person responsible for the policy |

## Minimum Parameters to get a quote

```json
{
  "product": "agilepilotcover",
  "plan": "plus_rw_ag"
}
```

## All Parameters

```json
{
  "product": "agilepilotcover",
  "plan": "plus_rw_ag",
  "name_of_insured": "Mary Smith",
  "licence_number": "ZZ1234",
  "next_of_kin_name": "Susan Smith",
  "next_of_kin_phone": "0400 000000",
  "name": "Mary Smith",
  "email": "marysmith@example.com",
  "region": "VIC"
}
```

## Plan Identifier Explanation

The `identifier` of the plan is a string made up of three components, separated by an underscore. The first part of the identifier is the level of cover, the second is the type of aircraft flown, and the third is the main type of flying activity.

- The level options are `basic`, `plus`, `premium` and `platinum`
- The wing type options are `fw` (Fixed Wing Only) and `rw` (Fixed and Rotor Wing)
- The activity types are `student`, `private`, `commercial`, and `ag` (Agriculture)

Each plan returned in the product info response includes information about the cover, the price, and the activity and wing type. For example, the Plus plan for Fixed Wing Only, Agriculture, would be:

```json
{
  "id": "feb68b1c-94bc-4277-97c0-b7f95ac46808",
  "identifier": "plus_fw_ag",
  "grouping": "plan",
  "label": "Plus",
  "position": 1,
  "data": {
      "usage": "agricultural",
      "benefits": {
          "accidental_death": "$75,000"
      },
      "currency": "AUD",
      "wing_type": "fixed",
      "grand_total": 1395.0,
      "sales_tax_label": "GST",
      "class_of_business": "KG"
  }
}
```