---
name: go-live
description: Put a Behio website or shop live (on its free behio.app address or the user's own domain) and publish changes. Use when the user wants the site on the internet, on their own domain, asks how to connect a domain, wants to publish, or asks why the live site differs from the preview.
---

# Going live

Explicit instructions from the user take priority. Publishing changes what customers see:
do it only on the user's explicit request.

1. `site-get` shows the preview URL, the live URL and the latest builds.
2. `site-publish` puts the site live, on every plan including Free. The first publish
   creates the live site at `https://<web>.behio.app` (public and indexable, ready in 3 to
   5 minutes) and returns `liveUrl`; give the user that address. Later publishes move the
   current draft live. Until the first publish the site runs only on its preview address,
   which is public but hidden from search engines.
3. A custom domain is optional and needs a paid plan: `site-domain-connect`. Behio does not
   sell domains; a user without one buys it at any domain registrar first. Recommend
   `dnsChoice` "ours" (Behio hosts the DNS, the user only changes nameservers at the
   registrar). Give the user the exact instructions the tool returns, then check progress
   with `site-domain-status`. DNS changes can take minutes to hours. The custom domain then
   becomes the main address and `<web>.behio.app` keeps working.
4. `site-get` shows `liveBuild`; never say the site is live before it reports finished.
5. When the live site does not update, read `site-logs` for the live target.
