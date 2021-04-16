---
layout: page
title: Products
permalink: /products
has_children: true
has_toc: true
---

# Products

Each product has it's own requirements

---

See each product page for requirements specific to that product. Each one has its own fields that are required to create the quote, and others to bind the quote.

## Common Parameters -- Required

The following parameters are applicable to all products, and are not required to get a quote, but they are required before the quote can be bound:

`name`{: .fs-5 }

This is generally the name of the person getting the quote. For an individual, it is most likely the policy holder, although in some cases it may be the person buying the policy for someone else. If that is the case, the `name_of_insured` parameter must name the other party.

This name will be used to create a user account so this person can log in to their Agile portal and view and manage their policy.

`email`{: .fs-5 }

The email address of the person named above. This will be the address the policy documents will be sent to, and this address will act as the log in to the Agile portal

`name_of_insured`{: .fs-5 }

This is required for some products (where the policy is for a business, for example) and optional for others. See the description for the name parameter to see where you might want to provide this parameter when it is optional

## Common Parameters -- Optional

In addition to the required fields, you may optionally provide the following:

`no_customer_contact`{: .fs-5 }

Ordinarily, once a policy is bound, the policy holder will receive an email with information about the policy and how to access their Agile account. Some partners prefer to handle all contact with the policy holder themselves. If you pass `no_customer_contact: true` with the quote parameters (either on create or update), then no email will be sent. Additional, Agile's internal systems clearly mark the policy as Do Not Contact.

`policy_start_date`{: .fs-5 }

If this parameter is not provided, cover on the policy starts from the day it is bound. If you need the policy cover to start at a different date you may provide a value. The format is `'YYYY-MM-DD'`. If you provide a date in the past, the request will fail validation. Additionally, there is a limit to how far in advance the start date may be set. Unless otherwise stated on specific products, the limit is 30 days in the future.

`custom_field`{: .fs-5 }

This is a string parameter that can be used for anything you choose. We do not validate or use the values supplied in this parameter, but it may be helpful for you to supply to help with your own reporting, or for identifying your own customers.