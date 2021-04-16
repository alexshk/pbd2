---
layout: page
title: API Reference
permalink: /api/
has_children: true
has_toc: false
---
# Quote and Policy generation

Generating quotes and policies with the Powered by Agile API

---

## Overview

The AgileAPI allows 3rd parties to generate quotes and policies for insurance products. To generate a quote and subsequently accept the quote to create a policy there are [4 endpoints](/api/#endpoints).

## Authentication

All requests are associated with a specific "partner" and permissions are based on the settings that Agile have made for that partner. Client access tokens should be provided in the Authorization header as Bearer tokens.

Example request with bearer token:

```shell
curl --request GET \
  --url https://api.staging-agileaperture.com/v1/products/cargo \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJhZmZpbGiMDE4Y...RoqFdnaforvXxO9O3NrgmZE'
```

## Responses

All responses are JSON encoded.

Timestamps are in UTC and formatted as ISO8601.

## Errors

All 400 series errors (400, 401, 403, etc) will be returned with an optional JSON object in the body and a application/json content type.

## HTTP Status Codes

We use HTTP status codes to indicate success or failure of a request.

### Success codes:

- `200 OK` -- Request succeeded. Response included
- `201 Created` -- Resource created. URL to new resource in Location header
- `204 No Content` -- Request succeeded, but no response body

### Error codes:

- `400 Bad Request` -- Could not parse request
- `401 Unauthorized` -- No authentication credentials provided or authentication failed
- `403 Forbidden` -- Authenticated user does not have access
- `404 Not Found` -- Resource not found
- `415 Unsupported Media Type` -- POST/PUT/PATCH request occurred without a application/json content type
- `422 Unprocessable Entry` -- A request to modify or create a resource failed due to a validation error
- `500, 501, 502, 503, etc` -- An internal server error occured

## Validation Errors

In case of validation errors on a POST/PUT/PATCH request, a `422 Unprocessable Entry` status code will be returned. The JSON response body will include an array of error messages.

## Endpoints

## [GET /v1/products/:product_slug](/api/v1/products-product-slug)

This endpoint will return data that can be used to construct a form for requesting a quote. This includes information about the product in general, and rates and loadings that are required to generate a valid quotation.

## [POST /v1/quotes](/api/v1/quotes)

The quotes endpoint accepts a set of parameters for a product, and returns data details for the cost of insuring the item/s along with other pertinent information. This includes the quote id that can the be used to generate a policy.

## [PATCH /v1/quotes/:id](/api/v1/quotes-id)

If needed, the quote can be updated with changed or extra parameter. Each product has a minimum set of parameters requited to create a quote, but the may be extra parameters needed to bind the quote. If you didn't provide all the parameters when creating the quote, you can provide them with this endpoint.

## [POST /v1/quotes/:id/bind](/api/v1/quotes-id-bind)

This creates a policy from the quote, using the payment method you provide.