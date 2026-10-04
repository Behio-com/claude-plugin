---
name: shop-ready
description: Get a Behio shop ready to take real orders, payments, shipping and legal pages. Use when the user asks to set up payments, connect Stripe, accept card payments or bank transfer, set up shipping or carriers, generate terms and conditions or privacy policy, or asks "what is still missing before I can sell".
---

# Ready to sell

Explicit instructions from the user take priority. A Behio shop sells only when it has
published products, at least one way to pay, at least one way to deliver and the legal
pages. Work through what is missing and say what remains.

1. `eshop-onboarding-get`: the pending setup steps are your checklist. Repeat it at the end.

## Payments

`eshop-payment-providers-list` shows the providers and their config fields. Every method
needs `currencies` (the shop currency from `eshop-settings-get`).

- Bank transfer (`bank_transfer`): ask for the account number or IBAN and create the method
  with `eshop-payment-method-create`, enabled true. Works immediately.
- Cash on delivery (`cod`) or on pickup (`cash_on_pickup`): no secrets needed.
- Card payments with Stripe: create a method with provider "stripe", empty `config` and
  enabled false, then give the user the link from
  `eshop-payment-method-stripe-connect-url`. They connect their own Stripe account there.
  When they confirm, check `eshop-payment-methods-list` and switch the method on with
  `eshop-payment-method-update` enabled true.
- Any other gateway needs secret keys. NEVER ask for API keys, passwords or secrets in the
  chat. Send the user to
  `https://app.behio.com/{lang}/{org slug}/eshop/{eshopId}/settings/payments`.

## Shipping

Shipping methods and carrier contracts are set up in the Behio admin, not in the chat.
Check `eshop-shipping-methods-list`. When nothing is there, give the direct link
`https://app.behio.com/{lang}/{org slug}/eshop/{eshopId}/settings/shipping` and say: add a
method (personal pickup, own delivery or a carrier such as Zásilkovna, PPL, DPD, GLS, DHL
or UPS), set the price and countries.
The `eshopId` of a site that sells equals its `siteId`.

## Legal pages

`eshop-legal-docs-generate` drafts terms, complaints policy, privacy policy, withdrawal form
and cookie policy for Czech or Slovak law. It needs the `seller` identity (company or
person name, address, company ID, contact e-mail). Ask the user for these facts; never
invent them. Also ask the yes or no questions the tool requires (custom goods, digital
content, perishables, hygiene sealed goods). Track progress with
`eshop-legal-doc-jobs-list`. The drafts stay unpublished until the owner reviews them in
the admin; say so.

## Test

Once the storefront preview works, ask the user to place a test order and confirm it with
`eshop-orders-list` and `eshop-order-get`. Report what is ready, what is missing and where
in the admin the owner finishes it.
