# Meta Ads

Meta manufactures demand the App Store cannot capture and scales far beyond Apple Ads, but a Meta install pays ASO back only through the rating it produces, and the audience the creative selects decides that yield. This file is the store-facing view plus the campaign choices a marketer must make or review. Rules on what works in creative and audiences come from one October 2025 account and count as (rule of thumb) unless marked; Meta's documentation (captured November 2026) settles campaign mechanics but reports no outcomes and says nothing about App Store ranking, ratings or custom product pages; Apple's documentation settles the App Store side. Campaign depth, iOS attribution and the launch and reconciliation procedures are in `references/meta-campaigns-and-measurement.md`; Apple Ads in `references/apple-ads.md`; consent and the ATT prompt in `references/app-tracking-transparency.md`.

## Who Meta Ads suits

- Choose the channel by whether people already search for what you do. A nameable search term means ASO and Apple Ads first; no term means creating demand on Meta or TikTok, with ASO kept because it is free. The searched half is settled: a store visitor is ready to get an app, a Facebook or Instagram browser is not (dated: 2021, still holds). The no-search-term branch rests on 2025-2026 accounts alone.
- Read competitor downloads first: steady growth means people search, weekend-only spikes mean paid campaigns. If competitors run Apple Ads, start there, since Meta needs creatives you do not yet have.
- The trade: Meta gives scale and cheaper views, Apple Ads gives intent. Out-of-store ads need more impressions per download (dated: 2021); Meta users rate less, while Apple Ads users convert considerably higher but the channel caps out (rule of thumb, October 2025).
- Meta is the dominant paid channel for iOS-first apps (October 2025); most subscription apps buy users on Meta or Google at rising cost (late 2025).
- A popularity-5 niche may be cheap on Apple Ads because it is small; if not, Meta or TikTok tells users what is possible. A head term owned by giants ("Bible", popularity 73) takes massive Meta spend; settle this before committing to the idea.
- Buying ratings: Apple Ads for searched categories, Meta for novel apps whose users rate less, one country at a time since Apple counts ratings per storefront. Meta's structure advice fits: never target one country in several campaigns at once; group countries into tiers by past performance (Meta recommends).

## Before you have data: competitor proxies

All figures here are third-party modeled estimates, not App Store Connect or Meta data (Procedure 1).

- Cost of entry (dated: 2020): the more ad networks successful competitors integrate, the costlier paid competition; there is room only if you can afford that spend.
- Cost-per-acquisition ceiling (dated: 2020): the competitive set's revenue per download over 30 days. Flag it as weak for subscriptions and consumables; nothing offers a substitute such as lifetime value per install by channel.
- Where to advertise (dated: 2020): spend in the countries where competitors get downloads, skip the rest.
- Who pays (dated: 2020): the dominant age and gender of the top five apps by revenue; in one casino set this turned a generic campaign ROI positive (observed). It predates App Tracking Transparency, and an Advantage+ app campaign cannot target age or gender at all (Meta-documented), so use it for creative and offers only. The same holds for the 2026 list of other apps your users also use: a partnership list and overlooked competitors, not a targetable audience.

## Campaign choice: app promotion with Advantage+ app campaigns

- Acquire new users with the app promotion objective (formerly app installs; only the name changed). Engagement, leads, sales and traffic objectives reengage existing users (Meta-documented).
- Run it as an Advantage+ app campaign (formerly automated app ads): Meta sets bidding, audiences and placements, app promotion only (Meta-documented). For iOS 14.5 and later one help page makes Advantage+ the only setup, one ad set and one optimization type per campaign (Meta-documented); whether manual setup survives for iOS is open.
- It can target country (or regions or worldwide), optional language, and operating system (contested: one Meta page lists app store instead). It cannot target age, gender, device, interests, behaviors, lookalikes or custom audiences (Meta-documented). Minimum age (18+ by default, 21 in some countries) and city or region are account-wide settings (Meta-documented).
- Anyone who installed or opened the app in the last 90 days is excluded automatically (Meta-documented); reengagement needs another objective and a deep link.
- Placements are automatic across Facebook, Messenger, Instagram and Audience Network (Meta-documented); the formats you upload are the remaining placement lever (inference).
- Prerequisites: the app registered on Meta for Developers, the ad account linked, app events from the Facebook SDK, a measurement partner or the Conversions API. Without them, or without one install in the last 28 days, the campaign optimizes for link clicks and tracks no installs (Meta-documented). Confirm this before reviewing creative.

## Optimization goal in brief

- Four goals: installs, link clicks, app events, value of conversions (Meta-documented). Link clicks is a fallback Meta does not recommend.
- Installs for a new app or thin event data, Meta's choice for reach and lowest cost per install (Meta recommends). App events only when a standard event completed by 1% to 30% of users has more than 100 attributed conversions in the two weeks before launch (Meta recommends); for subscriptions, Start Trial or Subscribe. Value of conversions maximizes purchase values only in app promotion; predicted lifetime value and profit are web-only (Meta-documented).
- Trial optimization skews delivery young, who trial readily and rarely pay (rule of thumb). Meta does not address the skew, but its 1% to 30% advice points the same way: move to a deeper event such as a paid subscription once volume allows.
- Leave a learning campaign alone: an ad set exits learning after about 50 results in the week after the last significant edit, earlier results do not predict later ones, and edits, frequent budget changes included, restart it (Meta-documented). Below 88 installs a day per campaign, reporting likely shows null conversions (Meta-documented).

## Creative leads targeting

- "Creative is targeting": Meta picks the audience, the creative decides who sees the ad. Target broadly and read creative-level age and placement breakdowns (October 2025, corroborated August 2025). Meta now enforces the broad half: Advantage+ takes only country, language and operating system so its system can find audiences (Meta-documented). Meta's old best-practices page recommending device, lookalike and connections targeting predates iOS 14.5 and is history.
- Never trust an aggregate gender split; age bands skew differently. Per-band data now feeds creative, offers and the reading of breakdowns, not delivery (inference).
- Media type dictates placement, placement dictates audience: 9:16 video goes to Reels, Stories and the young; the Facebook feed's older users need static creative. The ceiling is creative. Upload assets per placement, such as vertical video for Stories (Meta recommends).
- Split young from old on day one, in analysis: the young are cheap, trial readily and rarely pay; the old install poorly and pay far more. Know each band's break-even cost per trial; never judge on blended cost per trial. Meta reports age, gender, country, device and placement breakdowns for Advantage+ and AEM campaigns, but SKAdNetwork-attributed Advantage+ campaigns show no results, so the per-band read needs AEM attribution (Meta-documented). Placement insights are (contested): one Meta page says they are not offered, the same bundle lists the breakdown.
- Price follows the creative: Reels UGC brings young users, $70 a year converts them terribly and halving it can quadruple conversion (observed); vary offers through onboarding.
- Angles come from reviews, ideally a competitor's users complaining about a feature you have (2026 method: 1- and 2-star reviews, last 30 days, both stores, grouped by version). Test many angles, then double down; two or three ads drive 90% of volume. Meta's emphasis differs: upload the maximum (50 images or videos, 5 primary texts, 5 headlines) and refresh 2 to 4 times a month, never during learning (Meta recommends); its asset-level creative reporting supports either read.
- Show, don't tell: 5 to 10 second ads of the product doing the transformation; "we added AI" means nothing. Such ads cut one photo editor's acquisition cost enough to open Brazil, Indonesia and Mexico (observed). Meta recommends the same: what the app does, visuals over text, the app on a device, value in numbers. Fully synthetic UGC risks backlash; clean audio gives it away.

## Aligning the ad with the product page

- The product page is the landing page. What the top two or three ads promise must be visible on it; a cheap install that fails there is worse than zero. Each custom page's screenshots, preview and promotional text serve one segment, and its URL goes only into promotion aimed at that segment (dated: 2021, still holds).
- The first screenshots continue the ad's promise: Meta and TikTok traffic wants the feeling the ad sold, niche visual first; Apple Ads traffic tolerates more technical screenshots. See `references/screenshots-and-product-page.md`.
- A custom product page can be a Meta ad's destination, app promotion included (Apple-documented): Apple names social media ads as a place for the page URL, and ad networks open a page in StoreKit-rendered ads by passing its page ID to SKOverlay or SKStoreProductViewController. Up to 70 pages per app. No Meta page mentions custom product pages, so how the URL is entered on Meta's side is undocumented. Mechanics in `references/custom-product-pages-and-events.md`.
- Not one page per ad at the start: a winning angle lifts about 3x, an aligned page adds 5 to 10% (rule of thumb). Once angles are known, keep three or four page sets matched to ads sharing a pain point, audience and message; segment by feature, access, affinity or promotion, by traffic source last (dated: 2021).
- Apple's figure is far larger: referrals to a custom page convert 2.5 percentage points higher on average, 156% over the 1.6% default-page average (Apple-documented aggregate). The baselines differ (all referred traffic against all default-page traffic, versus aligned against unaligned inside Meta), so keep "find the angle first" and quote both when sizing the work.
- A custom page URL is the default URL plus a product page ID; editing keeps it; a disabled or deleted page redirects to the default page, so its ads keep delivering to an unaligned page (Apple-documented). Repoint or pause ads before disabling.
- Continue the promise into the app. Meta's install ads send people to the App Store; a deferred deep link opens the promised content on first launch and, in campaigns reaching iOS 14.5+, needs Facebook SDK 18.0.3 or later (Meta-documented); Meta recommends it to cut drop-off. For existing users arriving through a custom page, add a custom page deep link (iOS and iPadOS 18 or later). Use universal links: Apple recommends them with no shorteners or redirects, and Meta supports them.
- Meta traffic may land on the store sheet, a lookalike outside the App Store, rather than the product page; you and the ad network choose, and Apple says it can meaningfully affect conversion (Apple recommends comparing them, Procedure 2, step 6). Which one Meta opens is undocumented.
- The icon matters little for Meta traffic, which lands on the page or sheet; it drives impression-to-tap in store placements and so the organic uplift that lowers blended cost (rule of thumb). "AI" in the app name helps paid conversion, not organic search (observed, May 2026).

## Measurement in App Store Connect

- Meta's in-app ads land as App Referrer, discovery inside another app (Apple-documented). Web Referrer counts only a link tapped in Safari; any other browser counts as App Referrer (Apple-documented). Definitions in `references/measurement-and-cadence.md`.
- Search is not purely organic. A fair share of Meta-driven installs lands under App Store Search because view-through users look the brand up (rule of thumb, late 2025; neither Apple nor Meta describes it), more so for under-35 audiences and video placements; Apple Ads performance is also included in search figures (Apple-documented). Rising Search with rising Meta spend is not organic growth.
- Read store metrics against the traffic source before calling anything an ASO problem: a falling install rate may only mean older, higher-quality audiences. Filter conversion rate, retention and proceeds per paying user by source type such as App Referrer (Apple recommends).
- Referrer and campaign-link data appear only above a minimum threshold, and per-custom-page metrics only after five first-time downloads (Apple-documented); do not read a page or link before then. Per page, Analytics shows views, downloads, conversion rate, retention, sessions and proceeds per paying user against the default page, and the Metrics tab compares pages by source type (Apple-documented).
- App Referrer covers every in-app source with no split by referring app, so the read is cleanest when Meta is the only large in-app buy running (inference).
- Make one App Store Connect campaign link per creative variant, filter by campaign, and carry winners into a custom page or a product page optimization test (Apple recommends). Whether such a link survives inside a Meta app promotion ad is undocumented.
- Never expect Meta's Results to equal App Referrer downloads (inference from both platforms' rules): App Store Connect counts total downloads, redownloads included, from every in-app network; Meta counts installs it attributes to its own clicks within its windows, partly modeled; AEM windows are click-only, so a view-then-search install shows in Search but not as a Meta result. Reconcile with the procedure in `references/meta-campaigns-and-measurement.md`.
- "Dumb installs": a paid install never turned into a rating moves neither store conversion nor blended cost. Benchmark installs per new rating (observed): Cal AI 15 to 17, MyFitnessPal 24 to 25 with apparently no onboarding prompt.
- Rating prompt: inside onboarding after a first insight, never on the launch screen, since 75% or more of users are gone by the next day (October 2025). Since August 2026 Apple deletes ratings prompted too early, and nothing draws the line, so prompt after real value and watch for deletions after each release. See `references/ratings-and-reviews.md`.

## Attribution in brief

- Apple side (Apple-documented): AdAttributionKit (formerly SKAdNetwork) credits the most recently clicked ad among registered networks, sends data after app open, and thins and delays postbacks under crowd anonymity thresholds; size test cells to clear them. Apple Ads' AdServices sees nothing outside the App Store, so Meta and Apple Ads can both claim one install; AdAttributionKit is the official last click. Never sum channel claims.
- Meta side (Meta-documented): each iOS 14.5+ app promotion campaign uses Aggregated Event Measurement (AEM) or SKAdNetwork. AEM now covers app promotion without SKAdNetwork event setup, rolling out per account as of November 2026; SKAdNetwork is optional. Details in `references/meta-campaigns-and-measurement.md`.

## Web-to-app versus app install

- Web-to-app funnels (web quiz, web payment) take 80 to 90% of major players' budgets. Only payers, about 5% of web traffic, reach the store, so install rate exceeds 90% but the algorithm sees nobody; store volume and ratings starve (rule of thumb). Meta's thresholds starve too: install optimization needs an install in the last 28 days, learning about 50 results a week, and reporting goes null below 88 installs a day (Meta-documented).
- Rational where top three is unreachable. Otherwise run a hybrid: app promotion campaigns acquire new app users while sales, leads and engagement campaigns reengage (Meta-documented), keeping organic search available.
- Do not justify web-to-app as escaping App Tracking Transparency measurement: website conversion campaigns reaching iOS 14.5+ also run through AEM, and Conversions API events may fall under AEM's limits (Meta-documented). The documented gain is value optimization: predicted lifetime value and profit are web-only under the Sales objective, while app promotion maximizes purchase values only (Meta-documented). Store fees as a motive: no evidence.
- Web funnel payers count as Web Referrer only via Safari, otherwise as App Referrer (Apple-documented); Meta's in-app browser is undocumented.

## Meta Ads and organic rank

- The mechanism is (contested): one view calls install and rating volume the two top ranking inputs; the other says paid installs move rank only through the ratings they produce. Apple and Meta are silent. Both land on one rule: buy the audience that rates. See `references/keyword-research.md`.
- Meta's Rate is an optimizable event, but nothing ties it to App Store ratings; do not optimize for it expecting store ratings.
- Observed: Cal AI tops "calorie" (popularity 51) with 205K US ratings against Lose It's 720K and MyFitnessPal's 2.1M, on cheap Reels and TikTok volume that rates more per install.
- A break-even Meta campaign is justified if it holds top rank where the profit is: cost per result rises past the ideal-customer bubble and ASO brings blended cost back down.
- Competitor ads are public in Meta's Ad Library; study the best competitor's (MyFitnessPal ran only about nine, observed), but prefer reviews as the angle source. Method in `references/competitor-research.md`.

## Procedures

Launching a Meta campaign and reconciling counts are in `references/meta-campaigns-and-measurement.md`.

1. Pre-launch paid-acquisition check (2020, third-party estimates): (1) take the top results for the idea's main keyword as the competitive set; (2) pull 30-day estimated downloads and revenue in the target storefront; (3) set the cost-per-acquisition ceiling from revenue per download, flagged weak for subscriptions; (4) count each one's ad networks; (5) pull downloads by country and the top five apps' age and gender, both for spend allocation and creative only.
2. Reading a Meta campaign on the Apple side (2026, Apple-documented): (1) create one custom product page per angle set with a recognizable reference name; (2) put its URL, or page ID for StoreKit-rendered ads, in the ad; (3) wait for five first-time downloads; (4) on the Acquisition tab, read the page against the default page; (5) on the Metrics tab, compare all pages filtered to App Referrer; (6) set conversion rate's dimension to page type, filtered to App Referrer, to compare product page and store sheet; (7) filter retention and proceeds per paying user by source type.

## Dated changes

- 2018: SKAdNetwork (now AdAttributionKit). 2020: competitor proxies as the first campaign inputs. 2021: App Tracking Transparency, the reason web onboarding exists; custom product pages announced at 35 per app (now 70, raised November 2025).
- 2025: Threads placement and notification ads raise Meta's ad load; by October custom pages accepted as Meta destinations; late 2025 the biggest new-app surge in about nine years crowds inventory.
- August 2026: Apple deletes early-prompted ratings. September 2026: App Analytics renamed "Analytics"; Apple cites the 2.5 point custom-page average.
- November 2026, Meta documentation: app installs renamed app promotion, automated app ads renamed Advantage+ app campaigns, no age, gender or audience targeting in them, AEM covering app promotion per account.

## Checks

- Can a user name a search term? If yes, Apple Ads first.
- Before launch: competitor ad networks, revenue per download and downloads by country pulled; ceiling flagged weak for subscriptions.
- App promotion as an Advantage+ app campaign, optimizing for installs or events, not link clicks; app registered, account linked, events flowing.
- Goal fits the data; nothing judged or edited during learning; volume near 88 installs a day or nulls expected.
- Demographic and cross-app estimates used for creative and offers only; nobody expects age or gender targeting.
- Results read per age band and placement under AEM, never blended; break-even cost per trial known per band.
- Angles from reviews; 5 to 10 second show-don't-tell creative; assets per placement.
- Top ad promises in the first screenshots; deferred deep link on SDK 18.0.3+; custom pages in three or four angle sets, none disabled under a live ad, read after five downloads filtered to App Referrer; product page versus store sheet compared.
- Search and App Referrer read against Meta and Apple Ads spend; Meta Results not expected to equal App Referrer; claims never summed.
- Installs per new rating benchmarked; rating prompt after a first insight, deletions watched.
- Web-to-app justified by value optimization, not by escaping AEM; hybrid unless top three is unreachable.

## Open questions

- One voice: every rule on what works in Meta creative and audiences comes from one October 2025 account; Apple and Meta add mechanics, not outcomes.
- Delivery targeting is settled for Advantage+; how much per-band and cross-app research should shape creative and offers, and whether the account-wide minimum age pays, is open. No subscription-era substitute for the revenue-per-download ceiling.
- Ranking: install volume as a direct input versus ratings only.
- Unaddressed by Apple: the view-through Search share; any App Referrer split by referring app; which conversion-rate denominator its overview means.
- Undocumented on both sides: which page type Meta opens, how Meta's in-app browser is filed, whether campaign links or custom page URLs survive in app promotion ads, whether manual setup exists for iOS 14.5+. Absent everywhere: a budget split across channels, store fees as a web-to-app motive.
- Apple's 2.5 point custom-page average and the 5 to 10% aligned-page lift are unreconciled.
- Where "too early" begins for a rating prompt is unknown.
