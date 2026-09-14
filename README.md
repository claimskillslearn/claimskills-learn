# india.claimskills.ai – deploy package

Static site. No build step. Upload this folder as-is.

## Cloudflare Pages
1. Cloudflare dashboard → Workers & Pages → Create → Pages → Upload assets (or connect the GitHub repo).
2. Upload the contents of this folder (index.html at the root).
3. Custom domains → add india.claimskills.ai → Cloudflare creates the CNAME automatically if the DNS is on Cloudflare.
4. _headers and _redirects are picked up automatically.
5. Security → Bots: make sure "Block AI bots" / "AI Scrapers and Crawlers" is OFF, otherwise ChatGPT, Claude and Perplexity cannot read the page.

## GitHub (+ Vercel or Cloudflare Pages via Git)
1. Create a repo, push this folder's contents to the root (index.html at repo root).
2. Vercel → New project → import repo → framework "Other", no build command, output directory "." → deploy. vercel.json handles clean URLs and headers.
   Cloudflare Pages via Git: build command empty, output directory "/".

## After deploy (10 minutes)
- Open https://india.claimskills.ai/robots.txt, /sitemap.xml, /llms.txt and confirm they load.
- Google Search Console + Bing Webmaster Tools: add the property, submit /sitemap.xml.
- Rich Results Test: https://search.google.com/test/rich-results?url=https://india.claimskills.ai
- Make a ₹1 test payment (Razorpay key rzp_live_T75kc2OCVrabhb, auto-capture must be enabled) and confirm the redirect to /thankyoupage.

## Files
- index.html – landing page as real static HTML (~135 KB). All copy, headings, FAQ and JSON-LD are in the raw HTML so non-JS AI crawlers (GPTBot, ClaudeBot, PerplexityBot) read the full page. support.js + React (unpkg) add interactivity; Razorpay, Wistia and Vimeo load lazily from their CDNs.
- support.js – page runtime. Upload it next to index.html.
- assets/ – all page images (lazy-loaded, cached 1 year)
- thankyoupage/index.html – post-payment page (noindex)
- robots.txt, sitemap.xml, llms.txt, llms-full.txt – AI/search crawler files
- _headers, _redirects – Cloudflare Pages config
- vercel.json – Vercel config (ignored by Cloudflare)

Full AEO plan: see AEO-PLAYBOOK.md in the project.
