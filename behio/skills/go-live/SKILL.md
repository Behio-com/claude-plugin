---
name: go-live
description: Put a Behio website or shop live on the user's own domain and publish changes. Use when the user wants the site on the internet, on their own domain, asks how to connect a domain, wants to publish, or asks why the live site differs from the preview.
---

# Going live

Explicit instructions from the user take priority. Publishing changes what customers see:
do it only on the user's explicit request.

1. `site-get` shows the preview URL, the live URL and the latest builds.
2. A site goes live by connecting a domain the user owns: `site-domain-connect`. Behio does
   not sell domains; a user without one buys it at any domain registrar first. Recommend
   `dnsChoice` "ours" (Behio hosts the DNS, the user only changes nameservers at the
   registrar). Give the user the exact instructions the tool returns, then check progress
   with `site-domain-status`. DNS changes can take minutes to hours.
3. Until then the site runs on its preview address, which is public but hidden from search
   engines.
4. Once the site has a live deployment, `site-publish` moves the current draft live.
5. When the live site does not update, read `site-logs` for the live target.
