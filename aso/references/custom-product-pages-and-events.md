# Custom Product Pages and In-App Events

A custom product page is an alternate version of the product page served by traffic route. It changes what a visitor sees after the keyword match, never whether the app matches or where it ranks: a conversion lever for Apple Ads and Meta traffic, and since iOS 26 for organic keywords. Treat it as the App Store's landing page: one kind of visitor, exactly what they came for. Mechanics, limits and review rules are Apple-documented as of November 2026; strategy rules keep their own labels. Caption and layout rules: `references/screenshots-and-product-page.md`.

## What a page is and its limits

- A page has its own screenshots, app previews, promotional text and keywords, is localizable, has a unique URL and can carry a deep link (Apple-documented). Customize any of screenshots, previews and promotional text; the icon, name, subtitle and description cannot change per page.
- Only people who follow the page's link see it, or searchers once you assign keywords; everyone else sees the default page (Apple-documented).
- The URL is the default URL plus a product page ID parameter, generated on Create, visible in draft, unchanged by edits (Apple-documented).
- Since 2026 a page can carry its own product page header and a search result asset tailored per keyword (Apple-documented; WWDC26 presented them for iOS 27). Indexing of their text is not documented.
- Cap: 70 pages per app, not per localization (Apple-documented). Older guidance said 35, Apple's 2021-2023 figure; plan on 70.
- 10 screenshot slots. Fill at least six or seven, ideally all 10; building only the three Apple Ads shows is a common mistake (rule of thumb). Apple's floor, customize at least the first two, does not conflict.
- Pages route, they do not rank. Apple documents only routing: when the app appears for a keyword assigned to a page, that page replaces the default page. Apple never promises the app will appear and states no ranking or indexing effect. Page screenshot text is not indexed and attaching a page gives no boost (observed).
- Used to be: in 2021 pages were URL-only and Apple Search Ads could not use them; as late as 2024 search always showed the default page. Discard guidance that treats pages as URL-only.
- Not an A/B test (Apple-documented): product page optimization is unavailable on pages, and comparisons between pages are not like for like because audiences differ.
- Prerequisites (Apple-documented): app Ready for Distribution in at least one country or region; iPhone and iPad, pre-order included; shown on iOS 15 and iPadOS 15 or later, older devices get the default page; Account Holder, Admin, App Manager or Marketing role, or the App Store Connect API.
- Free, not listed publicly (only a competitor intelligence tool surfaces another app's pages), though Apple may feature a page in editorial stories and collections (Apple-documented). Build them for every app; a page with no ad, keyword or owned channel pointing at it does nothing.
- Adoption (observed): 83 of the top 100 grossing apps had pages in mid-2025, far fewer below; none of four apps torn down in September 2026 had one.

## Pages for paid traffic

- In Apple Ads, choosing a page for an ad variation sets both the ad's creative and its tap destination (Apple-documented). That its first three screenshots form the ad is observed.
- One active custom ad per ad group, at most 70 custom ads per ad group. The default ad, built from the default page in upload order, still runs on iOS earlier than 15.2 and whenever the custom ad is paused or on hold (Apple-documented).
- Segment ad groups by keyword intent, one page per group ("invoice for carpenters" to a carpenter page); Apple documents variations aligned to an ad group's keyword theme or audience. Put the group's keywords in the captions (rule of thumb). Bidding: `references/apple-ads.md`.
- Maximize Conversions (Apple-documented): the Automated Ad Group always uses the default page; run page-per-intent ads in additional ad groups.
- Placements (Apple-documented): Today tab ads must point to a custom product page localized in the default language of the campaign's country or region, with no prices, offers, rankings, awards or "App of the Day" wording; Search tab ads may use either page. Page deep links work from ads only on iOS 18 or later and are disabled when the ad group uses age or gender settings. Localize pages for every market a campaign reaches; a campaign duplicated into another language market can make variations incompatible.
- Lifecycle (Apple-documented): disabling a page puts its ad variation on hold, and it stays paused after re-enabling until you activate it by hand; deleting the page deletes the variation. During an icon test the served search ad shows the page's icon.
- Lift (Apple-documented outcome): on average 2.5 percentage points over the 1.6 percent default-page conversion rate, a 156 percent relative increase; Apple case studies show 33 percent higher conversion with 14 percent lower cost per install, and 20 percent for a seasonal page (2023). Do not quote 2.5 as a percent lift. Lift is near immediate (observed; Apple gives no timing).
- When and which (rule of thumb): with four or five working keywords, optimize the default page; once 50 to 100 or more get impressions, build pages per theme. Pick keywords by downloads or impression share, not tap-through; one page per essence of intent, five to seven pages, up to ten, for hundreds of keywords. Apple likewise says build the most distinctive pages first, each with an audience large enough to measure.
- Since the second ad placement in March 2026, slot three reaches browsers, not intent-driven searchers: a page is optional in slot one, effectively required in slot three, and pays only with very long-tail keywords (observed).
- Meta and other networks (Apple-documented): a network shows a page in StoreKit-rendered ads by passing its ID (`customProductPageIdentifier` with `SKOverlay`, `SKStoreProductParameterCustomProductPageIdentifier` with `SKStoreProductViewController`). Unsupported partners fall back to the default page: confirm support and test the URL first. Partner tracking needs App Tracking Transparency permission.
- Meta page count (rule of thumb): do not build one per ad at first. A new winning angle lifts performance about 3x, an aligned page adds 5 to 10 percent. Test angles on the default set, then keep three or four pages matched to ads sharing a pain point, audience and message. See `references/meta-ads.md`.

## Pages for organic keywords (iOS 26 and later)

- Timeline: announced at WWDC in June 2025; keyword picker live July 29 or 30, 2025; display needed an iOS 26 device; by July 2026 routing had worked for about a year (observed).
- Source (Apple-documented): assignable keywords come from the app's latest approved version and are selected per localization of the page. A term added to the keyword field is assignable only after that version is approved.
- Picker (observed): only keyword-field entries, never name or subtitle terms, picked from Apple's list; in the US the US English field supplies it.
- Whole entries (observed; Apple says only "any keyword or set of keywords"): a page attaches to a whole comma-delimited entry, so "YT Kids" must be one entry. Only the main localization's field needs phrase entries; other indexed localizations stay single-word.
- Visibility (Apple-documented): assign keywords at any time; a keywords-only change goes live without review. The page is searchable only once approved and set to visible. Keywords cannot change while the page is in review.
- Selection: match keywords to the page's intent and make each combination unique to one page (Apple recommends). Apple does not say whether overlaps are blocked, which page wins, or how many keywords a page may hold.
- Tradeoff: a field of single words does not fit how Apple expects pages to be used, and the restriction still held in August 2026. Add a phrase entry only when you can rank for it or pay for it; it weakens the field. Never duplicate a name keyword into the field to attach a page. See `references/keyword-research.md`.
- Strategy one: the default page serves the main keyword in the name; pages serve long-tail terms already in the field.
- Strategy two: find winning keyword and page pairs in Apple Ads, then move the keyword from the subtitle, never the name, into the field, get that version approved, and attach the page. Order (rule of thumb): reuse ad pages first, keep field terms non-repetitive, rewrite the field last and accept some rank loss.
- Reliability (observed): suggested keywords misaligned in September 2025, the link was "wonky" in January 2026, triggering was unreliable in April 2026. Apple's "can appear" leaves room for this. Verify on a current device in the target storefront.
- Extra localizations (contested, trending to no): triggering from another US-indexed localization was "leans yes" in August 2025, unknown in April 2026, "main localization only" by August 2026. Apple documents per-localization selection but not cross-storefront behavior.
- Pages and localizations do not replace each other: regional localizations miss audiences sharing one storefront. A micro-niche like "logo maker for barber shops" gets a page; seasonal demand gets both, prepared ahead. See `references/localizations.md`.
- Targets (rule of thumb): keywords already ranking with search popularity (Apple's 5-100 scale) of about 10 or more; keywords where the default page tells a different story; non-brand searches. Since 2026 add a search result asset tailored to the keyword; Apple suggests the same asset in the header and in search results.

## Designing a page

- Segment first: who downloads, why, what persuades them. By use case or feature; by user type when users identify by profession (plumber, electrician); by motivation in fitness (an event, a wedding); by demographics only in inherently demographic categories. Mine reviews, as specific as demand allows ("Knicks tickets"). Apple's common uses match: specific audiences, seasonal events, specific content or features.
- Axes (dated: 2021, still current):
  1. Features or use cases: easiest; matches how you promote the app elsewhere.
  2. Access: what the app gives the user; one page per major sport in a multi-sport app.
  3. Affinity: how users see themselves; a page for one team's fans.
  4. Promotion: one page per new feature, event or content release.
  5. Source or medium (contested): weakest by intent, since the channel says little about what the user wants; Apple recommends a page per channel whenever the best assets differ by channel, and per-channel pages enable channel-level measurement. Use one when creative differs or you need that measurement.
- Keep every screenshot and the video on one intent; show the feature in context and the actual person. Apple recommends the same. Repeat the searched term in captions for people, not the algorithm.
- Keep layout and branding identical across pages; swap only intent content. An affinity page may use the segment's colors and logos, which the default page must avoid. Segment the path to the paywall, not the price (Audible, observed).
- No pricing (Apple-documented): page metadata falls under App Review Guideline 2.3 and must not include pricing, offers or sales. Never write "free"; "free" searchers also do not monetize (rule of thumb). Relevance converts, not price.
- The default page shows the top three to five use cases by usage as one story; pages take the rest.
- Poor man's page: reorder existing screenshots so the keyword's use case leads, under 30 minutes. Beats no page; the lift figures assume pages done well.
- A separate video per page pays only where video drives the download (rule of thumb).
- Deep links (Apple-documented): a universal link or custom URL that takes people who tap Open to specific content; iOS 18 and iPadOS 18 or later; works only after approval, so resubmit after adding. Apple recommends universal links, no shorteners or redirects, and testing from the Notes app. Carry the intent into onboarding when pages differ substantially.
- Production (Apple-documented): reuse approved assets from the Asset Library; preview the page (product page and search views, Dark Mode, devices) in App Store Connect before submitting.
- How many (observed): Audible 13, Tinder 12, CapCut 12, Hallow 10; simple successful apps run 15 to 40. Do not aim for 70; drop underperformers.
- Inspect competitors' pages first and correlate them with their paid keywords; a big studio with none is an opening. See `references/competitor-research.md`.

Planning procedure:

1. Write down who downloads the app and why.
2. Pick one axis; source or medium only when the channel's creative differs or you need channel measurement.
3. Give each page one goal and build its screenshots, preview and promotional text for that segment only.
4. Plan the route (ad group, Meta ad, keyword entry, URL) with the page and use it only for that segment.

## In-app events

- Where (Apple-documented): iPhone and iPad events (competitions, premieres, live experiences) show on the product page, in search, in editorial and personalized recommendations, and in the App Store widget.
- Search display (Apple-documented): in results for the app, past downloaders, including those who deleted it, see the event card instead of screenshots; people who never downloaded it see screenshots; anyone searching for the event sees the card. Plan events in search as re-engagement, not acquisition. Add them after the screenshot strategy is settled.
- Crowding (rule of thumb): an event card takes about two result slots, a promoted in-app purchase about half. The first result can stack both, making the third nearly invisible.
- Product page (Apple-documented): events appear in start-time order, High Priority first; past downloaders see them above the screenshots. Priority also picks which event shows in search for the app.
- Rank: Apple documents no boost and said in 2022 that priority does not affect ranking against other apps. A launch-era 2021-2022 boost was observed (dated). Do not promise rank from events.
- Purpose (Apple-documented): all users, attract new, inform active, or bring back lapsed. It feeds recommendations, is not displayed, and never limits who finds the event. Pick a specific one.
- Acceptance (Apple-documented): one of seven badges (Live Event, Premiere, Challenge, Competition, New Season, Major Update, Special Event); a Major Update goes beyond UI tweaks or bug fixes, Live and Special Events bring new content, features or goods. No fitting badge means no event. Guideline 2.3.13: metadata describes the event, not the app; the event happens at the stated times; the deep link reaches it. Prices in event metadata cause rejection; repetitive daily tasks, price promotions without new content and awareness pushes are poor candidates. The low 2022 bar (observed) is no license to fake one.
- Limits (Apple-documented): 10 published, 15 approved, 50 drafts; 15 minutes to 31 days; discoverable up to 14 days before start; at most 10 overlapping start times; regional starts within 48 hours. Older guidance said 10 approved and 5 published.
- Metadata (Apple-documented): reference name 64 characters and unique, event name 30, short description 50, long description 120; badge required and not localized. After approval only availability, priority and future times can change. Write the real event name in title case, not a call to action; no all caps or text in media (Apple recommends).
- Media (Apple-documented): card 16:9, details 9:16, images from 1920x1080 or 1080x1920 up to 4K, videos 15 to 30 seconds. Cards have carried video since 2021.
- Review (Apple-documented): no new app version once the app is approved; an app's first events ship with its first iOS version; review took about 24 hours in 2022. Each event has a URL that falls back to the product page after it ends; promote it by email, ads and social. A featuring nomination for an event needs three weeks' notice.
- Measurement (Apple-documented): impressions by surface (product page, search, other), details views, opens, downloads, redownloads and notification opt-ins, after five associated downloads.
- Promoted in-app purchases (Apple-documented): up to 20 per page, shown in search (not consumables); no ranking effect stated.

## Product page optimization versus pages

The test procedure is in `references/screenshots-and-product-page.md`; here are the limits and how tests sit beside pages.

- Scope (Apple-documented): up to three treatments of icon, screenshots and previews (since 2026 also the header) against the original, a random share of iOS 15 or later visitors split evenly, chosen localizations, one test per app at a time, up to 90 days. No text metadata is testable, so keyword placement never is.
- Icons (Apple-documented): alternates must already be in the current App Store binary; an icon-only test starts without review; the winning icon needs a new app version. Icon tests have been documented since 2021 and previews are testable; discard older claims of an icon gap or untestable video.
- Independence (Apple-documented): visitors sent to a custom product page never enter a test. Run pages in Apple Ads and a test on the default page together. Test pages sequentially instead: baseline, then page A, then page B, or two weeks each (rule of thumb).
- Traffic (Apple-documented, 2023): treatments reach visitors from all sources, including paid advertising referrals, except page visitors. Discard the claim that tests use organic traffic only. A default Apple Ads ad likely lands where treatments show (inference).
- Duration (Apple-documented): impressions and time drive significance; use the duration estimate at 90 percent confidence, and cut treatments if it exceeds 90 days. No confidence shows for seven days; run in seven-day increments; results need five first-time downloads. A stopped test cannot restart, only be recreated. Older guidance said tests expire at 30 days; the limit is 90.
- Results (Apple-documented): Performing Better, Performing Worse, or Likely to Be Inconclusive at 90 percent confidence, on unique impressions. Applying copies only screenshots and previews, one treatment, irreversibly, and stops the test.
- First test: reorder live screenshots; a reorder-only or binary-icon-only treatment needs no review (Apple-documented). Keep one test running and ship a new set as a treatment, never outright (rule of thumb). Plan tests between releases (Apple recommends).
- Treatment screenshots are not indexed (observed); Apple says only that treatments may appear in search like the original.

## Workflow: setup, approval, attribution, evaluation

- Setup: App Store Connect, the app, Custom Product Pages, plus; name it, create or copy, pick keywords (optional), upload, submit. The reference name labels the page in analytics; a copy takes only the primary localization (Apple-documented).
- Review (Apple-documented): every page and edit is reviewed under Guideline 2.3, with no new binary once the app is approved. Before first approval, a page ships with the first iOS version. Pages, events, tests and in-app purchases can share one submission.
- Editing (Apple-documented): a page in review cannot be edited; withdraw to change it. An edit creates a new version that replaces the live page on approval, URL unchanged. Pages stay active across new builds.
- Timing: do not tie a standalone page submission to an app release (Apple recommends). Up to 3 days with one page in review at a time in August 2025 (observed); Apple documents neither.
- Disable and delete (Apple-documented): both redirect the URL to the default page; disabling is reversible, deleting is not. Changing the primary language later requires approved screenshots for every page.
- Analytics (Apple-documented): per page, impressions, product page views, downloads, redownloads, conversion, retention, proceeds per paying user, sessions and a default-page comparison, after five first-time downloads; since 2025 search traffic per page and filters by territory and source type.
- Attribution: source type separates search from referrals per page; separating channels (Meta versus email) needs one page per channel, as Apple recommends. In Apple Ads read conversion per ad group or keyword and rebuild weak pages. Meta view-through shows as App Referrer plus a share of Search, so rising search beside rising spend is not organic growth. See `references/measurement-and-cadence.md`.
- OS floors (Apple-documented): iOS 15 pages, iOS 18 page deep links, iOS 15.2 custom ads. Organic routing showed only on iOS 26 (observed). Many users take 6 months to 2 years to update (rule of thumb).

Evaluation procedure, per page. No conversion rate is universally good; the test is the page against the default page, on product page views, not impressions.

1. Wait for five first-time downloads, then read downloads and product page views.
2. Conversion is downloads divided by page views.
3. Compare with the default page at a similar number of views; never rank pages against each other.
4. Keep a page that converts higher if day-one retention holds; revise the audience and asset pairing if lower.

## Dated changes

- June 2021: pages, product page optimization and in-app events announced for iOS 15; 35 pages.
- By February 2023: page-based ad variations in Apple Search Ads. June 2024: page deep links.
- April 15, 2025: Apple Search Ads renamed Apple Ads.
- June 2025, WWDC: keywords for pages. July 29-30, 2025: picker live.
- Around November 2025: 70-page cap observed (documentation gives no date).
- March 2026: second ad placement at position three.
- June 2026, WWDC26: header and keyword-tailored search assets per page; opened to all developers October 2026.

## Checks

- Any pages? If none, that is the first gap. Each with one goal and a live route?
- One page per Apple Ads ad group, keywords in captions, custom ads outside the Automated Ad Group?
- Today tab pages localized for the market, free of prices, offers and awards?
- Before disabling or deleting a page: which ad variations use it, and who reactivates them?
- Six or more of 10 slots filled, one message, identical layout, no pricing or "free"?
- Each organic keyword a whole main-localization field entry from the latest approved version, unique to one page, page approved and visible, seen on a device?
- Deep links universal, tested from Notes, page resubmitted?
- Ad networks confirmed to pass the page ID?
- A test running on the default page, icons in the live binary, no release inside the window?
- Pages judged against the default after five first-time downloads, retention checked?
- Events with a fitting badge, event-specific metadata, no prices, planned for past users, not for rank?

## Open questions

- Organic routing: whether secondary localizations trigger pages; whether name or subtitle terms ever become assignable; why triggering is unreliable; how overlaps resolve; keywords per page; whether routing needs iOS 26 or any iOS 15 device.
- Indexing of page screenshots, test treatments and the 2026 assets rests on experience; Apple is silent. Which OS shows the 2026 assets is not restated after WWDC26.
- In-app events: no rank test since launch; which fields event search indexes; no conversion or re-engagement benchmarks; how often a card displaces organic results.
- Promoted in-app purchases as a rank signal: untested since 2022.
- Product page optimization: whether default Apple Ads ad taps enter a test; what a release does to a running test.
- Analytics: Apple defines conversion three ways, and which one the per-page figure uses is unclear. Apple's 2.5-point average gives no method; other lift figures are anecdotes.
- Undocumented: page review times after August 2025, more than one page in review at once, iOS 26 adoption share.
