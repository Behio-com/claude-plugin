# Behio for Claude

Launch a complete online shop or website on [Behio](https://behio.com) straight from
Claude: products with photos and texts, payments, legal pages, a storefront with an
instant preview, hosting and your own domain. Claude guides you step by step and does the
work through the Behio tools; a first working shop typically takes 30 to 60 minutes.

## Install (Claude Code, Claude desktop app)

```
/plugin marketplace add Behio-com/claude-plugin
/plugin install behio@behio
```

Then run `/mcp`, pick `behio` and sign in to Behio (a Behio account is needed; new users can
create their organization right in the chat).

## Use

- `/behio:new-shop handmade candles` starts the guided shop launch.
- `/behio:shop-status` shows what is done and what is still missing.
- Or just ask: "I want to sell my candles online", "add these products", "make the
  storefront look like my brand", "how do I put the shop on my domain".

## What is inside

| Skill | What it does |
|---|---|
| launch-eshop | Guided launch: plan with you first, then shop, catalog, storefront, payments, legal pages, test order, domain |
| shop-products | Products from a list, spreadsheet or website: texts in every language, photos, prices, categories, variants, parameters |
| shop-website | Storefront or website code with instant preview and screenshots |
| shop-ready | Payments (bank transfer, Stripe link), shipping and legal pages in the admin with exact links |
| go-live | Own domain and publishing |
| site-content | Forms into the CRM, blog, editable data collections, visitor stats |
| site-analytics | Evaluate visitors with numbers: trends, sources, pages, leaving, devices, funnels, forms, and what to change |

The plugin connects to `https://be.behio.com/mcp-code` (OAuth). Every change is visible in
the Behio admin, where it can be undone. Nothing is published to a live domain without
your explicit request, and no passwords or API keys ever pass through the chat.

## Develop

```
claude plugin validate ./behio
claude plugin eval ./behio --runs 1 --no-publish
```
