---
layout: page
title: Guides
permalink: /guides/
---
# Powered by Agile

Welcome to the Powered by Agile API

---

## Environments

As well as the production environment, the API has a staging environment. Please speak to us to organise access to the staging environment for testing your integrations. The urls for the environments are:

Staging: [https://api.staging-agileaperture.com](https://api.staging-agileaperture.com)

Production: [https://api.agileaperture.com](https://api.agileaperture.com)


## Quote and Bind

Creating quotes and policies using the API is very simple, but each product has its own rules about which parameters are needed.

### Step 1 -- Product Info

The product info is subject to change, albeit infrequently, so it would be best to either populate any UI elements you build dynamically from the data in the response, or check for changes regularly.

The /v1/products/:product_slug endpoint will provide a list of the parameters that are acceptable to generate a quote. In addition, the product info includes the duty of disclosure (in Markdown format) and the url to download a copy of the Product Disclosure Statement (pds_url)

### Step 2 -- Get a Quote

By sending the parameters required for a specific product, you will get a quote in the response. If you supplied all the parameters for the quote initially, you will be able to go straight to step 4!

### Step 3 (if needed) -- Update a Quote

If the quote is incomplete, you will not be able to bind it. Add the required parameters that weren't supplied when creating the quote by updating the quote

### Step 4 -- Bind the Quote

When you "bind" a quote, you create the policy using all the information provided in the preceding steps. You will need to provide information that either enables Agile to charge for the policy or commit to paying later, depending on your arrangements with Agile.
