---
name: shop-ready
description: Get a Behio shop ready to take real orders, payments, shipping and legal pages. Use when the user asks to set up payments, connect Stripe, accept card payments or bank transfer, set up shipping or carriers, needs terms and conditions or a privacy policy, or asks "what is still missing before I can sell".
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
  chat. Give the user the link from `site-admin-link` with topic `payments`.

## Shipping

Shipping methods and carrier contracts are set up in the Behio admin, not in the chat.
Check `eshop-shipping-methods-list`. When nothing is there, give the link from
`site-admin-link` with topic `shipping` and the siteId, and say: add a
method (personal pickup, own delivery or a carrier such as Zásilkovna, PPL, DPD, GLS, DHL
or UPS), set the price and countries.
The `eshopId` of a site that sells equals its `siteId`.

## Legal pages

Behio does not write legal texts through Claude and does not vouch for them, so never draft
terms, a privacy policy, a withdrawal form or cookie rules yourself. Give the owner the link
from `site-admin-link` with topic `legal-pages` and the siteId: a shop opens the legal
documents wizard there, where the owner prepares and publishes them. When the owner hands
you a finished text, you may add it as a page (`site-page-create`) and, once they publish
it, link it from the footer menu (`site-menu-item-create`, type PAGE).

## Test

Once the storefront preview works, ask the user to place a test order and confirm it with
`eshop-orders-list` and `eshop-order-get`. Report what is ready, what is missing and where
in the admin the owner finishes it.
