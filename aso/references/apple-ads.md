# Apple Ads

Apple Ads (Apple Search Ads until April 15, 2025) buys the search demand that organic ASO also captures. Run a large exact-match long-tail campaign with Search Match off, bids raised per keyword until impressions appear, a custom product page per intent, and every paid install pushed to a rating, because spend never moves organic rank on its own. Apple documents the mechanics; its advice on Search Match, brand and competitor campaigns, country grouping and bid steps runs against tested practice and is marked (contested). Every budget, bid and placement number is 2025-2026 from a handful of campaigns, dated because two top results have been paid since March 2026; "popularity" is the 5 to 100 score keyword tools report (log scale, same for paid and organic), not the console's 1 to 5 Search Popularity scale.

## Placements and the auction

- Use the search results placement in Advanced mode. Each campaign runs in one of four placements, Today tab, Search tab, search results or product pages, in 91 countries and regions; only search results supports keywords, Maximize Conversions, bid recommendations and custom product page ads (Apple-documented). The Today tab converts poorly (observed); Apple pitches it for awareness.
- Never use Basic: it charges per install, picks keywords and bids, gives no keyword data or audience settings, and caps spend at $10,000 per app per month (Apple-documented).
- Impressions are free and you pay per tap, never above your max CPT (Apple-documented): an irrelevant keyword costs money, an untapped one nothing.
- Relevance gates delivery (Apple-documented): an irrelevant app never enters the auction at any bid, judged from its title, descriptions and keywords in App Store Connect. A brand-only name leaves budget unspent, and a keyword absent from your metadata pays more than relevant apps pay (observed). Fix metadata first (`references/metadata-writing.md`); a change reaches the live ad within two hours (Apple-documented).
- Apple rotates apps within a keyword, so a low bid still earns a few impressions, too few to convert (observed). Volume comes from popularity, not from the bid.
- Second placement: announced January 2026, live in early March 2026; by September 2026 the paid slots read as positions one and three (observed), organic visibility means top three, and cost per tap is up everywhere. You cannot choose or bid for a position (Apple-documented).
- Slot three is not a cheaper slot one (observed): users read the first ad, the first organic result, then the second ad, so slot three gets browsers at a cost per tap usually lower, sometimes identical. The number one ad on a smaller keyword beats number three on a bigger one; slot three works only with long tail plus a custom product page. Steer by Impression Share (First Ad Position), which Apple reports apart from all-position share.

## Budget

- Decide budget, then bid, then keywords, plus the bid strategy: Manage Bids (manual) or Maximize Conversions (automated). Start with what you are willing to waste: the first weeks buy your conversion rate.
- The daily budget is a monthly average (Apple-documented): one day can overspend, a month never exceeds 30.4 times it ($100 a day caps at $3,040), and an end date caps total spend at days times budget. Lifetime budgets ended in June 2026; for a fixed test total, set an end date. Every bid must be lower than the daily budget.
- Starting levels (rules of thumb): under $10 a day gets nothing; $10 a day for 3 to 5 days is the smallest learning unit; $20 or less is fine; $30 to $40 is the common start. Apple sets no minimum.
- Ceiling per tap is break-even: what a user pays you times tap-to-paying conversion; a launch week above it is acceptable. Compute within a week ($300 a month, 16 downloads, one subscription is $300 per subscriber). First-payment break-even is the green light: if 4 to 10 keywords work at $30 a day, double to $60 on those only. Apple's starting-bid formula prices the download ($2.50 value times 40% tap-to-download is a $1.00 bid); price the paying user instead.
- Before you have data (dated: 2020), use competitors' estimated revenue per download as the cost-per-acquisition ceiling ($1.50 to $7.50, about $5 aggregate, for word games); it misleads for subscriptions.
- Budget more than 1,000 downloads for 1,000 real users.
- Stop rule: 100 taps at $2 for one $10-a-year subscription cannot scale. Fix onboarding and paywall, then cut keywords, never the channel. Do not advertise an app that is free or under repair.
- Check daily or every other day; only about $100 a month needs no watching. Nobody at Apple will suggest pausing a $5,000 a month campaign that returns nothing.
- One campaign per country, never mixed (contested: Apple recommends grouping markets that share goals or language); Apple's mechanics favor the split, since keywords apply to every country in a campaign and location refinement needs a single-country campaign (Apple-documented). US bids run far higher, some countries a tenth. Expand to your top five download countries; against a category owner, start in Australia, Canada or the UK (procedure 5). Brazil and some other countries require localized metadata and screenshots before a campaign runs (Apple-documented).
- Scope competitor paid data by device: iPhone and iPad keyword sets differ; iPad was cheaper for some apps in 2025 (observed).

## Campaign structure and match types

- Create campaigns paused or scheduled, because one starts as soon as a payment method is added, and pause rather than remove, because a removed campaign or ad group cannot be restored (Apple-documented).
- Search Match is on by default in every Manage Bids ad group (Apple-documented). Switch it off on every campaign (January 2025 through September 2026) (contested: Apple recommends a Search Match discovery ad group whose winners you promote to exact). Competitors' paid keywords give the same discovery free; impressions tank afterward, revenue and conversion rate should not.
- Broad is the default match type and reaches related terms, other languages and similar product names (Apple-documented), buying competitor-brand traffic unasked ("app analytics" became Instagram analytics). Use exact match in square brackets (2021 through 2026) (contested: Apple suggests broad beside exact for coverage).
- Exact match includes close variants: misspellings, word rearrangements and translations (Apple-documented). Listing every variant yourself is redundant but harmless; read the search-term report for what each keyword matched.
- Match type is fixed once saved; pause and re-add to change it. Brackets set exact when typing; the CSV upload has a Match Type column, up to 5,000 rows (Apple-documented). A plain bulk paste carried no match type in August 2026 (observed).
- Negatives (contested, changed over time): January 2025, as many as possible, broad for unwanted themes; June 2026, exact only, none in an all-exact campaign. Follow 2026. Apple-documented: an exact negative blocks only that term, not longer queries ("kids puzzles" still allows "kids puzzles apps"); a broad negative blocks any query with all its words. In an all-exact campaign, add a leaking close variant as an exact negative.
- Two tiers: a master group of proven keywords at higher bids and an experimental group of long-tail terms, easily 1,000, at low bids; promote what converts. Mature accounts experiment in separate campaigns. An ad group holds 5,000 keywords (Apple-documented). Never put one keyword in two campaigns.
- Run only a Category campaign, the large exact long-tail one (contested: Apple recommends Brand, Category, Competitor and Discovery campaigns).
- Customer type: "New users" for efficient spend (it still records some redownloads), "All users" (default) only for awareness, "Returning users" installs report as redownloads, "Users of my other apps" needs the Apple Account tied to App Store Connect (Apple-documented).
- Audience refinement (Apple-documented): any specified audience needs more than 5,000 customers or sits on hold, and the 78% of iOS 17+ search volume with Personalized Ads off never sees it, in any placement. Age or gender also disables custom product page deep links and AdServices attribution. Set no age or gender refinement; the 2020 to January 2025 rule to narrow first loses to these mechanics.
- No OS-version or device-age targeting exists; iPhone and iPad can be split per ad group (Apple-documented).

## Choosing and pruning keywords

Apply `references/keyword-research.md` to ads data; competitor sourcing is in `references/competitor-research.md`.

- Skip the head term: a calendar app bids on "business calendar" or "calendar for Outlook", not "calendar", where 2026 bidders are burst-spending AI newcomers; general terms need higher bids (Apple-documented). The exception is seasonal terms (dated: 2024; procedure 3).
- Long tail means two- or three-word phrases; stacked, they match a head term at far lower cost. Metadata holds 5 to 10 of them, a campaign 5,000, and the failures never spend.
- Size (rules of thumb, observed): 300 to 1,000 keywords; impressions kick in around 300; a lucrative niche wants 1,500 to 2,000. Most never spend: 16 to 18 of about 180 did in one account.
- Seed from competitors' paid keywords (a bidder present for months runs a strategy, a new one a test), their organic keywords, the apps your users also use, your own organic ranks from below 10 to about 70 or 80, and Apple's keyword recommendations (seven-day estimates, missing while activity is low). Harvest monthly (procedure 2).
- Competitor set: whoever bids on your keywords, starting from 2 to 3 direct competitors (dated: 2024). The 2026 filter: the popularity 5 to 10 terms of the 5 to 10 most similar competitors, 500 to 1,000 of them; the March 2025 band of 13 to 50 or 60 is superseded.
- Competitor paid data is a daily store scan of ads seen, not Apple data; a 65-keyword campaign can show as one, so "too few keywords" is an inference.
- Read impression share first: skip keywords where one app holds the majority (52% on "diet planner" at popularity 8) or three hold about 85%; enter where five or more split it, or nobody advertises. Per competitor, a large gap means avoid, a small one means raise the bid (dated: 2024, procedure 6). These are third-party estimates: Apple's console shows only your own share per search term and a Rank of 1 to 5 or >5 (Apple-documented).
- Competitor brands: default to no (2021 and 2026: 99% no, never in a small campaign); brand searchers rarely convert, and poor conversion drags organic rank (contested: an August 2025 view calls undefended brands cheap, and Apple recommends a Competitor campaign on exact).
- Your own brand: no campaign by default, since brand searchers download you even below an ad, unless you rank around 50th for your name or the brand became the generic term (contested: Apple recommends a Brand campaign with an impression share target). A generic-word brand ("smoothie", popularity 30) burns budget. Monitor bidders (procedure 7); monitoring alone does not justify a campaign.
- Prune by budget share: no non-brand keyword dominates spend; turning one off made downloads drop, conversion rise and paying conversions stay flat (observed). Push the 10 to 50 converting low-popularity keywords to double-digit share of voice.

## Bids

- The suggested bid reversed direction (contested across time): March 2025, too high ($1 to $2 suggested, start at $0.25 to $0.50); February 2026, low ($1.82 suggested, impressions at about $8); July to September 2026, about half of what two placements require. In 2026 start at twice the suggestion in the US. Apple calls it a reference point from similar apps, set per ad group; bid recommendations cover exact match keywords only (Apple-documented).
- Raise until impressions: none after about 24 hours means too low; double until impressions start, then lower slowly to the last working level (contested: Apple warns of 24 to 48 hour data lag and recommends small gradual raises after several days). Recheck for lag before a second doubling.
- Set keyword-level bids, since the ad group default applies to every keyword without one (Apple-documented). Raise one keyword at a time, cheapest first; popularity-5 terms rarely need 2x. An $8 tap is fine for a week to get a keyword started, never as a channel.
- CPA cap (Apple-documented): an optional per-ad-group cap that lowers effective bids toward a target cost per install and limits impressions. Leave it unset until you know your CPA; never set it below the max CPT; before removing one, lower bids and wait a day.
- If you cannot afford the bid, add cheap relevant keywords instead; answer the March 2026 cost rise with more keywords, not more money per keyword. Anything containing "AI" has been very expensive since mid-2025.
- Turn off every automation; optimize for downloads or paying users, never views. The automated mode from March 2026 is Maximize Conversions (Apple-documented): a target CPA met on average, spend capped by the daily budget, an Automated Ad Group whose Search Match cannot be turned off, no keyword bids, installs only, not paying users. It has one positive report; test small, wait two weeks before changing the target, and keep pre-order apps on Manage Bids.

## Creative: a custom product page per keyword theme

- A custom product page on the ad group makes the ad match that page and the tap land on it; otherwise the ad uses the default page's screenshots in upload order (Apple-documented). That its first three screenshots form the ad is observed. If you run Apple Ads, use them.
- Limits (Apple-documented): 70 pages per app (35 until late 2025); 70 custom ads per ad group, one active at a time; the default ad serves on iOS before 15.2 and whenever the custom ad is paused. Pages need no new app version and can be swapped anytime.
- Lift is double-digit, never a benchmark: 10% and 12% higher install rates in Apple's 2023 case studies, about 27% more tap-through for a puzzle game with crossword and Sudoku pages, one 90% anecdote.
- Which page: take keywords with high impression share or the most downloads (not the highest TTR, which you want to raise), one page per intent, once 50 to 100 keywords get impressions. Observed themes: a profession ("invoice for carpenters"), an audience (women, men and couples for a workout app), a driver type ("Uber driver"). Put the keywords in the screenshots. Build audiences into keywords ("workout for women"), not gender targeting (inference).
- Optional in slot one, effectively mandatory in slot three.
- Localize every page for every market, or the ad goes on hold and stays paused after the fix until reactivated (Apple-documented). Today tab ads need an approved page, iPhone on iOS 16.4+, and no prices, offers, rankings or awards.
- Not an A/B test: one custom ad runs per ad group, so compare two weeks of default page against two weeks of custom page. Product page optimization does not run on custom product pages. Move winners to the organic page and keyword field; design rules are in `references/custom-product-pages-and-events.md`.

## Reading the numbers

- Definitions (Apple-documented): TTR is taps over impressions; CR (Tap-Through) is tap-through installs over taps; Average CPA is spend over tap-through installs. Installs include redownloads, within 30 days of a tap or one day of a view. CR (Total) adds view-through installs and is not comparable with CR (Tap-Through).
- A tap is a page view, not an install. Watch impressions and installs per keyword weekly; 50 impressions, 10 taps, 1 install is a readable funnel.
- Diagnosis: no impressions means relevance, budget or bid; impressions without taps means the keyword or screenshots do not fit; low TTR means the wrong crowd, whose taps never pay.
- Sufficiency (rules of thumb): 800 to 900 impressions show whether the ad works; judge tap-to-install on 50 to 100 taps, and at least 5 of 50 should install.
- Apple's dashboard is enough to run the campaign. Check that ad users clear onboarding like organic users; judge expensive keywords only by your own return on ad spend.
- Your attribution provider's count differs by design (Apple-documented): Apple counts a verified download within its windows and includes redownloads, a provider counts first open on its own windows; it gets Apple Ads data only with your permission through AdServices tokens. AdServices keeps data 21 days with no user identifier. Age or gender ad groups return no attribution.
- AdAttributionKit (Apple-documented): Apple Ads registered April 10, 2025, but as of November 2026 only through SKAdNetwork 1.0 to 3.0, click-through only, so its view-through installs never reach postbacks.

## Apple Ads and organic rank

- Spend has no direct effect on rank: the heaviest spenders are not number one everywhere, and ads conversion rate is not a ranking input. Apple says nothing about ad spend and rank.
- The one indirect path is ratings: paid installs lift rank only as new ratings in the last 30 days. Verify prompt timing first (`references/ratings-and-reviews.md`). Ratings count per country, so farm one country at a time; in a thin niche 10 to 20 seeded ratings can move rank 5 to 1 or 2 (observed).
- Ads as research: run every competitor keyword at low budget for about a week; per-keyword install conversion then picks what metadata and screenshots focus on.
- Paid to organic without spend (dated: 2024): keep competitors' paid keywords where you rank below position 10, check popularity and competition, add them to metadata.
- Channel choice: Apple Ads captures demand that exists, Meta and TikTok manufacture it; if nobody can say what they would type to find you, use `references/meta-ads.md`. In the ASO loop, Apple Ads follows metadata and screenshot work (June 2026).
- Cannibalization (contested, changed over time): January 2025, pause bids where you rank 1 or 2 organically; July 2026, compare total downloads before and after, and spend where you rank 5 to 10, up to 15 or 20. With two placements, organic rank 6 on an advertised keyword is weak.
- Featuring (dated: 2019, observed): list planned Apple Ads campaigns in Apple's promote form.

## Mistakes seen in teardowns

- Search Match on: a self-care app paying for "toilet chronicles", a voice memo app for "dream car giveaway".
- Bids too low: a mood app visible in Ukraine and not in the US. Relevance mismatch: a stuttering app whose metadata never said stuttering.
- Too few keywords: an astrology app at nine. A brand keyword that stops spending means a competitor started buying it. One term eating the budget: a savings tracker on "Empower Retirement" (popularity 58), swapped for about 50 popularity-5 terms.
- Model campaign: an art display app with 222 keywords and a long tail of fives; an AI math app runs 6,500 US keywords, almost 6,300 below popularity 11; copy the tail, not the budget.

## Procedures

1. Early-stage campaign (2021, updated): one country; many cheap long-tail keywords; exact match only; no competitor names; Advanced mode, Search Match off, no age or gender refinement, bids above the suggestion; manage actively.
2. Monthly harvest (2024): pick apps, country and device; 90-day window for breadth, 30 by default; exclude keywords you run; bucket into irrelevant, competitor names and relevant, reviewing the low-popularity band hardest; add the relevant ones as exact.
3. Seasonal keywords (2024): competitors on a 7-day window; search for the seasonal term; target the most and least popular, skipping the contested middle.
4. Negatives in a Search Match or broad campaign (2024): sort your paid keywords by popularity; pick terms that do not belong, however cheap; add them as exact negatives in brackets.
5. New country (2024): add many competitors; switch to that country's paid keywords; translate and pick relevant terms; localize metadata if required; build a campaign for that country alone.
6. Share-of-voice check (2024): your app plus 2 to 3 competitors and the repeated top advertisers; filter to shared keywords; per keyword, avoid a large gap, bid up on a small one; cross-check your console share and Rank.
7. Bidder monitoring (November 2026): for your brand and top category term, list each advertiser's impression share, organic rank and tenure; decide by the own-brand rule.
8. Custom product page ad (Apple-documented): create and localize the page; wait for approval; create the ad, which pauses any other custom ad; if it goes on hold, fix assets, then reactivate it by hand.

## Dated changes

- 2019 to 2024: "Search Ads"; the early-stage shape is set by 2021; custom product pages arrive in 2022 (cap 35); by 2024 Search Match and broad match are known budget drains.
- 2025: Apple Ads joins AdAttributionKit (April 10) and is renamed (April 15); "AI" terms expensive by mid-year; keyword-linked organic custom product pages at WWDC25; page cap 70; the channel much more expensive by late year.
- 2026: second placement live in March, with automated bidding; lifetime budgets end in June; WWDC26 shared ad assets still "Coming soon" in November; suggested bid about half of need by summer; slots one and three by September; Apple documents close-variant exact match and first-position impression share by November.

## Checks

- Advanced mode, search results, one campaign per country, Search Match off, automation off, no age or gender refinement; campaigns created paused; nothing removed that should be paused.
- Every keyword exact, set before saving; none in two campaigns; no ad group over 5,000; no negatives in an all-exact campaign beyond leaking variants.
- At least 300 keywords, mostly popularity 5 to 10, no head terms, no competitor brands; competitor data scoped to country, device and window; harvest monthly.
- Month capped at 30.4 times the daily budget; bids below it, twice the suggestion in the US (2026), set per keyword; zero-impression keywords raised one at a time after a lag check; no CPA cap below the max CPT.
- A localized, active custom product page per intent theme once 50 to 100 keywords get impressions.
- Break-even per tap computed; rating prompt verified; ad users clear onboarding at organic rates; 50 to 100 taps before judging tap-to-install; tap-through and total conversion rates never mixed; total downloads compared before and after bidding on keywords you already rank for.

## Open questions

- Unreconciled, dated in the body: competitor and own-brand campaigns, Search Match discovery, country grouping, negatives, bidding on organic number one keywords. Apple's advice is not outcome evidence; the tested rule stays the default.
- When brand monitoring should turn into bidding; slot-level pricing and where the lower slot sits; whether Maximize Conversions beats an exact long-tail campaign; whether age or gender narrowing ever pays for a niche app.
- How far exact close variants reach; whether description text changes ad cost; how the 5 to 100 tool score maps to Apple's 1 to 5; whether the WWDC26 shared assets change the custom product page's role.
- The seasonal exception is untested after March 2026; the monthly cadence predates 5,000-keyword campaigns; the pre-launch CPA ceiling misleads for subscriptions.
- The suggested-bid reversal is unexplained and every multiplier comes from a handful of campaigns; no TTR or conversion benchmark exists beyond "5 of 50"; custom product page lifts are case studies; competitor share is a third-party estimate; whether iPad is still cheaper is unknown.
