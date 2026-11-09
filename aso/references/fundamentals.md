# Fundamentals: how App Store search indexes and ranks

App Store search works in two stages. The words in an app's metadata decide which queries it is eligible for; inside that eligible set, the observed model says apps are ordered mainly by new ratings in the last 30 days in that storefront and by where the keyword sits in the metadata. Apple documents the first stage in detail (searchable fields, limits, formatting, rejection reasons) and lists the inputs of the second stage without weights, so the ordering rules here are reverse-engineered from rank data unless marked (Apple-documented). Rules that held from 2019 through 2026 are stated flat; rules that rest on one period carry their year. The other reference files assume this model, so read it first.

## Precedence: whose rule wins

- On mechanics, limits, definitions and review rules, Apple's current documentation (App Store Connect Help, Apple's developer pages, Apple Ads Help, as of November 2026) wins. Where a field-tested rule states a different limit or mechanism, use Apple's value and note the old one only when it prevents a common mistake.
- Where Apple's current documentation and an older WWDC session or Tech Talk differ, the documentation wins and the talk is dated history (for example, custom product pages were 35 per app in 2021-2023 and are 70 now).
- On ranking weights, windows, thresholds, conversion lifts and bidding, Apple documents nothing, so the observed rules stand with their labels.
- Keep "(Apple recommends)" apart from "(Apple-documented)". Advice such as "use a distinctive name" or "turn Search Match on for discovery" does not override a tested rule; write both sides as (contested).
- Where two Apple pages disagree, say so and plan for the tighter reading. Example: the keyword field is 100 bytes in App Store Connect Help and 100 characters on the developer pages; in multibyte scripts budget 100 bytes.

## The model as Apple documents it

- Searchable fields (Apple-documented): name, subtitle, keywords and company name; the primary and secondary category are also indexed. Apple's own lists disagree slightly: one Apple page names title, subtitle, keywords and primary category as the text-relevance fields, another omits the subtitle. Treat name, subtitle and keyword field as the planned surfaces.
- What search considers (Apple-documented, no weights): text relevance (title, subtitle, keywords, primary category) and user behavior ("downloads, ratings and reviews, and more"). Apple's discoverability page names "downloads and the number and quality of ratings and reviews". Search also uses in-app purchase metadata.
- Ratings and reviews influence how an app ranks in search, and the summary rating is specific to each territory (Apple-documented). Apple documents no 30-day window, no velocity and no recency weight.
- Documented non-inputs (Apple-documented): promotional text does not affect search ranking; in-app event priority sets the order on your own product page, not your ranking against other apps.
- The description is not among the App Store search fields; Apple says it is used for web search engine results, and Apple Ads also reads it for ad relevance (Apple-documented).
- Results can show developer cards, in-app events, promoted purchases, custom product pages, categories, editorial content and Apple Ads, plus up to three screenshots or previews and the rating per app; people can search in natural language and see suggested searches and regional Trending Searches (Apple-documented).
- App Store Tags (Apple-documented, as of November 2026): generated from metadata with AI and human curation, United States App Store only, built from en_US metadata. The only control is deselecting a tag; deselecting all may hurt discoverability. Apple says tags improve relevance; no rank effect has been measured.
- App information changes take up to 24 hours to appear on the App Store (Apple-documented). Do not read a missing change as a failure before then.
- Keywords are version metadata: a keyword-field change ships with a new app version, and promotional text is the only product page text changeable without one (Apple-documented).
- Apple may modify inappropriate keywords at any time, and Guideline 2.3.7 bans packing metadata with trademarked terms, popular app names or pricing information (Apple-documented). See `references/anti-patterns.md`.

Where Apple's list and the observed model diverge, write both sides:

- Downloads (contested): Apple lists downloads among the behavior inputs; every reading from 2022 on says downloads move rank only through the ratings they produce. Apple gives no weight, so plan around ratings and never claim downloads do nothing.
- Star value (contested): Apple says "number and quality of ratings and reviews"; every 2022-2026 reading says the star value does not move rank. Apple does not define quality, and it need not mean the star average. Plan rank around the count; treat the average as a conversion input.
- Name (contested): Apple recommends a distinctive name that avoids generic terms; tested rank data says the most valuable searched term goes first. Apple documents no mechanism, so the tested rule stands; write the keyword lead so the name still reads as a unique phrase (`references/metadata-writing.md`).
- Screenshot text: Apple's searchable fields and text-relevance list name no screenshot text; Apple says screenshots feed App Store Tags (WWDC 2025). The caption reading below stays (observed).

## Two stages: eligibility, then order

- Eligibility (Apple-documented): an app can appear for a query only if the query's words sit in its name, subtitle, keyword field, company name or category in one indexed localization. Ranking happens only inside that set. If you are not indexed for a word, no amount of ratings helps.
- Order (observed, consistent 2022-2026): after eligibility, apps are sorted mainly by new ratings in the last 30 days in that storefront. The count of ratings matters, not written reviews. Lifetime totals do not count, and a one-day spike is ignored; a consistent flow beats spikes unless the spike is massive.
- Downloads: readings from 2019-2020 ordered results primarily by downloads and ratings and had Apple weigh about one week of download data; every reading from 2022 on says Apple does not use downloads directly. Use the ratings model, treat download estimates as a proxy, and keep Apple's listing of downloads as the other side.
- Star average: a 2020 reading found top results carry a higher average as well as a higher count; the 2022 and every 2025-2026 reading say the average is ignored. Do not plan rank around the average.
- Placement in the name beats raw ratings across an order of magnitude (observed). "Learn French in 31 days" is number one for "learn French" with 200 ratings against Duolingo's 102,000; an app with 13 ratings is fourth for "subscription manager" (popularity 56) while Rocket Money's 13,000 ratings rank it from a subtitle. Page-two apps share one mistake: the keyword at the end of the name.
- Subtitle-only placement needs about two orders of magnitude more ratings than name placement to compete (rule of thumb).
- Product page conversion (views to downloads) is a ranking input, sometimes large, separate from ratings (observed 2025). A bad rate is not penalized, but better converters get a boost that lifts only already-competitive apps. Apple names downloads, not conversion rate, among its inputs. Treat conversion as a secondary input.
- Most ranking failures are metadata failures (duplication, brand first, no focus), not authority gaps. Diagnose metadata first.

## Indexed fields and weights

- Limits (Apple-documented): name 2-30 characters, subtitle 30, keyword field 100 bytes in App Store Connect Help (100 characters on Apple's developer pages), each keyword longer than two characters. The 100 characters hold roughly 10 to 12 English words; in multibyte scripts the byte limit holds far fewer.
- Weight runs name, then subtitle, then keyword field, and left to right inside each field (observed, held 2019-2026; Apple documents no field order). (contested) One mid-2026 reading puts subtitle and keyword field roughly equal; every other reading keeps the strict order. Place the second-best term in the subtitle either way.
- Weight is a fixed 100% split across every word you provide: fewer words means more weight each, and empty characters cost nothing (rule of thumb). The direction is confirmed independently since 2019; the fixed-split arithmetic is a model, not a measurement. Apple's advice is framed as fitting more words in, never as filling the field.
- Category and company name are indexed from their own fields (Apple-documented), so neither belongs in the keyword field. Very generic queries such as "games" are filled from category ranks (observed). Apple recommends researching how similar apps are categorized before choosing; the primary category decides browse placement, search filtering and the Apps or Games tab, and an irrelevant category is grounds for rejection (Apple-documented).
- Screenshot captions are a fourth surface since mid-2025, reinforcing only (observed). See the timeline below.

## Word combination within a localization

- Words combine across name, subtitle and keyword field within one localization, so a phrase never needs spelling out (observed; Apple does not describe cross-field combination). "Scanner" in the name plus "LiDAR" in the subtitle matches "LiDAR scanner".
- A competitive multi-word term split between name and subtitle still indexes, at lower relevance, and ranks only with momentum. Keep a term you must win contiguous in the name.
- Word order inside a phrase matters (observed 2022, not re-tested since): "app analytics" and "analytics app" are different keywords to the index. Write a phrase in the order people type it.
- Localized keywords are searchable wherever their language is supported in a storefront (Apple-documented), but words never combine across localizations (observed). See `references/localizations.md`.

## Token rules

- Word breaks: hyphens, colons, dashes, ampersands and spaces.
- Joined words are one token. "StepTracker" and "everyday" do not yield "step", "tracker", "every" or "day".
- Plurals of included words are duplicates (Apple-documented). Stemming covers English plurals only (observed): "tracker" and "tracking", "read" and "reading" are separate words, and other languages may index plurals separately. Pick the form people type, and track singular and plural as separate keywords in your rank tracker.
- Apple's leave-out list (Apple recommends): "app", "game", filler words such as "the" and "to", words already in the name, subtitle or category, the company name, and special characters such as # or @ unless part of the brand, since they carry no extra weight. Words of two characters or fewer are not valid keywords (Apple-documented).
- The fuller English stop-word list (dated: 2019, observed): articles, pronouns and prepositions, plus "more", "most", "only", "own", "same", "very", "few", "all", "any", "other", "such", "up", "down", "over", "under", "out", "off", "about", "after", "before", "again", "once", "further", "through", "between" and "against"; "best" is ignored. Lists for other languages are not published; assume their articles and prepositions.
- Rejection reasons (Apple-documented): unauthorized trademarks, celebrity names and other protected words, competing app names, irrelevant or offensive terms, pricing information (which covers "free"), "For Kids" outside the Kids category, "AR" without AR features. "HD" and "for iOS" are not on Apple's list; they waste characters (rule of thumb).
- Phrase entries with internal spaces are valid in the keyword field (Apple-documented). Valid is not useful: words already combine, so a phrase entry spends characters on a space. Use one only to route an organic custom product page (`references/custom-product-pages-and-events.md`).
- Special characters and the 30-character window (observed 2022, unconfirmed since): "&" and ":" count as one character in App Store Connect but as two to the search index, which reads only the first 30 characters of the name or subtitle. Leave one character unused per special character, or avoid them. Apple says only that special characters carry no extra weight. Whether this is the October 2025 title truncation bug is unknown.
- Misspelling normalization (observed 2022): an app with "fltr" in its name ranked at the top for "filter". Which words get normalized is unpredictable; never rely on it. Apple documents spelling variations only for Apple Ads exact match.
- Repeats: Apple recommends not repeating name, subtitle or category words in the keyword field. That a repeated word keeps only its last instance is observed, not documented. (contested) Whether the repeat is a penalty or just wasted characters is unsettled: one 2022 reading says all but the last instance are ignored, another that duplication has been penalized with lower ranks since 2022. Either way the repeat loses position. Rules in `references/metadata-writing.md`.

## What is not indexed

- The description: not an App Store search field (Apple-documented), and consistent with rank data 2021-2026. WWDC 2025 announced App Store Tags generated from metadata that includes the description, not description indexing. Two 2019 readings that list the description among indexed fields describe Google Play. Write it for people and for web search.
- Promotional text (Apple-documented: no effect on ranking).
- App Preview video captions (observed June 2025), custom product page screenshots and product page optimization treatments (observed 2026; Apple says treatments may appear in search like the original and says nothing about indexing).
- Review text is not a ranking input on the App Store (observed; Apple says "ratings and reviews can influence" rank without saying whether text is read). Google Play reads review text for keywords (observed 2022).
- In-app purchases and events: search uses in-app purchase metadata, promoted purchases can appear in results (consumables never), and in-app events are searchable by name (Apple-documented). Whether they rank the app itself for other queries is undocumented; do not plan app keywords there.
- Header and search result asset text (iOS 27, open to all developers in October 2026): Apple documents the assets, not indexing. Plan no keywords there.

## Screenshot captions since mid-2025

- February and April 2025: no screenshot text indexing found (observed).
- Early June 2025: within a week, apps moved sharply up or down depending on whether their captions already carried keywords aligned with name, subtitle and keyword field (observed). Apple said screenshots feed App Store Tags. Caption-only keywords ranked as a weaker signal, and June-July 2025 advice was to introduce new keywords through captions. Superseded.
- From October 2025: captions reinforce keywords already in the metadata, add none, and weigh less than name or subtitle (observed). Use this reading.
- December 2025: the reported "algorithm change" was continued tuning of screenshot reading.
- Fall 2026, iOS 27: screenshots read more intelligently, with uneven rank shifts around the transition (observed).
- Caption rule: `references/metadata-writing.md`. Design: `references/screenshots-and-product-page.md`.

## Index memory

- Removed keywords persist at reduced strength, and resubmitting an app keeps its history (observed).
- Changing the name to a new keyword transfers no weight; only ratings carry over.
- An existing rank, even at 99 or 147, proves the index already judged the app relevant, and is easier to lift than a new term. See `references/keyword-research.md`.

## Visibility

- Results start between rank 3 and 5 on the screen. Attention drops sharply outside the top 5 and becomes very small outside the top 10 (observed 2019-2020), so a top-5 rank on a modest keyword is worth more than a poor rank on a popular one. Below 10 is invisible.
- A search result shows up to three screenshots, or the preview, unless a search result asset replaces them since iOS 27, which a custom product page can tailor per keyword (Apple-documented).
- An in-app event card replaces the screenshots in search only for people who downloaded the app before, and for anyone searching the event itself (Apple-documented); everyone else sees screenshots. The "about two slots" reading (observed) applies to past downloaders. Promoted purchases and in-app events have taken more room since April 2025.
- Since the second Apple Ads placement in early March 2026, ads sit at positions one and three (observed; Apple documents ads at the top or further down, with no slot number, and no way to choose or bid for a position). Target top 3, not top 10.
- As of January 2025 Apple's own apps rank almost always number two for their head term (observed). Treat that rank as untakeable.

## Ranking inputs and non-inputs

Inputs:

- New ratings in the last 30 days in that storefront (observed; Apple documents ratings as an input and the rating as per territory, not the window). Downloads per rating is downloads in the last 30 days divided by new ratings in the same 30 days, lower is better (defined 2022); ideal 1, under 30 good, above 100 ugly (rule of thumb). 10 to 20 more ratings can move rank 5 to 1 or 2 in a thin niche; below rank 20, one rating a week shows. Strategy in `references/ratings-and-reviews.md`.
- Keyword placement (name over subtitle over keyword field, left over right; observed).
- Downloads (Apple-documented as an input; contested in how they count, see above).
- Product page conversion, secondary (observed).
- Adoption of new Apple features (observed 2022, lift at launch; current status unknown): apps promoting an in-app purchase or running in-app events, and games with Game Center, ranked better than their ratings justified. Apple documents no boost and says event priority does not affect ranking against other apps. Adopt them for conversion and result space, not for rank.
- The new-app boost: about 7 days, described as fact in 2021 and paying only when keywords are set before launch; reported changing in March 2025 and mostly gone by September 2025. Do ASO before launch.

Not inputs:

- Promotional text and in-app event priority (Apple-documented).
- Retention, usage, crashes (little), traffic source, preview video, custom product pages, updates without metadata changes (observed). Google Play uses all-time downloads, uninstalls, crashes and retention; do not carry Play logic to the App Store.
- Apple Ads conversion rate and Apple Ads spend (observed). Apple mentions view-through installs as a possible organic effect within 24 hours and makes no ranking statement; the observed path to organic rank is the ratings that paid installs produce.
- Farmed or early-prompted ratings. Manipulating charts, search or reviews is discovery fraud under Guideline 5.6.3 (Apple-documented). Apple has removed fake ratings since at least 2022, in August 2026 deleted ratings prompted too early (observed), and rank rebuilds slowly after a penalty.

## Earlier history

- Before 2019: the algorithm moved from rewarding packed names and subtitles to rewarding focus.
- 2019-2022: the popularity baseline the fall 2025 re-normalization moved away from: a third-party 5-100 scale (one reading says 1-100) where most of about 11,000 US keywords scored 10-40. Apple Ads itself shows Search Popularity on a 1-5 scale. Details in `references/keyword-research.md` and `references/data-inputs.md`.
- 2020 to April 2023: the US storefront's searchable localizations grew from English plus Spanish (Mexico) to ten; Apple's 2026 storefront table lists the same ten. The set is in `references/localizations.md`.
- June 2021, WWDC: custom product pages (35 per app then) and product page optimization announced for iOS 15; icon and preview treatments were testable from the start.
- 2022: duplication across fields became a penalty (one reading); the special-character bug was found; Apple was seen removing fake ratings.
- February 2023: Apple's keyword-field checklist (commas without spaces, no app name, category or plurals), still current.

## What changed in 2025-2026

- Early 2025: more apps ranked across more keywords; the keyword field became more influential; Apple's own apps moved to number two.
- March to September 2025: the roughly 7-day new-app boost reported changing, then mostly gone.
- April 15, 2025: Apple Search Ads renamed Apple Ads; promoted purchases and in-app events take more room in results.
- Before May 2025: pre-orders stopped surfacing in search. Bring your own pre-order traffic.
- June 9, 2025, WWDC: App Store Tags (drawn from metadata such as description, category and screenshots), keywords for custom product pages and review summaries announced. In the first week of June, screenshot text became a ranking input (observed), narrowed to reinforcement by October.
- July 29-30, 2025: custom product pages attachable to organic keywords for iOS 26, observed as limited to the main locale's keyword field; Apple's current documentation selects keywords per localization, from the latest approved version.
- Late September to October 2025: the third-party popularity score re-normalized, many keywords fell to 5 or below 10.
- Around November 2025: custom product page cap raised from 35 to 70, now Apple-documented as 70 per app.
- Early March 2026: second Apple Ads placement, ads at positions one and three; organic visibility about top three; cost per tap up.
- June 8, 2026, WWDC: product page headers and search result assets announced for iOS 27, opened to all developers in October 2026; indexing undocumented.
- August 2026: ratings prompted too early deleted (observed).
- November 2026 (Apple documentation): tags still US-only; review summaries in the US plus eight English storefronts; Personalized Collections in select countries.

## Checks

- Every target query's words exist in name, subtitle or keyword field of one localization, with no word split across localizations.
- The term you most need to win sits contiguous at the start of the name, in the order people type it.
- No word appears twice across name, subtitle and keyword field; no plural next to its singular; no category or company name in the keyword field.
- No joined words standing in for two keywords; no stop words, no words of two characters or fewer, nothing on Apple's rejection list ("free" and other pricing, trademarks, competing app names, celebrity names).
- The keyword field fits 100 bytes in multibyte localizations, not only 100 characters.
- A full-length name or subtitle that uses "&" or ":" leaves one spare character per special character.
- No keyword plan depends on the description, promotional text, preview video, custom product page screenshots, treatments or header assets being indexed.
- Competitor comparison uses new ratings in the last 30 days in that storefront, not lifetime totals, star average or download estimates.
- Every claim about downloads or star value as a rank input states both Apple's list and the observed model.
- Visibility target is top 3 (since March 2026), and an Apple first-party app in the results is counted as an untakeable slot.
- A missing metadata change is not judged before 24 hours.

## Open questions

- Weights: Apple lists text relevance, downloads, and the number and quality of ratings and reviews without weights or windows. How downloads count, what "quality" means, and whether the 30-day window is exact are all unmeasured.
- Screenshot indexing mechanics: how much of the image is read, whether caption-only words still index as they did in June 2025, what iOS 27 changed, and whether header and search asset text is read.
- App Store Tags: Apple says they improve relevance; no rank effect is measured, and they were misaligned in beta (September 2025).
- Subtitle versus keyword field weight: below versus roughly equal (contested).
- Which text-relevance fields Apple means: its pages list them differently (with or without the subtitle).
- The special-character double-counting bug (2022) has no confirmation or retraction since. Word order inside a phrase and misspelling normalization rest on single 2022 observations.
- The 2022 boosts for promoted in-app purchases, in-app events and Game Center: lift at launch confirmed, current status unknown; Apple documents none.
- No quantified ratings-to-rank formula exists; only the rules of thumb above.
- Whether LLM-driven discovery or Personalized Collections send measurable installs: no data.
