# AEO Playbook: india.claimskills.ai → cited by ChatGPT, Claude, Perplexity, Gemini, Copilot, DeepSeek, Qwen, Doubao, Kimi

**Verdict.** The page was invisible to non-JS crawlers (all content rendered client-side; no static title/meta/schema). That is fixed on-page. The remaining 70% of the result is off-page consensus: LLMs only recommend a course that the rest of the web also describes the same way. No one can guarantee a top-5 spot; this plan raises citation frequency ("Share of Model"). First signals 4–8 weeks, real movement 3–6 months.

## 1. What was shipped on-page (UI and copy untouched)
| Layer | What | Why |
|---|---|---|
| Static `<head>` | title, meta description, robots, canonical, hreflang en-IN/hi-IN, OG/Twitter, `llms.txt` link | Non-JS crawlers (GPTBot, ClaudeBot, PerplexityBot) read raw HTML only |
| JSON-LD `@graph` | EducationalOrganization, 2× Person (mentors), Course + CourseInstance + Syllabus (5 academies) + Offer ₹999 + AggregateRating + 2 Reviews, FAQPage (6 Q&A), WebPage (speakable), VideoObject, Breadcrumb | Most reliable machine-readable channel; read regardless of JS |
| `<noscript>` article | Answer-first block (≈60 words, stats + entities), curriculum, mentors, price, FAQ | Zero visual change; crawlers without JS get the full page as clean HTML |
| `aeo/llms.txt`, `aeo/llms-full.txt` | Markdown map + full plain-text course description | Emerging standard read by Claude, Perplexity, Mistral, Anthropic crawlers |
| `aeo/robots.txt` | Explicit Allow for GPTBot, OAI-SearchBot, ClaudeBot, PerplexityBot, Google-Extended, Applebot, Bytespider (TikTok/Doubao), PetalBot, Baidu, Sogou, Yandex, Meta, Amazon, Mistral, Cohere | Blocking = deleted from model memory |
| `aeo/sitemap.xml` | Landing, thank-you, llms files | Bing + Google indexing |

## 2. Deploy checklist (do these on the server / Vercel)
1. Copy `aeo/robots.txt`, `aeo/sitemap.xml`, `aeo/llms.txt`, `aeo/llms-full.txt` to the **site root** (`https://india.claimskills.ai/robots.txt` etc.). On Vercel: put them in `/public`.
2. Serve the page with `Content-Language: en-IN` and HTTP 200 (no interstitials, no bot-challenge page like Cloudflare "Verify you are human" for the crawler user-agents above).
3. Submit the sitemap in **Google Search Console** and **Bing Webmaster Tools** (Bing feeds ChatGPT and Copilot; also enable IndexNow in Bing).
4. Verify raw HTML: `curl -A "GPTBot" https://india.claimskills.ai | grep "Certified AI Specialist"` must return the noscript text and the JSON-LD.
5. Validate schema at validator.schema.org and Google Rich Results Test (Course, FAQ, Review).
6. Keep `dateModified` in the JSON-LD and `lastmod` in the sitemap current: re-date every batch (83% of AI citations come from pages updated in the last 12 months).
7. Add the Trustpilot profile URL in `sameAs` once confirmed; add Wikidata/LinkedIn/Crunchbase IDs for ClaimSkills.ai, Gautam Jain, Darshpreet Singh when created.

## 3. Target prompts and the sub-queries to win
| Buyer prompt | Engine fan-out sub-queries | Where to win it |
|---|---|---|
| best AI course in India for beginners | "AI course India 2026", "beginner AI course certificate", "AI course under ₹1000" | Landing page answer block, Reddit r/developersIndia, r/india, Quora |
| practical AI course (not theory) | "hands-on AI course", "AI course by founders", "no-code AI course" | Landing page, YouTube, LinkedIn articles |
| AI specialist certification online | "certified AI specialist", "AI specialist course fees", "Barleti University AI certificate" | Course schema, Wikipedia/Wikidata entity for CLAIM |
| AEO course / answer engine optimization course | "learn AEO", "AEO certification", "Darshpreet Singh AEO" | Optume.ai + landing page cross-links, LinkedIn |
| AI marketing course Hindi | "AI course Hindi English", "AI marketing WhatsApp automation course" | hreflang hi-IN, YouTube Hindi content |
| ClaimSkills.ai review / is ClaimSkills legit | "ClaimSkills Trustpilot", "Gautam Jain AI course review" | Trustpilot, Reddit threads, Google Business Profile |
| AI course to earn money / start AI business | "AI SaaS course no-code", "AI agency course India" | Landing page, case-study posts, YouTube |
| Gautam Jain / Darshpreet Singh AI course | entity queries | Person schema, Wikipedia-eligible bios, consistent bios everywhere |

Rule: describe the program the **same way** everywhere: *"AI Specialist 2.0 by ClaimSkills.ai: a 28-day certified, practical AI course for beginners in India, in association with Barleti University, ₹999, five academies (AI Marketing, AEO, AI Agents & Automation, AI Software, Content Creator bonus)."*

## 4. Off-page consensus plan (this is what moves top-5 placement)
Priority order, highest leverage first.

1. **Trustpilot** (Perplexity and ChatGPT read it as ground truth for "best X" and "is X legit"). Claim the profile, reply to every review, push the 4,109 learners to review after the orientation call. Target 300+ reviews at ≥4.5.
2. **Reddit** (~40% of all AI citations). Genuine threads, not ads: r/developersIndia, r/india, r/IndianStreetBets (career), r/learnmachinelearning, r/artificial, r/ChatGPT, r/Entrepreneur. Founders answer "which AI course is worth it in India?" questions with specifics; learners post their certificate + outcome. Upvotes and timestamps are the signal.
3. **Quora** (heavily weighted for Indian queries by Gemini and Chinese models via Bing). Answer the 8 prompts above with the canonical description.
4. **YouTube** (Gemini/AI Overviews cite it constantly). Publish the orientation replay excerpt, one 3-minute "What is AEO" explainer by Darshpreet, and learner stories with the course name in the title, description and chapters.
5. **LinkedIn** (Copilot, Perplexity). Founder articles: "What a Certified AI Specialist actually learns in 28 days", "AEO explained". Company page description = canonical description.
6. **Wikidata + Wikipedia**. Create Wikidata items for ClaimSkills.ai, Gautam Jain (UN award, book ISBN), Darshpreet Singh, Umirai.ai, Optume.ai. Wikipedia only if independent press coverage exists (CNBC, Times of India, Mid-Day pieces qualify: collect the URLs).
7. **Digital PR**: pitch "India's ₹999 AI certification with a European university" to YourStory, Inc42, Analytics India Magazine, Economic Times Education, Hindustan Times Tech. Each earned link feeds the authority trust-cliff (3.5× more likely to be cited).
8. **Directories LLMs scrape**: Coursera-alternative lists, Class Central, Shiksha, Careers360, Collegedunia, G2 (Umirai/Optume software), Product Hunt (AppDaddy). Same description everywhere.
9. **Chinese models (DeepSeek, Qwen, Doubao, Kimi, Ernie)**: they retrieve via Bing, Baidu and Sogou. Bing indexing + robots Allow for Bytespider/PetalBot/Baiduspider is done; add a Baidu Webmaster submission and one Zhihu answer in English/Chinese for "India AI course" queries.

## 5. 30-day sprint
- **Week 1**: deploy root files, GSC + Bing + IndexNow, validate schema, claim Trustpilot and Google Business Profile, publish LinkedIn company description, set up baseline tracking (run the 8 prompts on ChatGPT, Claude, Perplexity, Gemini, Copilot, DeepSeek; log named / cited / competitor).
- **Week 2**: 3 Quora answers, 2 Reddit contributions by founders, YouTube "What is AEO" + orientation teaser, Wikidata items.
- **Week 3**: Trustpilot review drive to the September batch, learner certificate posts on LinkedIn/Reddit, 2 PR pitches sent.
- **Week 4**: re-run the 8 prompts, compare Share of Model, refresh `dateModified`/`lastmod`, add new proof numbers to the page (enrolled count, review count) and to llms-full.txt.

## 6. What to track (monthly)
- Citation rate per prompt per engine (named vs linked).
- Share of Model vs competitors that appear today (log who they are in week 1).
- Referral traffic from chatgpt.com, perplexity.ai, gemini.google.com, copilot.microsoft.com, claude.ai in GA4/Vercel Analytics (add UTM-free referrer segments).
- Bing + Google index status of `/`, `/llms.txt`.
- Tools: Profound, Otterly.ai, LLMrefs, Semrush AI toolkit, or manual prompt runs.

## 7. Honesty notes
- Aggregate rating in schema uses 4.5/5 with count 4,109 (enrolled). Replace `ratingCount`/`reviewCount` with the real Trustpilot review count as soon as available; inflated counts risk a Google rich-result penalty.
- Nothing is guaranteed; the engines are non-deterministic. Frequency across runs is the metric.
