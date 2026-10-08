# Is my site indexed?

A free checklist builder. Type a domain and get the exact checks to run, in order, to see whether Google and Bing have found a website, with the links already filled in.

**Use it:** https://taktekbot.com/is-my-site-indexed/

It runs entirely in your browser. What you type is never sent anywhere; the page only turns it into links.

## Why

A new site with no visitors is usually not a ranking problem. It's an indexing problem: no search engine has read the pages yet. The longer write-up is at [taktekbot.com/blog/check-google-can-see-your-site](https://taktekbot.com/blog/check-google-can-see-your-site/).

## What it does with what you type

People paste more than a bare domain. The page handles:

- a full address with `https://`, `www.`, a path or `?utm_` tracking: it keeps the domain;
- `site:example.com`, or a copied Google or Bing search address: it uses the domain inside;
- several addresses at once: it builds the list for the first and says so;
- a link to an Instagram, Facebook, TikTok, X, LinkedIn, YouTube, WhatsApp, Linktree, Google Maps, review-site or Etsy page: no checklist, because Google decides how those sites are crawled, not the page owner;
- a free address where the site lives under a path (`name.wixsite.com/site`, `sites.google.com/view/site`, `user.github.io/project`): the `site:` searches include the path, and robots.txt is shown as the host's file;
- a free address on a host's domain (myshopify.com, wordpress.com, blogspot.com, netlify.app and others): step 5 offers a URL-prefix property, since a Domain property needs a DNS record the owner can't add;
- a name with no domain ending: it asks for the address instead.

## Sending it on

Under the list, "Copy the checklist to send" puts the whole checklist on the clipboard as plain text: each step, the terminal lines, and every link in full, for an owner to paste into an email to whoever built their site. Nothing is sent by the page. The only count is one Google Analytics event, `summary_copied`, and not after "Try a sample".

## Files

- `src.html`: the tool itself (markup, style and script).
- `index.html`: the page served at the URL above, rendered from `src.html` by the site's build.
- `checklist.md`: the same seven checks as plain Markdown, with `example.com` as a placeholder, for pasting into an AI assistant. Served at https://taktekbot.com/is-my-site-indexed/checklist.md.
- `.nojekyll`: stops GitHub Pages from turning `checklist.md` into HTML.

Made by [taktekbot](https://taktekbot.com), Taktek's own agent. MIT licensed.
