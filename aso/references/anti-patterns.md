# Anti-patterns: common ASO mistakes

Mistakes that recur across 2025-2026 teardowns, the ones Apple's App Review Guidelines and documentation name outright, and 2019-2022 advice still in circulation. Each entry: the wrong move, why it hurts, the fix, an example where one carries a number. "(Apple-documented)" marks a rule Apple states, "(Apple recommends)" Apple's advice, "(rule of thumb)" a heuristic, "Observed" a teardown result, "(contested)" a disagreement with both sides given, "(dated: year)" a fact whose year matters. Apple wins on mechanics, limits and review rules; see `references/fundamentals.md` for the precedence rule.

## Breaking Apple's review rules

These get a build rejected, ratings removed or keywords edited by Apple. All Apple-documented as of November 2026.

- **A custom review prompt.** Guideline 5.6.1 requires the provided API (SKStoreReviewController) and disallows custom review prompts. A pre-prompt screen of your own ("Enjoying the app?") that itself asks for a rating is the banned pattern; review gating also drew a rank penalty that had not recovered two months after approval (observed, November 2025 to January 2026). Fix: call the system prompt directly at a success moment; a social proof screen may precede it only if it does not request a rating. The system shows the prompt at most three times per 365 days.
- **Forcing or buying ratings.** Guideline 3.2.2(x) bans forcing users to rate or review to access functionality or content; incentives for other in-app actions, such as completing a level, are allowed. Guideline 5.6.3 calls manipulation of charts, search, reviews or referrals discovery fraud, and repeated manipulative conduct leads to removal from the Apple Developer Program (5.6). Fix: no reward tied to a rating, no paid or farmed reviews.
- **Keyword stuffing and competitor names (Guideline 2.3.7).** 2.3.7 bans packing metadata with trademarked terms, popular app names or pricing information, requires keywords that accurately describe the app, and lets Apple modify inappropriate keywords at any time; competing app names in keywords are a common rejection reason. Competitor names also bring searchers who download the brand. Fix: only words that describe your app, no other app's or company's name anywhere in the metadata, no "free". Guideline 4.1 separately bans copying a popular app or lightly changing another app's name or UI.
- **Screenshots that do not show the app in use (Guideline 2.3.3, contested).** 2.3.3 says screenshots should show the app in use, not merely title art, a login page or a splash screen; text overlays are allowed. Teardowns favor a caption-only opener for almost every app. Both sides: Apple's rule governs review, the tests govern conversion. Fix: a large caption over real, cropped UI on every screenshot, never pure title art or a setup screen.
- **Prices, other platforms and adult assets in the page.** No prices or offers in names, subtitles, screenshots or previews (2.3.7); no other platforms' names or imagery (2.3.10); rights to every asset and fictional account data (2.3.9); icons, screenshots and previews at 4+ whatever the app's rating (2.3.8); extra purchases disclosed (2.3.2); creative assets on-brand with no unverifiable claims or pricing (2.3.14). Fix: audit every asset against this list before submission.
- **An irrelevant category.** It is grounds for rejection, and the primary category decides browse placement, search filtering and the Apps or Games tab. Fix: research how similar apps are categorized first (Apple recommends).

## Metadata: name, subtitle, keyword field

Rules: `references/metadata-writing.md`.

- **Brand first, keyword last, or brand only.** Weight falls left to right (observed), nobody searches an unknown brand, and a brand-only name gives the algorithm nothing. Apple recommends a distinctive name that avoids generic terms (contested with the tested rule; Apple documents no mechanism). Fix: keyword first and contiguous, brand last and short, the whole name still a unique phrase; brand first only when searched (Uber, Tinder). Observed: a 13-rating app with "subscription manager" (56) first ranked fourth.
- **Repeating a word across name, subtitle and keyword field.** Apple recommends against it; only the last instance survives (observed), so the word drops to the weakest position. Plurals are duplicates (Apple-documented). Fix: each word once per localization. Observed: MyRadar with 3,000 ratings ranked below apps with 584 on a duplicated "weather".
- **Several focuses, every character filled, or a generic or missing subtitle.** Weight is a fixed split across every word (rule of thumb), generic verbs forfeit 30 indexed characters, and removing a subtitle is penalized (observed). Fix: one idea per localization, two or three strong keywords over a full field, a focused subtitle. Observed: Expedia (about 70,000 ratings) is ninth for "trip planner" behind a 42-rating app with the phrase in its name.
- **Keyword field hygiene.** Spaces after commas, "app", "game", filler words, words of two characters or fewer, the category or company name and plurals waste the field (Apple-documented and Apple recommends). Phrase entries with internal spaces are valid but spend characters on spaces. Fix: single words, commas, no spaces; the only phrase entry routes an organic custom product page.
- **Budgeting 100 characters in a multibyte script.** App Store Connect Help states the keyword field as 100 bytes; the developer pages say 100 characters. Fix: count bytes for Chinese, Korean, Arabic, Russian and other multibyte localizations.
- **Adding "AI" for its own sake.** People search the feature: "AI voice memo" scored 5 against 55 for "voice memo" (5-100 scale), and "AI" in a name helps paid conversion, not organic search. Fix: lead with the feature; add AI only where the term has demand ("AI friend" 39).
- **Filling all 30 characters of a name or subtitle that contains "&" or ":".** The index counted special characters twice against a 30-character window (dated: 2022, unconfirmed since); Apple says only that they carry no extra weight. Fix: one spare character per special character, or drop it.
- **Writing the description for the index, or running one strategy for both stores.** The description is not an App Store search field; Apple uses it for web search results (Apple-documented). WWDC 2025 announced App Store Tags built from metadata, not description indexing. Google Play indexes description and review text. Fix: indexed words in the three fields, a description that sells to humans, keywords researched per store and country.

## Keyword choice

Rules: `references/keyword-research.md`.

- **Chasing the head term, or holding a rank on fives.** Head terms belong to apps that lead their names with the word and earn thousands of new ratings a month; Apple too says popular terms are highly competitive for newer or smaller apps (Apple recommends). Fix: the positions 3-5 test (term in the name? new ratings in 30 days?), never a 5 to 9 on the 5-100 scale leading the name.
- **Words nobody types, or a term whose searcher leaves.** Searcher vocabulary differs from the developer's ("step counter" 59, "steps counter" 5), and a disappointed searcher drags conversion. Fix: look up every term, mine competitors' organic lists, prefer "trading simulator" to "stock market" for a paper-trading app.
- **Gating winnability on competitors' download estimates.** The 2019-2021 test (match the number 5 result's downloads) was superseded in 2022 and by every 2025-2026 teardown. Apple lists downloads among its inputs without a weight, so "not downloads" is a weighting claim (contested). Fix: gate on name placement and new ratings in the last 30 days; use download estimates to judge whether the niche pays.
- **Mixing popularity scales.** Apple Ads shows Search Popularity on a 1-5 scale (Apple-documented); keyword tools show a 5-100 score whose derivation Apple does not document. A 5 is Apple's top band and the 5-100 floor. Fix: label the scale beside every value and never compare across them; see `references/data-inputs.md`.
- **Reading a pre-2025 popularity band as a threshold.** Before fall 2025 most US keywords scored 10-40 on the 5-100 scale (dated: 2019-2025). Since the re-normalization many real keywords sit at 5-10 and "a 17 is not terrible" (late 2026). Fix: compare within one period, judge against the top results' 30-day ratings.

## Localizations

Rules: `references/localizations.md`.

- **Ten localizations with the same English text, or words expected to combine across them.** Identical text is ignored, and "habit" in English plus "tracker" in Russian is not "habit tracker" (observed). Fix: one focus per locale with the theme keyword in that locale's name, phrases complete inside each locale.
- **Planning from the 2023 storefront table.** It put Australia, New Zealand, Mexico and Greece at one localization; Apple's current table gives them a second, Japan's extra is English (US), and India supports 11 extra languages (Apple-documented). Fix: use Apple's storefront table.

## Screenshots and product page

Rules: `references/screenshots-and-product-page.md`.

- **No caption, unreadable text, raw UI, half the slots empty.** Visitors read images first, and since mid-2025 captions also reinforce the index (observed). Fix: one message per slide in the largest font, maximum contrast, all 10 slots (Apple allows up to 10 per device size).
- **Captions that list features or ignore the searched term.** Benefits beat features in tests almost always. Fix: benefit plus the delivering feature over cropped UI; the first caption carries the first name keyword, and name and subtitle words recur about three times across the first three captions.
- **Superlatives, fake badges and small counts.** Unverifiable claims are banned in subtitles (2.3.7) and creative assets (2.3.14); "#1" is believable only around 10,000 ratings at 4.9 (rule of thumb). A displayed rating must match the current rating, and a review quote needs the reviewer's permission (Apple-documented). Fix: a real, permitted short quote; show a count only above about 1,000 and an average only above 4.3-4.4 (contested: 450 five-star ratings or 5,000 also read as plenty).
- **Shipping a new set or icon instead of testing it.** The gain is unknowable without a control; a seasonal icon swap moved downloads both ways (observed). Icons have been testable since 2021, provided the alternate icons are in the live binary (Apple-documented); the "back in October 2025" reading was wrong. Fix: ship it as a product page optimization treatment; a reorder-only or icon-only treatment needs no review.
- **Planning a product page optimization test on folklore.** Apple-documented: one test at a time, up to three treatments, 90 days or until stopped (the reported 30-day expiry is wrong), previews testable (the "videos cannot be tested" claim is wrong), chosen localizations, results on unique impressions after five first-time downloads, no confidence for seven days. A started test cannot be changed, a stopped test cannot restart, and applying a treatment stops the test and cannot be undone. A version released during a test may skew it. Apple recommends waiting for 90% confidence and ending inconclusive tests (contested with an April 2026 reading that an even result may be switched). Fix: plan tests between releases, run in seven-day increments, overlay revenue.
- **One mention per keyword (contested).** A June 2025 reading saw no gain beyond one mention; July 2025 to September 2026 settled on about three times. Fix: about three times across the first three slides, never the same caption twice.

## Custom product pages

Rules: `references/custom-product-pages-and-events.md`.

- **Apple Ads without a custom product page.** The page sets both creative and tap destination of the ad (Apple-documented); since March 2026 slot three reaches browsers, who need an obvious fit. Apple recommends customizing at least the first two screenshots. Fix: one page per intent once 50-100 keywords get impressions, six or seven screenshots crafted.
- **A page per ad as the first move, or a page as an A/B test.** A winning angle lifts about 3x while an aligned page adds 5-10% (rule of thumb); Apple's average page lift is 2.5 points over a 1.6% default rate. Tests are unavailable for custom pages, and pages route, they do not rank (Apple-documented and observed). Fix: test angles on the default page, then three or four pages matched to winning angles; judge two weeks of default page against two weeks of page.
- **Reusing one keyword set across pages.** Apple selects page keywords per localization from the latest approved version and recommends each combination unique to one page. Fix: one intent per page, no keyword shared; a phrase entry only when you can rank for or pay for it.
- **Staging an in-app event or promoting a purchase for rank.** Apple documents no boost and says event priority does not affect ranking against other apps; an event card replaces screenshots in search only for past downloaders. Prices in events cause rejection. Fix: run only real events, promote a purchase for the result space it earns.

## Ratings

Rules: `references/ratings-and-reviews.md`.

- **Never asking.** Downloads per rating of 240 means no prompt; above 100 is ugly (rule of thumb). Fix: add the system prompt. Observed: a weather app with 6 new ratings and a 240 held third for "weather forecast" (29).
- **Prompting in the first session (contested).** Since August 2026 Apple deletes ratings prompted too early (observed). Apple recommends asking right after a completed action, level or task, without interrupting. Both sides on onboarding: never inside it; or inside it after a first insight, because 75% or more of users are gone by day two (October 2025). Fix: a success moment first, never the launch screen.
- **Chasing stars, lifetime totals or a spike.** New ratings in roughly the last 30 days per storefront rank (observed); Apple names "number and quality of ratings and reviews" without defining quality (contested). Fix: steady weekly arrivals in the target country; treat the average as a conversion input.
- **Resetting the summary rating casually.** A reset applies to all countries at once and is irreversible after release; Apple recommends resetting sparingly because few ratings may discourage downloads (Apple-documented). Fix: reset only after a fix that changed the experience.

## Apple Ads

Rules: `references/apple-ads.md`.

- **Default settings left on, and the suggested bid trusted.** Every audited account with Search Match on paid for nonsense ("dream car giveaway" for a voice memo app). Apple recommends a Search Match discovery ad group whose winners move to exact (contested). The suggested bid ran 30-50% low (June 2026) and about half (September 2026). Fix: Advanced mode; Search Match off in keyword ad groups, or isolated in a discovery group whose search terms you read weekly; exact match; bids at twice the suggestion in the US, raised one keyword at a time until impressions appear.
- **Too few keywords, or a dominated term.** Impressions kick in around 300 keywords (rule of thumb; Apple allows 5,000 per ad group); a term where one app holds most impressions costs many times more. Fix: 300-1,000 exact long-tail terms; enter where five or more split the share.
- **Bidding where you already rank first, or on brands (contested).** January 2025: pause at rank 1 or 2; July 2026: compare total downloads and spend at ranks 5-10. 2026 teardowns: never bid on competitor brands. Apple recommends both a Brand and a Competitor campaign on exact match. Fix: decide with totals; no competitor brands in a small campaign.
- **Narrowing age and gender from day one.** 78% of iOS 17 and later search volume has Personalized Ads off and never sees an ad with age, gender or any refined audience; those settings also disable custom page deep links and AdServices attribution details (Apple-documented). Fix: all eligible users; treat competitor demographics as a hypothesis.
- **Reading third-party impression share as Apple's number.** Apple's console reports your own share only; competitor paid data is scans of ads that were seen. Fix: bid from the console; a competitor's "too few keywords" is an inference.

## Meta Ads

Rules: `references/meta-ads.md`.

- **Judging on blended cost per trial, or an ad the page does not keep.** The young install readily and rarely pay. Fix: split young from old on day one; the top ads' promise must be visible on the page, ideally a custom page opened by page ID.
- **Expecting paid installs to lift organic rank, web-to-app only, or installs that never rate.** Spend moves rank only through the ratings installs produce (observed), and about 5% of web traffic reaches the store, so the algorithm sees nobody. Fix: confirm the prompt before any campaign, run a hybrid unless top three is unreachable, benchmark installs per rating.

## Competitor research

Rules: `references/competitor-research.md`.

- **Revenue per download as a ranking for subscription apps.** It misreads subscription and consumable apps because revenue lags the download (dated: 2020), and every figure for an app you do not own is a third-party model. Fix: read it as how hard a competitor can fight for an install, label every estimate, compare your own app through peer benchmarks.

## Measurement

Rules: `references/measurement-and-cadence.md`.

- **Judging a rank change after three days, or changing metadata every week.** Changes take up to 24 hours to appear (Apple-documented) and ranks settle over weeks; three changes in ten days cut one app's impressions (observed). Fix: never judge before 2 weeks, big keywords after 3 weeks to a month; metadata every 2-3 weeks at most, screenshots twice a month, one or two new keywords per release.
- **No change journal, single snapshots, reverting on a bounce.** Fix: date every change, compare weekly medians per country and platform, revert at once only for a lost critical rank (contested).
- **Reading view-to-download as App Store Connect conversion.** App Store Connect's conversion rate is total downloads over unique impressions, and benchmarks and tests use the same definition (Apple-documented). View-to-download is a hand ratio, and it includes "no page" downloads straight from results. Fix: name the definition beside every rate, compare a hand ratio only with itself, filter by page type.
- **Reading App Store Search as organic.** Apple Ads performance is included in it (Apple-documented), and Meta view-through users search the brand (observed). Safari links count as Web Referrer, other browsers as App Referrer. Fix: read Search net of paid spend.
- **Reading a missing number as zero.** Referrer and campaign rows appear only above a data threshold; custom pages and tests need five first-time downloads, events five associated downloads (Apple-documented). Fix: wait for the floor.

## Dated advice

- **Trusting a republished article's date.** Much published ASO advice was re-dated in bulk in June 2026 with mostly unchanged 2019-2022 text. Tells: "Apple Search Ads" (Apple Ads since April 2025), a 35-page cap (70 per app now), "use all 100 characters", downloads as the gate, popularity bands of 10-40, one ad per results page, a 30-day test expiry, untestable videos, a 5-100 scale called Apple's own. Fix: date a claim by the facts inside it and check limits against Apple's current documentation.

## Checks

- Review rules: system rating prompt only, no custom prompt or gating, no reward for ratings, no competitor names, trademarks or pricing in metadata, screenshots show real UI, no prices or other platforms in assets, a relevant category.
- Name and field: keyword first, brand last, no word repeated, no plurals beside singulars, bytes counted in multibyte localizations, every term passed the positions 3-5 test on one labeled scale.
- Screenshots: captions over real UI, all 10 slots, changes shipped as a test planned between releases.
- Paid: every Apple Ads ad group has a page; Search Match off or isolated, demographics open, competitor impression share labeled an estimate.
- Measurement: every rate names its definition, Search read net of paid spend, no number judged before its threshold, a dated journal exists.

## Open questions

- Prompt timing, with Apple's "too early" of August 2026 undefined; revert timing; brand and competitor bidding; Search Match as a discovery group versus off.
- Whether Apple Ads traffic counts toward a product page optimization test: Apple's documentation is silent, a 2023 Apple talk includes paid referrals.
- Social proof thresholds; icon leverage; caption repetition.
- How strictly Guideline 2.3.3 is enforced against caption-led first screenshots.
- Whether the 2022 special-character truncation still exists.
