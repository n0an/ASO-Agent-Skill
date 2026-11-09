# Measurement and cadence: judging an ASO change

Every ASO change is a hypothesis about eligibility (which searches the app appears in), position (where it ranks) or conversion (what the page does with its impressions). Indexing is fast and ranking is slow, rank snapshots are noisy, App Store Connect's conversion rate is not the view-to-download ratio most benchmarks quote, and its source labels stop meaning what they say once paid channels run. This file says when to look, what to compare, and how to tell a real movement from a bounce. What each number is and where it comes from is in `references/data-inputs.md`.

## Before the first change: journal and baseline

- Record every change with its date, the field (name, subtitle, keyword field, screenshots, icon, custom product page, rating prompt), the localization and country, the before and after text, and the rank or rate you expect to move. Without this journal no movement can be attributed.
- Export impressions, product page views and downloads by source type from App Store Connect for the last 3 months before touching anything.
- Record two conversion baselines and label them: App Store Connect's conversion rate (definition below), per source type and territory, and page conversion, downloads divided by unique product page views over the last full month, times 100 (dated: 2021). Re-measure both after every change. A 5% figure often quoted beside the page-conversion definition is illustrative arithmetic, not a target.
- Snapshot ranks per keyword, country and platform before every round; track hourly where possible, read weekly. Track multi-word combinations and singular and plural forms as separate keywords.
- Change one thing per round so a rank move has one cause. What needs a new version (Apple-documented): keywords, description, subtitle and screenshots are version properties, so keyword rounds ride on releases; promotional text is the only text editable without a submission. Screenshots and previews can also change by applying a test treatment, header and search results assets by an approved Asset Library swap, and a custom product page's keywords without review (WWDC 2025). Older guidance flagged the keyword-field rule as unverified; it is settled.
- Log confounders in the same journal: the fall 2025 popularity re-normalization, the June 2025 start of screenshot caption indexing, the second Apple Ads placement in March 2026, Games app icon views counted as impressions (September 2026), search volatility around the iOS 26 to 27 transition (July to fall 2026), paid spend starting or stopping, seasonal demand, a competitor adding your term to its name.

## App Store Connect's conversion rate is not view-to-download

- Definition (Apple-documented): conversion rate = total downloads (first-time downloads plus redownloads) divided by unique impressions. A unique impression is one person who saw the app's icon anywhere on the App Store that day: search results, the product page, the Today, Games and Apps tabs, and since 2026 the Games app. Every product page view is also an impression. Apple's worked example: 50 downloads from 100 unique impressions is 50%.
- Counting rules (Apple-documented): uniques are deduplicated per person per day, so a search result view plus a tap into the page is two impressions, one page view and one unique impression. A first-time download is a Get or Buy tap, a redownload a cloud-icon tap; automatic downloads to a person's other devices are excluded. Summing daily uniques over a month does not give unique people; never sum them.
- Apple's documentation also phrases conversion two looser ways (downloads per device that viewed; product page viewers against downloads plus pre-orders) without saying which is current. The metric, product page optimization results and peer group benchmarks all use downloads over unique impressions; read every App Store Connect conversion figure that way.
- Warning: view-to-download benchmarks are a different ratio. The 3-4% rule of thumb and the observed 45%, 13% and 40% figures below divide downloads by product page views, computed by hand. Never compare them with App Store Connect's conversion rate or its peer benchmarks. One funnel, two ratios: 30,000 impressions, about 2,700 page views and 1,200 downloads is 45% view-to-download and 4% on Apple's definition; 11,000, 659 and 87 is 13% against 0.8%. Write numerator and denominator next to every rate you report.
- Downloads over page views also overstates the page's own effect: total downloads include downloads tapped straight from search results or browse without opening the page, which Apple reports as page type "no page" (Apple-documented). Separate them: in App Store Connect Metrics, open conversion rate, set the dimension to Page Type, filter by App Store Search to compare direct downloads from results with downloads after a page view, or by App Referrer to compare the product page with the store sheet used by ads. In Apple's examples, people who viewed the page first converted better.

## The funnel, sources and benchmarks

- Three steps, two hand-computed rates: unique impressions to unique product page views (icon, name, subtitle) and page views to downloads (screenshots, video, the rating shown). Read both per source type.
- Source types (Apple-documented): App Store Browse (featuring and top charts land here), App Store Search, App Referrer and Web Referrer; links opened in Safari count as Web Referrer, in other browsers as App Referrer. Apple Ads performance is included in these figures, so App Store Search is not purely organic. Referrer and campaign sources appear only above a minimum data threshold, and usage data covers only users who opted in, so a small campaign can be invisible rather than failed.
- Benchmark App Store Connect's conversion rate against the app's peer group (Apple-documented): grouped by category and business model, with similar download volume as an optional comparison since 2026; App Store Connect shows the 25th, 50th and 75th percentiles for conversion rate, retention, crash rate and proceeds per paying user, and since 2026 D35 proceeds per download and D35 download-to-paid conversion. Apple's one example peer group showed 1.19%, 2.91% and 6.78%; that is an illustration, not a norm. Below the group's 25th percentile, look at the page before the keywords.
- Rules of thumb on the page-view ratios only: 40-50% impression-to-view means icon and name are fine; 3-4% view-to-download means the page is the problem. Observed: the 45% and 13% funnels above and a low-competition utility at 40%; no utility benchmark exists beyond these. Expect lower page conversion in crowded same-feature categories and higher in niches (dated: 2021).
- Apple's custom product page figure (2.5 points above a 1.6% default-page rate, definition unstated) and its "more than 60 percent" for top-of-search ads (a tap metric) compare with none of the above.
- Diagnose by shape. Decent impression-to-view with abysmal view-to-download means the name pulls the wrong searcher, too few screenshots, or a keyword mismatch; remove a keyword whose views leave even where the app ranks. Ranks and impressions up with downloads flat means the page; a correct keyword change raises all three together (dated: 2019, consistent since).
- Fix visibility before conversion: 50 impressions a day means invisible, not broken. Conversion work pays once traffic exists (40 of 100 views instead of 30 is meaningful).
- Judge a keyword change on visibility metrics (ranks, impressions), not on downloads alone; downloads mix in conversion and seasonality (dated: 2020, still true).
- Conversion is a ranking input, sometimes large (rule of thumb): a bad rate is not penalized, better converters get a boost that lifts only already-competitive apps, and extreme spreads between keywords read as manipulation. Apple names downloads, ratings and reviews among search factors, not conversion rate, so this stays observed.

## How fast things move

- Indexing is fast: Apple says metadata changes can take up to 24 hours to appear (Apple-documented); observed pickup is within hours (a name change in 3-4 hours). Ranks make their sharp moves in the first 12-48 hours, then bounce and drift for weeks while the algorithm tests placements; apps often shoot up and fall back after a few weeks (observed, 2019-2026). Impressions follow ranks with a lag, downloads come last.
- Ranking settles slowly: judge a big keyword after 3 weeks to a month, a modifier or long-tail variant after about 2 weeks, never before 2 weeks (rule of thumb). Older practice used a flat 3-4 weeks (dated: 2019-2020); the two agree on big keywords.
- Ratings show faster than metadata (rule of thumb): a gradual rise shows in rank within days to a week; an ad-driven spike takes longer, since the algorithm wants a week of the new steady state. See `references/ratings-and-reviews.md`.
- Penalties recover slowly (observed): an app approved after a review-gating flag in November 2025 had not regained its category ranks by January 2026.
- The index remembers: removed keywords persist at reduced strength, and a name change to a new keyword transfers no weight; only ratings carry over.
- An organic custom product page attaches with an indexing delay, and triggering was unreliable through April 2026; a page not showing on day one is not a failed attachment.

## Change cadence

- Metadata (name, subtitle, keyword field) no more than every 2-3 weeks. Observed: three changes in ten days cut one app's impressions. The 2-3 weeks is the minimum gap between edits; the verdict on a big keyword still takes 3 weeks to a month, so a round normally waits for its own result.
- Screenshots at most twice a month since captions became indexed in mid-2025 (observed; Apple sets no cap). Changing them carries no penalty; the cap exists so each set can be read.
- One or two new related keywords per release, not a rewrite, and one hypothesis per round. Rotating three themed keyword sets for four weeks each (dated: 2020) fits only an app with no ranking history.
- Keep one product page optimization test running at all times. A test ends at 90 days or when you stop it (Apple-documented; older guidance reported a 30-day expiry), and a stopped test cannot be restarted, only recreated with the same treatments.

## The three-metric scorecard for a keyword strategy

A keyword-level evaluation loop (dated: 2020, nothing newer replaces it) that App Store Connect cannot give you; run it from your rank tracker.

1. Track every target keyword, multi-word combinations and singular and plural forms included.
2. Record the baseline: (a) the share of targeted keywords you rank for at all, target 100% (already at 100% means the list is too short or too unpopular); (b) the average rank across targets, which catches gains offset by losses; (c) the count of keywords ranked 1-10 with meaningful popularity, across everything you rank for. "Meaningful" was 10-100 on the pre-2025 scale; set the current floor yourself ("a 17 is not terrible", late 2026).
3. Ship the change; wait four weeks; record the three again. Ask first whether any metric got worse, then whether the result beats the last evaluation.
4. With no history, run the same metrics on a competitor over the same window, so a market-wide shift does not pose as your result. Keep what improved, replace what did not, repeat.

## Reading a product page optimization test

Setup, eligibility and what can be tested: `references/screenshots-and-product-page.md`. This is the measurement side.

- Limits that shape the read (Apple-documented): up to three treatments share the traffic proportion evenly, 90 days at most, no edits after the start, and fewer treatments or more localizations reach a result sooner.
- The metric is App Store Connect's definition (Apple-documented): unique impressions and conversion rate per treatment, conversion meaning downloads or redownloads over unique impressions. Icon treatments show while browsing and in search, screenshot and preview treatments in search and on the page, so high-impression low-tap placements dilute a gain. The 2022 description as "share of views that downloaded" is superseded.
- Result labels (Apple-documented): results appear after five first-time downloads tied to the test; no confidence shows in the first seven days; a treatment reads Collecting Data until it reaches 90% confidence, then Performing Better or Performing Worse against the baseline, or Likely to Be Inconclusive if 90 days will not be enough. The baseline defaults to the original and can be switched to compare treatments; hovering a rate shows its credible interval; data exports as CSV.
- Size the test before starting (Apple-documented): the optional duration estimate uses recent daily impressions and downloads to show the impressions and days needed for a chosen lift at 90% confidence. Apple's 2022 example needed about 174,404 impressions to detect a 5% improvement, about two weeks for that app. If the estimate exceeds 90 days, cut treatments or add traffic. At 10 page views a day only very large differences reach 90% within 90 days (inference from Apple's example), which is why variants must be abrupt; a one-word change never resolves at low traffic.
- Duration: at least a week, in seven-day increments to cover weekday and weekend patterns (Apple recommends); realistically a month (dated: 2022). Run any idea at least twice before giving up.
- Decision rule (contested): Apple recommends acting only at Performing Better or Worse (90% confidence or more), never on early results or minor uplifts, and ending and retrying a test where every treatment reads Likely to Be Inconclusive; a control win counts as a success. April 2026 practice may switch on an even or unclear result; Apple's mechanics allow it. Both: undo fast when the metric goes negative. Follow Apple when the test decides a default page with real traffic; take the 2026 latitude only as a tiebreaker between two acceptable sets.
- Watch revenue: results show impressions, conversion rate, improvement and confidence, not revenue (Apple-documented). A treatment can raise conversion while attracting users who do not pay, so overlay daily revenue on downloads for the test period and end the test if revenue drops significantly; Apple's own icon case checked downstream performance before applying the winner.
- Applying a treatment stops the test and cannot be undone (Apple-documented). A new version released during a test may affect its results if it carries tested assets; Apple does not say the test stops. Schedule tests between releases and log campaigns and seasonal shifts that start mid-test.
- Paid traffic in a test is contested: August 2025 says Apple Ads traffic counts, June 2026 says organic only. Apple's 2023 talk includes paid referrals; custom product page visitors are outside tests; the documentation never names Apple Ads. Working reading: an ad variation lands on a custom product page and is outside; an ad landing on the default page may be inside. Avoid a heavy paid push during a test you want clean.
- A live treatment's text is not indexed (observed, single report; Apple is silent); treatments are a conversion instrument only.
- Fallback when the native test cannot hold the change (a name, a keyword placement): the timed sequential test, 14-30 days per version (steps in `references/screenshots-and-product-page.md`, Procedures). It cannot separate the change from time of month or promotions, so use it only when nothing else holds the change.

## Custom product pages and off-store creative

- Custom product pages are routing, not experiments, and product page optimization cannot run on them (Apple-documented). Per page, App Store Connect shows product page views, total downloads, conversion rate, average retention and sessions, and the Metrics tab compares all pages by region or source type (Apple-documented).
- Compare each page with the default page, never with other custom pages, whose audiences differ (Apple recommends). Keep a page that converts higher at similar page views and holds day-one retention.
- Since organic search also lands on custom product pages (live fall 2025), App Store Connect cannot attribute page traffic by channel (September 2025). Compare sequentially: baseline, page A, page B, two weeks each; in Apple Ads read conversion per ad group. See `references/custom-product-pages-and-events.md`.
- Off-store creative test (Apple-documented): one App Store Connect campaign link per creative variant, used across channels; compare downloads and conversion by campaign; move the winning elements into a custom product page or a product page optimization test. Campaign data appears only above the minimum threshold.

## Reverting (contested)

- Advice diverged; give every side with its date. 2020: monitor hourly through the window and revert as the downtrend begins, before the damage becomes permanent. January 2025: wait a day or so, because an immediate revert confuses the algorithm. May 2025: revert at once only when a critical rank such as number one drops. October 2025: undo a clearly bad update and let it rest.
- Decision rule derived from the four: if the change cost a rank you depend on (number one or top three on the term that pays), revert at once and journal it; otherwise hold the full window, because the early bounce is the algorithm testing, not the verdict. A product page optimization treatment that reads Performing Worse is ended, not held.

## Diagnostics: a rank that makes no sense

- Your exact name keyword is absent from the first three pages: look for a duplicate of a name word in the subtitle or keyword field, since only the last instance survives (observed). If the name carries "&" or ":", check the trailing keyword separately (a 2022 observation, unconfirmed since).
- A competitor with zero or few ratings sits above you: it probably has a shorter keyword list and more new ratings in the last 30 days in that storefront than its lifetime total suggests. Check name placement and the 30-day count, not lifetime ratings.
- You rank 99 or 147 for a term: that proves relevance and is easier to lift than a new term. A metadata keyword outside the top 10 is not helping; push or prune. See `references/keyword-research.md`.
- Impressions moved with no change of yours: check the two paid slots (positions one and three since March 2026, so organic visibility means top three), in-app event cards, a competitor adding the term to its name, your own 30-day rating count, and the Games app icon views counted since September 2026. Since June 2025 a jump without a metadata change usually means your captions align with your keywords, and a drop means they are missing or misaligned (observed).
- A negative trend with no obvious cause usually means a basic check was skipped: duplication, placement, a dropped subtitle, a stalled prompt (rule of thumb, dated: 2022). Read the seven-day trajectory, not a snapshot.
- Downloads per rating above 100: the prompt fires at the wrong time or not at all. Change one placement at a time and compare new ratings per day by country; App Store Connect lacks per-country ratings history, so your tracker or an export holds it (dated: 2020).

## Per-keyword conversion: the one-week Apple Ads test

- Organically you cannot see which keyword's visitors download; App Store Connect gives totals by source type, not by term. The only instrument is a one-week low-budget Apple Ads campaign: exact match, Search Match off, every competitor keyword plus your own organic ranks between roughly 10 and 80, bids raised until impressions appear. See `references/apple-ads.md`.
- Read it as a funnel per keyword, aggregated weekly. A tap is a page view, not an install. Data sufficiency (rules of thumb): 800-900 impressions show whether the ad works, 50-100 taps show tap-to-install, at least 5 of 50 should install; directional only.
- Let the result choose what the name, subtitle and first three captions focus on; a paid test is cheap and binary, a metadata change costs a 2-3 week slot.
- Without spend (dated: 2024): competitors' paid keywords where you rank organically below 10 are organic candidates; read 90 days for breadth, 7 for trends. Paid data is a floor on what competitors buy.

## Reading App Store Connect sources with paid channels running

- Apple Ads installs sit inside the App Store Search figures (Apple-documented): subtract them before crediting organic search growth. Apple Ads attributes an install within 30 days of a tap or one day of a view, redownloads included (Apple-documented), so its counts and App Store Connect's will not match line for line.
- Meta traffic lands as App Referrer plus a share under App Store Search, because view-through users look the brand up (observed, late 2025). Rising Search alongside rising Meta spend is not organic growth. See `references/meta-ads.md`.
- A falling conversion rate may only mean the creative now brings different audiences; read conversion against the source mix before calling it a page problem. Out-of-store traffic needs more impressions per download than store search in any case (dated: 2021).
- Apple Ads spend has no direct effect on organic rank; its only path is the ratings paid installs produce. Judge a campaign on return on ad spend and installs per keyword, never on organic rank movement.

## Rank data is noisy

- Compare weekly medians per keyword, not single snapshots; watch the trend over 2-3 weeks; hold country and platform constant.
- A tracker that stops at 200 shows "unranked" for both "not indexed" and "ranked 250"; check eligibility on a device set to the storefront (see `references/data-inputs.md`).
- Popularity scores from before and after the fall 2025 re-normalization are not comparable; ratings count per storefront over roughly the last 30 days (a working model from rank data, not an Apple statement).

## Checks

- A dated change journal with before and after text and the hypothesis exists before the first edit; a 3-month funnel baseline by source type is recorded.
- Every reported rate names its ratio: App Store Connect conversion rate (downloads over unique impressions) or page conversion (downloads over page views); the 3-4% and 40-50% rules are applied only to page-view ratios, the peer group percentiles only to App Store Connect's rate.
- The current round changes one thing; the last metadata change is at least 2-3 weeks old and rode on a version; screenshots changed at most twice this month.
- No rank is judged before 2 weeks; big keywords get 3 weeks to a month; the scorecard is re-read at four weeks; a revert happened only for a lost critical rank and is journaled.
- Rank comparisons use weekly medians per country and platform; Search growth is read net of Apple Ads and Meta.
- A product page optimization test is running between releases, sized with the duration estimate, read no earlier than seven days, applied only at Performing Better unless both sets were acceptable, with revenue overlaid.
- Per-keyword conversion claims rest on an Apple Ads test with 50-100 taps per keyword.

## Open questions

- Revert timing: a day's wait versus an immediate revert for an undefined "critical rank".
- Apple's documentation phrases conversion three ways and does not say which is current; the metric and its benchmarks use downloads over unique impressions.
- Whether Apple Ads traffic that lands on the default page counts toward a product page optimization test; what a release with tested assets does to a running test beyond "may affect the results"; per-channel attribution of custom product page traffic after September 2025.
- The 30-day rating window and the spike filter are a working model from rank data, not Apple statements; the page-view rules of thumb rest on one source and three observations, none for utilities; the 12-48 hour window is a 2019 observation never re-measured.
- Whether a rating from a paid install weighs the same as an organic one is assumed, never tested.
