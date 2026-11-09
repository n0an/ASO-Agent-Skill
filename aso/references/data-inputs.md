# Data inputs: what each ASO step needs and how to read it

This skill is tool-agnostic. Every step below names the data it needs, where that data ultimately comes from, and the traps in reading it. Use whatever keyword research tool, rank tracker, market intelligence product or attribution provider the user has connected (often as an MCP server or CLI); when none is available, say which step is blocked and fall back to the manual sources listed here. Apple supplies your own App Store Connect analytics, peer group benchmarks, the storefront language table and Apple Ads reports, and documents how each metric is defined; read those definitions before comparing any two numbers. Everything about an app you do not own is a third-party estimate and must be labeled as one.

## The data model

| Input | What it is | Ultimate source | Needed for |
|---|---|---|---|
| Search Popularity (Apple) | Apple's relative demand for a term, 1-5, 5 most popular | Apple Ads keyword recommendations and reports (Apple-documented) | sizing a term inside Apple Ads |
| Popularity score (third-party) | Relative demand on a 5-100 logarithmic scale; 5 is minimal demand, not zero; re-normalized fall 2025 | keyword research tools; described as derived from Apple Ads data, derivation undocumented | choosing keywords, sizing a niche, pruning |
| Rank | Your position for a term, per storefront and platform (iPhone, iPad, Mac) | the public App Store search results | tracking changes, opportunity tests, diagnostics |
| Difficulty | An estimate of how strong the ranking apps are; scales differ by tool | derived from live results | tiebreaker after the ratings test |
| Top results for a term | Positions 1-10 with names, subtitles and rating counts | the public App Store search results | the opportunity test, competitor discovery |
| 30-day new ratings | Ratings gained in the storefront in the last month | for your app, App Store Connect ratings per country, snapshotted over time (no ratings-over-time view is documented); for others, public counts over time | the ratings test, winnability |
| Downloads per rating | 30-day downloads over 30-day new ratings, per storefront; lower is better | App Store Connect for your app; estimates for others | prompt health, competitor prompting |
| Competitor organic keywords | Terms a given app ranks for | derived from rank scans | research waterfall, gap analysis |
| Competitor paid keywords and impression share | Keywords a competitor's ads were seen on, with an estimated share, per country and device | daily scans of results; only ads that were seen | Apple Ads seeding, avoid-or-enter decisions |
| Competitor download and revenue estimates | 30-day downloads and revenue, multi-window trends, downloads by country | a market intelligence tool's models; Apple publishes no individual app's numbers | sizing a niche, gating competitors, pre-launch validation |
| Revenue per download | Estimated 30-day revenue over 30-day downloads | derived from the estimates above | how hard a competitor can fight for an install |
| Audience demographics and cross-usage | Age and gender by band; apps a competitor's users also use | model estimates from public data | targeting hypotheses, competitor discovery |
| SDK list | Third-party SDKs in a competitor's binary, with removals | signature matching by a market intelligence tool | paid-spend, retention and platform inferences |
| Own metadata per localization | Name, subtitle, keyword field, description, promotional text, screenshots | App Store Connect | audits, duplication checks, localization planning |
| Storefront languages | Each storefront's default and additional languages, which are the localizations searchable there | Apple's storefront table in App Store Connect Help (Apple-documented, current as of November 2026) | localization planning |
| Impressions, product page views, downloads | Counts by source type (App Store Browse, App Store Search, App Referrer, Web Referrer), territory, page type and period | App Store Connect Analytics (Apple-documented definitions) | the funnel, measuring a change |
| Conversion rate (Apple) | Total downloads over unique impressions | App Store Connect Analytics, benchmarks, product page optimization | peer comparison, test results |
| Page conversion (hand ratio) | Downloads over unique product page views, last full month, times 100 | computed from App Store Connect counts | the page baseline before a change |
| Peer group benchmarks | Your app's metrics against the 25th, 50th and 75th percentiles of a peer group | App Store Connect Analytics (Apple-documented) | the only Apple-sanctioned comparison with other apps |
| Keyword-strategy scorecard | Share of targets ranked, average rank, count of top-10 ranks on popular terms | your rank tracker plus popularity | the four-week loop, competitor benchmark |
| Apple Ads reports | Spend, impressions, taps, installs, TTR, CPT, CPA, your own impression share, search terms | Apple Ads (Apple-documented definitions) | campaign review, per-keyword tests |
| Paid attribution | Installs and events by network and campaign | your attribution provider, Meta Ads Manager, AdAttributionKit | Meta review, blended cost; not a ranking input |
| Autocomplete and Trending Searches | What the App Store suggests per country | a real device or a tool that captures them | long-tail discovery, intent |

## Reading popularity: two scales, never mixed

- Apple Ads shows Search Popularity from 1 to 5, 5 the most popular, in keyword recommendations and reports (Apple-documented). Recommendations add installs, spend and cost estimates over a seven-day period from historical data.
- Keyword research tools show a 5-100 logarithmic score that tools describe as Apple's number; Apple documents no such scale, so its derivation is undocumented. Every popularity band in this skill is on the 5-100 scale.
- Never mix them. A 5 is Apple's top band and the 5-100 floor. Label the scale next to every value in every output ("popularity 34 on the 5-100 scale, read 2026-11-09").
- Compare 5-100 values only within one period. The score was re-normalized in fall 2025: many terms dropped to 5 or below 10, 100 stays pinned to a growing top term, and by late 2026 "a 17 is not terrible" (observed). Thresholds learned earlier are stale; see `references/keyword-research.md`.
- Either score is app-independent and country-specific, and neither is download volume. Estimate downloads from what the ranking apps earn and from your own impressions once you rank; even a 5 on the 5-100 scale can mark a paying market.
- A missing score means the tool had no data, not zero demand.

## Reading ranks

- Ranks are snapshots. Compare weekly medians and watch the trend over 2-3 weeks (rule of thumb; see `references/measurement-and-cadence.md`).
- Country and platform must match: a US iPhone rank is not a US iPad rank nor a Canadian iPhone rank.
- Below rank 10 an app is effectively invisible; since March 2026 two of the top results are paid, so organic visibility means the top three (observed; see `references/fundamentals.md`). Read a rank gap by distance to the top, not by the difference: 191 against 181 is no gap, 11 against a competitor's 1 is a near win, 247 against their 3 marks a term for the next metadata round (observed, October 2026).
- A tracker that reports only the top 200 shows "unranked" for both "not indexed" and "ranked 250"; check eligibility by searching the exact term on a device.
- Metadata changes take up to 24 hours to appear (Apple-documented). Do not read ranks for a change before then.

## Reading difficulty

- Difficulty estimates differ by tool and are not Apple data (what goes into them: `references/keyword-research.md`). Use them to order candidates, never as a pass or fail threshold.
- The decisive check is manual: do positions 3-5 carry the term in their name, and how many new ratings did they get in 30 days? See `references/keyword-research.md`.

## App Store Connect Analytics: Apple's definitions

All Apple-documented unless marked. Since September 2, 2026 the section is called Analytics (formerly App Analytics), with six acquisition metrics.

- Impression: any view of the app's icon on the App Store, in search results, on the Today, Games and Apps tabs and on the product page, and since 2026 in the Games app. Every product page view is also an impression. Unique impressions are deduplicated per person per day: a search result view plus a tap into the page is two impressions, one page view and one unique impression.
- Downloads: first-time downloads are Get or Buy taps; redownloads are cloud-icon taps; automatic downloads to a person's other devices are excluded. Total downloads are both.
- Conversion rate: total downloads divided by unique impressions (50 of 100 is 50%). The conversion metric, peer benchmarks and product page optimization results all use this definition. Apple's own pages also define conversion per device that viewed the app and as product page viewers to downloads and pre-orders; name the definition before comparing.
- Source types: App Store Browse (featuring and top charts land here), App Store Search, App Referrer (discovery inside another app, such as an in-app ad, and links opened in any browser other than Safari) and Web Referrer (links opened in Safari). Apple Ads performance is included in these figures, so App Store Search is not purely organic.
- Page type: downloads tapped straight from search results or the tabs without opening the page report as "no page". Filter conversion by page type with source App Store Search to separate direct downloads from downloads after a page view; with source App Referrer, to compare the product page with the store sheet an ad network can open instead.
- Campaign links: one link per creative variant lets you filter conversion and retention by campaign (Apple recommends).
- Custom product pages: per-page views, downloads, conversion rate, retention, sessions, proceeds per paying user and search traffic, filterable by source type, not by individual channel. Apple recommends one page per campaign or channel when you need channel-level quality. Apple's average: custom product pages convert 2.5 points above a 1.6% default-page rate.

## Privacy thresholds: when numbers appear

- App referrers, web referrers and campaign links appear only above a minimum data threshold (Apple-documented). A missing referrer row means too little data, not zero traffic.
- Usage and retention data cover only users who opted in to share analytics (Apple-documented).
- A custom product page shows metrics only after five first-time downloads (Apple-documented).
- Product page optimization results appear after five first-time downloads and show no confidence level in the first seven days (Apple-documented).
- In-app event analytics appear after five associated downloads (Apple-documented).
- Benchmarks use differential privacy, and a more specific download-volume peer group can be withheld (Apple-documented).
- Plan small tests and pages with these floors in mind: a page that cannot reach five first-time downloads cannot be judged.

## Peer group benchmarks

- Peer groups are built from the categories you selected and the business model (subscription when 50% or more of revenue comes from auto-renewable subscriptions), with three weekly download-volume tiers as an optional filter since 2026 (Apple-documented). Tier boundaries are undocumented.
- Benchmarks show your value against the 25th, 50th and 75th percentiles in weekly intervals, for eight metrics as of 2026 covering conversion, retention and monetization, including D35 proceeds per download and D35 download-to-paid conversion (Apple-documented). Apple's own apps may be in the peer set.
- Apple publishes peer percentiles for your app only, never another app's numbers.
- Apple's example travel peer group converted at 1.19%, 2.91% and 6.78% at the three percentiles: an illustration, not a norm.
- Apple's action map (Apple recommends): weak conversion, use product page optimization, custom product pages and localization; weak retention, in-app events and onboarding; weak monetization, the best D35 sources, trials and territory pricing.

## Reading the funnel

- Two hand ratios sit beside Apple's metric: unique impressions to unique page views (icon and name) and page views to downloads (screenshots and page). Impression-to-view of roughly 40-50% means icon and name are fine; view-to-download of roughly 3-4% means the page is the problem (rules of thumb). Neither is App Store Connect's conversion rate.
- View-to-download overstates the page's own conversion, because total downloads include "no page" downloads straight from results. Filter by page type before calling a page strong.
- Page conversion baseline: downloads over unique product page views over the last full month, times 100 (dated: 2021 definition). Record it per source and country before any change; there is no universal benchmark, and the peer median is the nearest one.
- "App Store Search" includes Apple Ads performance (Apple-documented) and people who saw a Meta ad and then searched the brand (observed). Rising Search alongside rising paid spend is not organic growth (see `references/meta-ads.md`).
- Judge a custom product page against the default page at a similar page-view count, keep it if higher, revise if lower (dated: 2021; Apple adds day-one retention as a check).

## Reading Apple Ads data

- Definitions (Apple-documented): TTR is taps over impressions; CR (tap-through) is installs over taps; a search term is the query a person typed, distinct from your keyword. Bid recommendations exist only for exact match keywords.
- Exact match includes spelling variations, word rearrangements and translations (Apple-documented), so a per-keyword test reads a keyword's close variants, not one literal query.
- Report data can lag 24 to 48 hours (Apple-documented); a metadata change reaches the live ad within two hours.
- Attribution (Apple-documented): Apple Ads counts App Store-verified downloads within 30 days of a tap or one day of a view, redownloads included; measurement partners count first opens. In AdAttributionKit Apple Ads appears for taps only, and a third-party network and AdServices can both claim one install; AdAttributionKit is the official last click among registered networks. Age or gender settings remove AdServices attribution details.
- Two impression shares share one name. Apple's console reports your own share per search term, for first position and all positions, with a 1-5 rank, and never a competitor's share (Apple-documented). A third-party share is a competitor's estimated share from daily scans of ads that were seen, per country and device: a keyword whose ads earned no impressions is absent, so a 65-keyword campaign can show as one.
- Decide bids from the console. Use the estimate only to compare competitors on a term: skip a term where one app holds the majority (52-60%) or three hold about 85%; enter where five or more split it (dated: 2024). Read 90 days for breadth, 7 for trends, 30 by default.
- Bidder monitoring (November 2026): per advertiser on your brand and top category term, share, organic rank and tenure; rules in `references/apple-ads.md`.

## Reading competitor estimates

- Every download, revenue, demographic, cross-usage, SDK and impression-share figure for an app you do not own is a third-party model, never App Store Connect data. Write "estimated" next to each one. A tool should withhold an estimate below its accuracy bar (dated: 2020); no Apple number has ever validated these models.
- Downloads and revenue: read the 30-day scale, then 90, 180 and 365 days plus year over year, as a pair; falling downloads with rising revenue was read as hyper-targeting (one method on one app, PicsArt, confidence medium). Downloads collapsing (24,000 to 4,000 a month) with revenue nearly flat was read as a paid burst that ended while subscriptions coast: the app no longer buys installs, an opening on its keywords (speculation, one app, October 2026). Split by country first: PicsArt's downloads were 31% India and 6% US.
- Revenue per download says how hard a competitor can afford to fight for an install ($0.64 cannot outbid $6.01). It misreads subscription and consumable apps because revenue arrives long after the download (dated: 2020); flag it for every subscription app. Its use as a pre-launch cost-per-acquisition ceiling: `references/competitor-research.md`.
- Downloads per rating for a competitor shows whether it prompts; thresholds in `references/ratings-and-reviews.md`.
- Demographics are model estimates; read them by age band, since the aggregate gender split can differ from the largest band's. Cross-usage lists the apps a competitor's users also use: a targeting profile, overlooked competitors, and a churn read when many rivals appear.
- SDK lists come from signature matching, can include SDKs later removed, and have no published accuracy. Inferences from them: `references/competitor-research.md`.
- Validation is a snapshot: keep tracking the same apps after deciding (dated: 2020).

## Storefront languages

- Apple's storefront table (Apple-documented, as of November 2026) lists each storefront's default and additional languages; localized keywords are searchable wherever the language is supported. Metadata can be localized in 50 languages and locales.
- US storefront: English (U.S.) plus Arabic, Chinese (Simplified), Chinese (Traditional), French, Korean, Portuguese (Brazil), Russian, Spanish (Mexico) and Vietnamese: ten localizations, about 1,000 keyword-field characters. That the language of the text does not matter to the index, and that no localization has priority, are observed, not documented.
- Other storefronts, and why the 2023 reverse-engineered table is stale: the table in `references/localizations.md`.
- A new localization copies everything from the primary language except the description and keywords; deleting one reverts its regions to the primary language (Apple-documented).
- To test whether text in a non-native language indexes in a given localization, put a unique throwaway term in its keyword field, ship, and search it on a device set to the storefront after 24 hours. Planning rules in `references/localizations.md`.

## Keyword-strategy scorecard inputs

- The loop and its three metrics are in `references/measurement-and-cadence.md`. It consumes, per keyword, country and platform, the rank at the baseline and four weeks later and popularity on one scale and one period; for the competitor benchmark, the same for one competitor over the same window from the same tracker.

## Working with a connected data tool

A connected keyword, market intelligence or ads tool replaces lookups, not judgment; without one, an assistant only guesses demand, competitors and size (rule of thumb, 2026).

- Scope every request: the app (resolve its store ID first), store, country and time window. Unscoped requests make the tool guess or scan every storefront, slowly and, where market lookups are metered, at a cost. Ask for the numbers behind each answer so a wrong one looks wrong (rule of thumb, 2026).
- Audit order, one country at a time: (1) own metadata per localization and every term the app ranks for; (2) the top 10 for three or four core terms, keeping the apps that recur as the competitor set, whatever they do; (3) each one's monthly download and revenue trend; (4) gaps: terms they rank for and you do not, with both ranks; (5) lift candidates: low-popularity terms you rank for outside the top 5; (6) competitor reviews for feature requests and missing tools (drop pricing complaints), then your own complaints; (7) if ads run, the paid sequence below. Impressions, page views, conversion by source, benchmarks and your own ratings per country come only from App Store Connect.
- Assistants summarize tool output to 20-50 rows. Ask for the count you need or add a competitor to widen it; keep the long list for research and a short, reasoned list for the metadata round (observed, October 2026).
- Treat the first answer as a draft: one request fits a niche of many small terms differently from one of large terms or a multi-function app. Follow up with narrow, app-specific questions (rule of thumb, 2026).
- Paid sequence, weekly or monthly: waste first; then any keyword in two campaigns in one country, which bids against itself, drains two budgets and splits the data; then converting keywords held back by impressions (under 50 a month), fixed by a higher bid; then competitors' long-tail paid keywords, screened for head terms (rule of thumb, 2026). Rules in `references/apple-ads.md`.
- Never delegate the winnability call (the top-5 test in `references/keyword-research.md`, not a score or an assistant's "within reach"), metadata wording and placement (`references/metadata-writing.md`), or bid levels (console data). Every write (bid change, removed keyword, new ad group, review reply) goes out as a draft and waits for the user's yes on the exact change.
- Check a tool number against what the user knows; an empty result from a thin sample ("no complaints" on an app with few reviews) means too little data.

## Minimum viable setup without tools

1. Search each candidate term on a real device set to the target storefront; record the top 10 apps, whether the term is in their names, and their rating counts.
2. Pull your own metadata for every localization from App Store Connect and diff for duplicates across name, subtitle and keyword field.
3. Export impressions, page views and downloads by source type and page type from App Store Connect Analytics for the last 3 months; compute the page conversion baseline for the last full month and note Apple's conversion rate beside it.
4. Open the peer group benchmarks and record conversion, retention and monetization against the median.
5. Snapshot your ratings count per country weekly; App Store Connect shows ratings per country but documents no ratings-over-time view.
6. Record every metadata change with its date in a journal; without that, no rank movement can be attributed.
7. Competitor estimates do not exist without a tool. Fall back to public rating counts over time, version history and visible metadata, and say that download, revenue, demographic and SDK inputs are blocked. Your own impression share comes from the Apple Ads console; a competitor's share is blocked.

## Checks

- Every popularity value names its scale (Apple 1-5 or third-party 5-100) and its date; 5-100 values compared were collected after fall 2025 or within one period.
- Rank comparisons hold country and platform constant.
- The opportunity test used live top-5 results and 30-day ratings, not a difficulty score alone.
- Every conversion number names its definition: Apple's (downloads over unique impressions) or a hand ratio; no hand ratio is compared with a benchmark.
- Funnel numbers are split by source type and page type, and App Store Search is read net of Apple Ads and Meta spend.
- No page, test or event is judged before its five-download floor and, for tests, seven days.
- Conversion was compared with the peer median before the page was blamed.
- Every competitor figure is labeled an estimate; revenue per download is flagged for subscription apps; impression share is named as console (yours) or estimate (theirs).
- Localization plans use Apple's storefront table.
- A dated change journal exists before the first metadata edit.
- Every tool-sourced number shows its app, country and window and whether it is account data or an estimate; no write went out without the user's yes.

## Open questions

- How the third-party 5-100 score relates to Apple's 1-5 Search Popularity: undocumented.
- Apple defines conversion three ways across its pages; the per-page custom product page figure does not say which it uses.
- Benchmark download-volume tier boundaries and the minimum data threshold for referrer rows: undocumented.
- How App Store Connect files a link opened in Meta's in-app browser, and whether App Referrer can be split by referring app: not shown.
- Whether text in a non-native language indexes equally in every localization: observed, not documented.
- The accuracy of SDK detection and of every download, revenue and demographic model; no Apple number validates them.
- A revenue-per-download correction for subscription apps; none is stated anywhere.
