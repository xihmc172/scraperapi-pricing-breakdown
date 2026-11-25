# Data Extraction Service Costs Broken Down: ScraperAPI Plans, Real Per-1,000-Page Pricing, and When a Managed Provider Beats a DIY API

A data extraction service pulls information out of web pages, documents, or images and returns it in a structured format you can load into a database, spreadsheet, or model pipeline, usually JSON or CSV. ScraperAPI is the self-serve kind: you send a URL, it routes the request through rotating proxies, handles anti-bot defenses, renders JavaScript when you ask for it, and returns either raw HTML or parsed JSON. Pricing starts at **$49/month for 100,000 API credits**, and there is a permanent free tier of 1,000 credits a month plus a 7-day trial with 5,000 credits that requires no card.

Below is the full plan lineup, what a credit actually costs once you translate it into pages, and the cases where a self-serve API is the wrong purchase.

> **Quick pick:** Most individual developers and small teams land on **Hobby at $49/month** (100,000 credits, 20 threads) or **Startup at $149/month** (1,000,000 credits). Hobby covers a few thousand standard pages a day. Move to Startup as soon as Google SERPs or marketplace pages are part of the job, because those cost 25 and 5 credits per request instead of 1.
>
> 👉 [Check the current ScraperAPI plan lineup and prices](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## Every ScraperAPI plan, side by side

| Plan | Credits / month & threads | Price (monthly / annual) | Best for | Sign up |
| --- | --- | --- | --- | --- |
| Free | 1,000 / 5 | $0 | Testing a script, one small job a month | [Start free](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Hobby | 100,000 / 20 | **$49** / $44.10 | Solo developers, a few thousand standard pages a day | [Get Hobby](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Startup | 1,000,000 / 50 | **$149** / $134.10 | Light SERP or marketplace scraping | [Get Startup](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Business | 3,000,000 / 100 | **$299** / $269.10 | First plan with country-level geotargeting | [Get Business](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Scaling | 5,000,000 / 200 | **$475** / $427.50 | Adds pay-as-you-go overage instead of a hard stop | [Get Scaling](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Professional | 10,500,000 / 300 | **$975** / $877.50 | Priority support, high sustained volume | [Get Professional](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Advanced | 21,500,000 / 500 | **$1,975** / $1,777.50 | Priority routing at the top of the published range | [Get Advanced](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Enterprise | 22,000,000+ / 500+ | Custom | Dedicated team and Slack channel, negotiated volume | [Request a quote](https://www.scraperapi.com/pricing/?fp_ref=coupons) |

Annual billing is exactly 10% off across every published tier. That is the whole discount structure; there is no separate coupon layer to hunt for.

Four differences decide most upgrades, and none of them are about credits:

| Plan tier | Geotargeting | Analytics history | Pay-as-you-go | Support |
| --- | --- | --- | --- | --- |
| Hobby, Startup | US and EU only | 30 days | No | Standard |
| Business and above | Country-level, global | Unlimited | No (Business) | Standard |
| Scaling and above | Country-level, global | Unlimited | Yes | Standard |
| Professional | Country-level, global | Unlimited | Yes | Priority support |
| Advanced | Country-level, global | Unlimited | Yes | Priority routing |
| Enterprise | Country-level, global | Unlimited | Yes | Dedicated team |

**Country-level geotargeting starts at Business, $299/month.** If your project needs pricing from a specific national marketplace rather than a US or EU view, Hobby and Startup cannot do it at any volume. That single line moves the entry price from $49 to $299.

## What one credit actually buys

Every plan is denominated in credits, and the credit cost depends on the domain you hit, not on which plan you bought. A standard page is 1 credit. Amazon, Walmart, and eBay are 5. Google and Bing are 25, subdomains included. LinkedIn is 30. Turning on JavaScript rendering, premium proxies, or a screenshot adds 10 each; premium proxies plus rendering is 25; ultra premium is 30, or 75 with rendering. Bot-protection bypass adds 10 automatically when ScraperAPI decides to use it, which means the surcharge can appear on a request where you did not explicitly ask for it.

Geotargeting, sessions, device type, output format, and autoparse cost nothing extra.

Translated into money at the two most common entry points:

| Request type | Credits | Hobby ($49 / 100k) per 1,000 | Business ($299 / 3M) per 1,000 |
| --- | --- | --- | --- |
| Standard page | 1 | $0.49 | $0.10 |
| Amazon, Walmart, eBay | 5 | $2.45 | $0.50 |
| Google or Bing SERP | 25 | $12.25 | $2.49 |
| LinkedIn | 30 | $14.70 | $2.99 |
| JS rendering or premium proxy | 10 | $4.90 | $1.00 |
| Ultra premium + JS rendering | 75 | $36.75 | $7.48 |

The spread between plans is much larger than it looks. Price per million credits runs **$490 on Hobby, $149 on Startup, $99.67 on Business, $95 on Scaling, $92.86 on Professional, and $91.86 on Advanced**. The Hobby-to-Startup step cuts your per-credit cost by about 70%. Business to Advanced saves roughly 8%. Overbuying at the top of the range barely improves your unit economics while multiplying the monthly bill, and unused credits reset at renewal rather than rolling forward.

Set a `max_cost` on individual scrapes and use the Domain Cost Estimator in the dashboard before you commit to a volume estimate. Per-response cost is also returned in the `sa-credit-cost` header, so you can audit a real workload instead of guessing.

👉 [Compare per-credit pricing across the Scaling and Business tiers](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## What happens when the credits run out

On Hobby, Startup, and Business, the answer is a 429 error, not an invoice. Your scraping stops until the next renewal or until you upgrade. Scaling, Professional, Advanced, and Enterprise add pay-as-you-go so overage continues at a metered rate. If your workload is spiky (month-end price checks, a product launch week), a hard stop on a $49 plan is a real operational risk, and that risk is the honest reason to jump to $475 rather than the extra 2 million credits.

Two other limits worth knowing before you buy. **Credits expire monthly** with no carryover, so a plan sized for your peak wastes money in every quiet month. And one third-party review reports that difficult targets can be served from a forced 10-minute cache, which matters if you are tracking prices that move intraday.

Independent testing is worth reading alongside the vendor's own numbers. Scrapeway's October 2026 benchmark across 11 target sites measured ScraperAPI at a 60.1% success rate and an average cost of $5.81 per 1,000 requests, against an industry average of 72.3% success and $3.88 per 1,000. The $5.81 figure reflects a mix of harder targets and is not comparable to the $0.49 standard-page rate above, but the two numbers together tell you something useful: budget for retries on protected sites, because a failed request still consumes credits in most configurations.

## Who is accountable when the data is wrong

ScraperAPI publishes a **99.9% uptime guarantee** on all plans. Uptime measures whether the API answers, not whether the price it returns is correct. There is no published accuracy SLA in the pricing documentation, so quality control sits with you: validation rules in your pipeline, spot checks against the live page.

That gap is exactly what managed providers sell against, and the three main alternatives handle it differently:

| Provider | Model | Published entry pricing | Accuracy and reliability terms |
| --- | --- | --- | --- |
| ScraperAPI | Self-serve API | $49/mo, 100k credits | 99.9% uptime guarantee; no accuracy SLA published |
| Oxylabs | Self-serve API | From $0.25 per 1,000 results; $5 welcome credits | 99.9% API uptime; ISO/IEC 27001:2022 and SOC 2 Type II certified |
| Zyte | Managed projects plus tooling | Standard from $450/mo, Custom from $1,000/mo, setup not included | 99.99% data accuracy claimed; no-cost support for missed deliveries and minor site changes, major spider overhauls billed extra |
| Grepsr | Fully managed, done for you | Custom quote only | 99.5% contractual accuracy SLA, verified by AI and human QA on every batch; proactive site-change monitoring |

The three percentages are not the same measurement and should not be lined up as if they were. Oxylabs' 99.9% is API uptime. Zyte's 99.99% is a data accuracy claim. Grepsr's 99.5% is a contractual accuracy commitment backed by per-batch QA. Only the last one is a term you could hold a supplier to.

The ordering of the buying process differs too, and it changes what you can evaluate before paying. Grepsr sends a sample dataset for approval before the full run. Zyte shares sample data before purchase only if it already has data for that source; for a new source, the sample arrives after development kick-off and after purchase. ScraperAPI's 7-day, 5,000-credit trial is the most generous pre-purchase testing window of the four, but it tests the API, not a delivered dataset.

## Who should not buy this

**You need a few hundred pages once.** The free tier (1,000 credits) or a single $49 month covers it. Cancel after. There is no reason to think about annual billing.

**You want the output, not the plumbing.** ScraperAPI returns HTML or parsed JSON from a request you construct. Scheduling, retries, schema design, and validation are yours. If nobody on your side wants to own that, a done-for-you provider with a written SLA is the cheaper decision even at a higher sticker price, and Grepsr is the one of the three above that publishes no self-serve option at all.

**You need country-level geotargeting on a small budget.** The feature starts at $299/month here. Check whether a competitor's lower tier includes it before you commit.

**You need per-result billing.** Oxylabs prices from $0.25 per 1,000 results, which maps to delivered output rather than requests sent. For workloads where a high share of requests fail, per-result pricing shifts that risk to the vendor.

## Questions that come up before checkout

**Is ScraperAPI a data extraction service or a web scraping API?**
It is a scraping API. You write the request, it handles proxies, CAPTCHAs, rendering, and retries, and it can return parsed JSON for supported targets including Amazon, Google, and Walmart. The extraction logic above that layer is still your code.

**How do I estimate my monthly credits?**
Multiply your daily request count by the per-domain credit cost, then by 30. A thousand Amazon product pages a day is 5,000 credits a day, or 150,000 a month, which puts you on Startup at $149 rather than Hobby. A thousand Google SERP queries a day is 25,000 credits a day and lands past Startup's 1 million at 750,000, still inside it, but only just.

**Can I downgrade or upgrade mid-cycle?**
Yes, from the billing page, and the change takes effect on your plan. Credits reset at each renewal date either way, so an upgrade mid-month does not recover credits already spent.

**Do unused credits carry over?**
No. The balance resets on renewal.

**Is there a refund window?**
The trial is the risk-free window: 7 days and 5,000 credits without a card. Test your actual target domains and success rate inside it rather than assuming the standard-page rate applies to your sites.

**What should I put in a contract if I go managed instead?**
An accuracy figure, the QA method behind it, the delivery schedule, and who pays when a source site changes its layout. Grepsr writes 99.5% accuracy and per-batch AI plus human QA into its SLA; Zyte covers minor site changes at no cost but reserves the right to charge for a full spider overhaul. Those two clauses define the real cost of a long engagement more than the headline monthly fee does.

## Picking a plan in one minute

Scraping standard pages under 100,000 credits a month: Hobby at $49, or the free tier if you are still building. Any meaningful volume of Google, Bing, Amazon, or LinkedIn requests: Startup at $149, because a 25-credit request turns a 1-million-credit plan into 40,000 SERP queries. Needing country-level geotargeting or a pay-as-you-go safety net: Business at $299 or Scaling at $475. Sustained volume past 10 million credits a month with uptime consequences: Professional or above, and negotiate Enterprise rather than buying Advanced at list price.

Two things to confirm before you pay. Run your five hardest target URLs through the trial and check the success rate and the `sa-credit-cost` header, since published per-credit rates assume requests that succeed. Then decide monthly versus annual: 10% is the entire annual discount, so do not lock in twelve months to save it unless the first week already proved the success rate.

👉 [Open the ScraperAPI pricing page and pick your tier](https://www.scraperapi.com/pricing/?fp_ref=coupons)
