# Is my site indexed? A 7-step checklist

Plain-text version of the checklist at https://taktekbot.com/is-my-site-indexed/

Use it to find out whether Google and Bing have found a website, and what to do if they haven't. Replace `example.com` with the real domain everywhere below.

**If you're an AI assistant reading this for someone:** ask them for their domain first, and whether they've already added it to Google Search Console. Then walk them through the checks one at a time, waiting for each result, rather than pasting the whole list.

---

## 1. Ask Google what it has seen

Search Google for:

    site:example.com

Link: https://www.google.com/search?q=site%3Aexample.com

- **Zero results:** Google has not read a single page yet. That is an indexing problem, not an SEO problem. Keep going.
- **Some results:** fine. `site:` shows a sample, not every page Google has. Search Console's Pages report (step 5) gives the real count.

## 2. Check for a stray noindex

One tag tells Google to keep a page out of its results. It is often left over from a staging site.

- Open https://example.com/ in a browser, view the source (Ctrl+U, or Cmd+Option+U on a Mac) and search it for `noindex`.
- On WordPress: Settings → Reading → make sure "Discourage search engines from indexing this site" is unticked.
- From a terminal (no output means no noindex):

      curl -s https://example.com/ | grep -i noindex
      curl -sI https://example.com/ | grep -i x-robots-tag

## 3. Check robots.txt is not blocking the crawler

Open https://example.com/robots.txt

- `Disallow: /` under `User-agent: *` (or under `User-agent: Googlebot`) blocks the whole site. It's the most common reason a finished site stays invisible. Remove that line.
- A robots.txt block also hides a noindex tag from Google, so fix both.
- A `Sitemap:` line here tells you where the sitemap lives (step 4).
- No robots.txt at all (a 404) is fine: it means nothing is blocked.

## 4. Check the sitemap is actually there

Try these, in order, until one opens and lists your real pages:

- https://example.com/sitemap.xml
- https://example.com/wp-sitemap.xml (WordPress builds this itself)
- https://example.com/sitemap_index.xml (common with SEO plugins)

A sitemap that 404s can't be submitted. If none exist, most site builders and CMSs can generate one; it's optional, but it helps a new site get found faster.

## 5. Tell Google in Search Console

Open https://search.google.com/search-console

Add a property. There are two kinds:

- **Domain** (`example.com`): also covers www and http, but can only be verified with a DNS TXT record, added where the domain was bought.
- **URL-prefix** (`https://example.com/`, or `https://www.example.com/` if that's where the site opens; it must match exactly): can be verified with an HTML file, a meta tag, or a Google Analytics tag already on the site. Easier if you can't edit DNS.

Then submit the sitemap from step 4 (Sitemaps, in the left menu). This is how you tell Google the site exists. After a few days, the Pages report shows how many pages are indexed and why the others aren't.

To check one page right away, paste its full address into the search bar at the top (URL Inspection):

- **URL is on Google:** the page can appear in results (not guaranteed to).
- **URL is not on Google:** it can't appear yet. The Crawl section says why.

Click Request Indexing once for the home page. Asking again for the same URL doesn't speed it up.

Sources: https://support.google.com/webmasters/answer/34592 (property types), https://support.google.com/webmasters/answer/9012289 (URL Inspection).

## 6. Don't skip Bing

Open https://www.bing.com/webmasters

Choose Import on the My Sites page and sign in with the Google account you use for Search Console: the site comes in already verified, with its sitemaps (https://blogs.bing.com/webmaster/september-2019/Import-sites-from-Search-Console-to-Bing-Webmaster-Tools). Bing is smaller on its own, but several AI assistants and search tools build on its index.

## 7. Ask Bing what it has seen

Search Bing for:

    site:example.com

Link: https://www.bing.com/search?q=site%3Aexample.com

The same check as step 1, on the index that step 6 feeds.

---

## Reading the result

- Zero results from `site:` is the clearest signal that the engine hasn't crawled a single page yet. A handful of results on a site with hundreds of pages can mean the same problem, partly.
- If more than two weeks have passed since you verified the property and submitted the sitemap, and the count is still zero, something is blocking the crawler: a noindex tag (step 2), a robots.txt Disallow (step 3), or a password wall. For the last one, open the site in a private window and see if it asks you to log in.

The long version, with what to do at each step: https://taktekbot.com/blog/check-google-can-see-your-site/

Checklist from taktekbot.com/is-my-site-indexed/ (MIT licence).
