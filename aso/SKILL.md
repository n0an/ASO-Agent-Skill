---
name: aso
description: Audits, plans and writes App Store Optimization for iOS apps - App Store Connect metadata (name, subtitle, keyword field, localizations), keyword research and winnability tests, screenshots and product page assets, custom product pages and in-app events, ratings strategy, Apple Ads, Meta app campaigns (Advantage+ app campaigns, optimization goals, AEM and SKAdNetwork measurement) and their fit with organic search, the App Tracking Transparency prompt and what consent changes for attribution, competitor research, and measurement of changes. Use when asked to improve App Store visibility or conversion, pick or audit keywords, write or review store metadata, plan or critique screenshots, set up or review Apple Ads or Meta app campaigns, write or review the ATT prompt, reconcile installs across Meta, Apple Ads and App Store Connect, or diagnose why an app is not ranking or not converting.
license: MIT
metadata:
  author: Anton Novoselov
  version: "1.0.0"
---

Do App Store Optimization work for an iOS app the way a careful practitioner would in 2026: diagnose from the app's own data, change one thing at a time, and judge results on the right clock. Every rule in `references/` is dated and labeled by how well it is known, because the App Store changed several times in 2025-2026; check the date on a rule before applying it.

Five facts the rest assumes:

1. Search has two stages. The words in the name, subtitle and keyword field of any indexed localization decide which queries an app is eligible for. Inside that set, apps are ordered mainly by new ratings in the last 30 days in that storefront and by where the keyword sits (name beats subtitle beats keyword field) (observed). Apple documents the inputs but not their weights: text relevance, user behavior such as downloads, and the number and quality of ratings and reviews (Apple-documented).
1. Placement beats volume: an app with 200 ratings and the term first in its name outranks one with 100,000 ratings that carries the term in a subtitle (observed). Most "we don't rank" cases are metadata mistakes, not authority gaps.
1. Visibility is the top three since March 2026, because two of the top results are paid.
1. Downloads from any channel, paid or organic, move organic rank mainly through the ratings they produce (contested: rank data points to ratings as the lever, while Apple lists downloads as an input in their own right). Product page conversion is a secondary input.
1. Indexing reacts within hours; ranks settle over 2-3 weeks. Never judge a change in days, never change metadata more often than every 2-3 weeks.

Audit process (run it when asked to review, audit, or "take a look at" a listing; load the reference named at each step, skip steps the user ruled out):

1. Collect inputs using `references/data-inputs.md`: current metadata for every localization, impressions, product page views and downloads by source for the last 3 months, current ranks for the terms the app cares about, and the top 5 results for each of those terms with their rating counts. If a tool for one input is not connected, say which step is degraded and use the manual fallback. If a data tool is connected, scope every request to the app, store, country and time window, run the requests in the order given in `references/data-inputs.md`, and ask for the numbers behind each answer; use the tool for lookups only, since winnability, metadata wording and bids follow the references, and any change to an account waits for the user's explicit yes.
1. Check the metadata for mechanical faults using `references/metadata-writing.md`: words repeated across name, subtitle and keyword field; brand first or keyword last in the name; phrases or spaces in the keyword field; stop words, words under three characters, trademarks; a missing subtitle; joined words standing in for two keywords.
1. Check eligibility and placement for each target term using `references/fundamentals.md`: is every word of the term indexed in one localization, and is the term the app most needs to win contiguous at the start of the name?
1. Judge each target term's winnability using `references/keyword-research.md`: popularity on the current scale, the top-5 test (do positions 3-5 carry the term in their name, how many new ratings in 30 days), then difficulty as a tiebreaker.
1. Check the localizations using `references/localizations.md`: which indexed localizations are used, whether each has one focus, whether words are duplicated across them for no reason, whether a non-English localization still carries parked English keywords that a real translation would lose.
1. Read the funnel using `references/measurement-and-cadence.md`: impression-to-view and view-to-download by source; decide whether the problem is visibility or the page. App Store Connect's own conversion rate is downloads over unique impressions, a different ratio from view-to-download; never compare one against a benchmark for the other.
1. If the page is the problem, review screenshots, icon, preview and description using `references/screenshots-and-product-page.md`.
1. Check the ratings flow using `references/ratings-and-reviews.md`: downloads per rating, where and when the prompt fires, what Apple would delete.
1. If the app runs paid traffic, check how it meets organic using `references/apple-ads.md` and `references/meta-ads.md`: custom product pages per keyword theme, Search Match, brand bidding, how paid traffic shows up in App Store Connect sources. If Meta campaigns run, check their setup and measurement with `references/meta-campaigns-and-measurement.md`; if the app shows the ATT prompt or relies on ad attribution, check it with `references/app-tracking-transparency.md`.
1. If custom product pages or in-app events exist or are planned, check them using `references/custom-product-pages-and-events.md`.
1. Catch what the checklists miss using `references/anti-patterns.md`.
1. Write the findings in the Output Format below and append a dated entry to the change journal before anything ships.

If doing partial work, load only the relevant reference files.


## Task-based routing

Match the user's goal to the read order. Load only what you need.

### "Audit my listing" / "why don't we rank"
1. The audit process above, in order
2. `references/anti-patterns.md` - the common causes of a flat or falling rank

### "Pick keywords" (new app, rename, or a new feature to promote)
1. `references/keyword-research.md` - the research waterfall, the top-5 test, relevance and intent
2. `references/competitor-research.md` - where the candidate terms come from
3. `references/fundamentals.md` - eligibility and placement rules the plan must respect
4. `references/localizations.md` - where surplus focuses go

### "Write or rewrite the name, subtitle, keyword field"
1. `references/metadata-writing.md` - the writing rules and worked examples
2. `references/fundamentals.md` - token rules (word breaks, plurals, stop words)
3. `references/custom-product-pages-and-events.md` - only if an organic custom product page needs a phrase entry in the keyword field

### "Plan localizations"
1. `references/localizations.md` - the indexed set, one focus per localization, the launch blueprint
2. `references/keyword-research.md` - which focus deserves its own localization

### "Review / design screenshots, icon, preview"
1. `references/screenshots-and-product-page.md` - sequence, captions, visual rules, icon, video, testing
2. `references/metadata-writing.md` - the caption reinforcement rule (which words to repeat)
3. `references/measurement-and-cadence.md` - how to tell a page problem from a visibility problem first

### "Set up custom product pages or in-app events"
1. `references/custom-product-pages-and-events.md` - limits, paid vs organic pages, the keyword-field attachment rule, page design, events
2. `references/apple-ads.md` - one page per keyword theme in ads
3. `references/screenshots-and-product-page.md` - screenshot order for a page

### "Get more ratings" / "our rank is stuck"
1. `references/ratings-and-reviews.md` - the 30-day currency, when to prompt, benchmarks, what Apple deletes
2. `references/fundamentals.md` - what ratings can and cannot do without placement

### "Set up or review Apple Ads"
1. `references/apple-ads.md` - placements, budget, structure, match types, bids, creative, reading reports
2. `references/keyword-research.md` - the same winnability logic picks ad keywords
3. `references/custom-product-pages-and-events.md` - the landing page per theme

### "Review our Meta app-install campaigns"
1. `references/meta-ads.md` - creative-led targeting, page alignment, how Meta shows up in App Store Connect
2. `references/meta-campaigns-and-measurement.md` - campaign type, optimization goal and events, learning phase, bids, limits, AEM and SKAdNetwork
3. `references/ratings-and-reviews.md` - turning paid installs into the ratings that rank

### "Set up a Meta app campaign" / "Meta and App Store Connect numbers don't match"
1. `references/meta-campaigns-and-measurement.md` - the launch procedure and the reconciliation procedure
2. `references/app-tracking-transparency.md` - what consent changes for attribution
3. `references/measurement-and-cadence.md` - App Store Connect's side of the numbers

### "Write or review the ATT prompt" / "do we even need ATT"
1. `references/app-tracking-transparency.md` - whether the app tracks, Apple's pre-prompt rules, purpose string, timing, opt-in rates
2. `references/ratings-and-reviews.md` - the parallel rule for the rating prompt, and where both sit in onboarding

### "Research competitors"
1. `references/competitor-research.md` - who to study, what to read, gap analysis, growth signals, positioning
2. `references/keyword-research.md` - scoring the terms you find

### "Did our change work?" / "our rank dropped"
1. `references/measurement-and-cadence.md` - the clock, the funnel, diagnostics, when to revert
2. `references/data-inputs.md` - what the numbers mean and their traps


## Decision trees

Quick orientation when you know the task but not the rule.

### Where does this keyword go?

```
Is it the one term the app most needs to win?
  -> first in the name, contiguous, brand after it (short)

Second-best term, or a modifier of the first?
  -> subtitle (do not repeat any name word)

Long-tail word that combines with name or subtitle words?
  -> keyword field, single word, no spaces, no repeats of name or subtitle words

Whole phrase that must trigger an organic custom product page?
  -> keyword field as one comma-separated entry (Apple picks page keywords per
     localization; the main localization is the observed safe choice), and only
     if you can rank for it or pay for it

A different focus the English set cannot carry?
  -> another indexed localization, with the focus word in that localization's name

Already in name or subtitle and you want to reinforce it?
  -> screenshot captions, about three times across the first three screenshots
```

### Is this term winnable?

```
Popularity on the current (post fall 2025) scale is 5-9 and the term would lead the name?
  -> no; use such terms only as supporting field words, many of them

Positions 3-5 all carry the term in their name and earn far more new ratings in 30 days than you can?
  -> no for now; pick a longer-tail or an adjacent term

Positions 3-5 hold the term only in subtitles or keyword fields, or earn few new ratings?
  -> yes; put it first in the name and build ratings velocity

You already rank 50-150 for it?
  -> yes, cheaper than a new term; fix placement and ratings
```

### Custom product page or product page optimization?

```
Different audiences or traffic sources need different stories?  -> custom product page per theme
Same audience, you want to know which creative converts better? -> product page optimization test
Testing the icon?                                                -> product page optimization (icon variants must already be in the live binary)
Need to control what Apple Ads traffic sees?                     -> custom product page (tests exclude custom page visitors; Apple does not say whether default-page ad taps enter a test)
```

### Apple Ads or Meta?

```
Need to learn which keywords convert, or defend a term you almost rank for?  -> Apple Ads, one week, low budget
Need volume beyond what search demand allows, and have creative to test?    -> Meta app-install campaigns
Either way: installs lift organic rank mainly through ratings (contested); plan the rating prompt before scaling spend
```


## Core Instructions

- Scope: the iOS App Store first; mention Google Play only where a rule differs and the user asked. Apps, not games. Knowledge is current to November 2026; platform facts carry their dates, and when a date-dependent rule matters, say so and recommend re-verifying against App Store Connect or Apple's documentation.
- Scope boundary: the skill decides and reviews campaigns, prompts and measurement; it does not walk through SDK integration, server-side event code or Events Manager click paths. Say so when asked, and limit the answer to what the setup must achieve.
- Tool-agnostic: the references name the data a step needs, never a product. Use whatever keyword research, rank tracking, market intelligence or attribution tool the user has connected; fall back to the manual checks in `references/data-inputs.md`. Never tell the user which tool to buy.
- State the status of a rule when it changes the decision: "(rule of thumb)", "(observed)", "(Apple-documented)", "(contested)". When a rule is contested, give both sides and the dates; never flatten it.
- On mechanics, limits, definitions and review rules, Apple's current documentation wins over numbers observed in the field. On ranking weights, conversion lifts and bidding strategy Apple is silent, and the observed rules stand. Apple's advice ("Apple recommends") is not a mechanic; where it contradicts a tested rule, give both.
- **Never** repeat a word across name, subtitle and keyword field; only the last instance counts and the word drops to the weakest position. A plural next to its singular is a repeat.
- **Never** remove an existing subtitle, and never ship without one.
- **Never** put phrases, spaces after commas, "app", "free", "for iOS", "HD", stop words, words under three characters, the category name or another company's trademark in the keyword field. Single words, commas, no spaces. The one exception: a whole-phrase entry that routes an organic custom product page (Apple lets you pick a page's keywords per localization; the main localization is the observed safe choice).
- **Never** lead the name with the brand unless people search the brand by name; the most valuable searched term goes first and contiguous, the brand last and short.
- **Never** fill the fields for the sake of it; two or three strong terms beat 100 characters of weak ones, because weight is a fixed split across every word you provide.
- **Never** judge a keyword change before two weeks, never change metadata more often than every two to three weeks, and never revert the next day except for a critical rank such as number one dropping (contested; see `references/measurement-and-cadence.md`).
- **Never** compare popularity values across the fall 2025 re-normalization, and never use a difficulty score as a pass or fail threshold without the live top-5 test.
- **Never** plan keywords in the description, promotional text, preview video or custom product page screenshots; none of them index. Screenshot captions reinforce metadata keywords but add none.
- **Never** prompt for a rating in the first session or inside onboarding without a clear success moment; Apple deletes ratings prompted too early (August 2026) and rank rebuilds slowly after a penalty. Use only the system prompt, at most three times in 365 days; custom review prompts, rating gates and rewards for a rating break App Review Guidelines 5.6.1, 3.2.2 and 5.6.3 (Apple-documented).
- **Never** read a rise in "App Store Search" as organic growth while Meta spend is rising; view-through users search the brand.
- **Never** leave Search Match on in an Apple Ads campaign whose search-term report you have not read, and never bid on a competitor's brand without flagging it as contested.
- When words must combine into a phrase, keep them in one localization; words never combine across localizations. Give each extra localization one focus, with the focus word in that localization's name.
- When an app must win a competitive multi-word term, keep it contiguous in the name; a split between name and subtitle ranks only with momentum.
- When an app already ranks 50-150 for a term, lift that term before adding new ones; an existing rank proves relevance.
- When paid traffic runs, fix the rating prompt before scaling spend; installs reach organic rank mainly through ratings (contested), counted per storefront, so ratings-driving campaigns run one country at a time.
- Every proposed change comes with a dated change-journal line; without the journal, no rank movement can be attributed later.


## Output Format

If the user asks for an audit or review, organize findings by area (name and subtitle, keyword field, localizations, screenshots and page, ratings, paid), ordered by expected effect. For each finding:

1. State what is there now (the exact text or number).
2. Name the rule or anti-pattern it breaks, with its status label.
3. Give the fix as the exact new text or the concrete action.
4. Say when it can be judged (the date two to three weeks after the change ships).

Skip areas with no issues. End with a prioritized summary and the change-journal lines the user should record.

If the user asks you to write metadata, write it directly: show character counts per field, list every word once with the field it lives in, and show the duplication check passing. If the user asks for a keyword plan, give one row per term: popularity with the date it was read, the top-5 test result, the intended placement, the localization it lives in.

Example output:

### Name and subtitle

**Name: "Acme: Identify Plants Fast" - brand first, most valuable term split and last (observed rule: weight falls left to right).**

- Now: brand leads; the searched phrase "plant identifier" never appears contiguously.
- Fix: `Plant Identifier - Acme` (23 characters). "Identifier" becomes the hub noun that combines with "flower", "tree" and "weed" from the keyword field.
- Judge on 2026-12-01 (three weeks after the 2.4 release) by rank for "plant identifier" and "flower identifier" in the US storefront.

### Keyword field

**`plant id, flower identifier, leaf scan,garden,plant care,app,identify plants,weeds` - phrases, spaces after commas, "app", "plant" repeated three times, "identifier" duplicates the name (rule of thumb, repeats keep only the last instance).**

- Fix: `flower,leaf,tree,weed,garden,care,species,botany,succulent,mushroom,scanner,disease` (83 characters, 12 single words, 17 free for the next round). "plant" and "identifier" stay in the name only.
- Judge on 2026-12-01.

### Summary

1. **Name order (high):** move the searched term first and keep it contiguous; the only lever that beats rating gaps.
2. **Keyword field hygiene (high):** removes the repeats and the dropped word "app", and adds seven new terms.
3. **Ratings flow (medium):** 3,000 installs a month against 15 ratings is 200 downloads per rating; fix the prompt before any paid scaling.

Change journal: `2026-11-10 2.4 - name changed to "Plant Identifier - Acme"; keyword field rebuilt (12 single words); judge 2026-12-01.`

End of example.


## References

- `references/fundamentals.md` - the two-stage model, indexed fields and weights, word combination, token rules (word breaks, plurals, stop words), what is not indexed, screenshot captions since mid-2025, index memory, visibility slots, ranking inputs and non-inputs, the dated 2025-2026 change log.
- `references/keyword-research.md` - the search popularity score and its fall 2025 re-normalization, difficulty, the top-5 winnability test, the research waterfall from competitors' organic keywords, intent and relevance, "AI" as a token, pruning.
- `references/metadata-writing.md` - name, subtitle and keyword field rules with worked examples: keyword first and brand last, hub nouns, one idea per metadata set, do not fill the fields, the no-repeat rule and its exceptions, keep a subtitle, the organic custom product page exception, the caption reinforcement rule.
- `references/localizations.md` - the storefront's indexed localizations as extra keyword budget, no combination across localizations, one focus per localization, the launch blueprint, device language and what the searcher sees, parked English keywords versus real translation.
- `references/screenshots-and-product-page.md` - sequence and story, captions at thumbnail scale, visual rules, icon (contested lever), preview video, description and promotional text, the iOS 27 header and search assets, product page optimization tests, conversion benchmarks.
- `references/custom-product-pages-and-events.md` - the 70-page limit per app, pages for paid traffic, pages for organic keywords since iOS 26 and the keyword-field attachment rule, page design, in-app events, pages versus product page optimization, approval and attribution limits.
- `references/ratings-and-reviews.md` - ratings as the ranking currency (count, 30 days, per storefront, velocity), ratings as social proof, when and how to prompt, downloads-per-rating benchmarks, review text and replies, what Apple removes.
- `references/apple-ads.md` - placements and the auction since March 2026, budget and scaling, campaign structure and match types, Search Match, negative keywords, keyword choice from organic ranks, bids over time, custom product pages per theme, reading TTR, CPT, CPA and impression share, Apple Ads and organic rank, brand bidding.
- `references/meta-ads.md` - who Meta app campaigns suit, creative-led targeting, ad-to-page alignment and destinations, how Meta traffic shows up in App Store Connect, campaign and goal choice in brief, web-to-app versus app install, Meta Ads and organic rank.
- `references/meta-campaigns-and-measurement.md` - Meta's own rules for iOS app campaigns: Advantage+ app campaigns and their targeting limits, optimization goals and event requirements, the learning phase, budgets and bid strategies, account limits, AEM and SKAdNetwork, what Ads Manager reports, launch and reconciliation procedures.
- `references/app-tracking-transparency.md` - whether an app needs the ATT prompt, the system prompt and purpose string, Apple's pre-prompt rules, copy and timing, opt-in rates, what consent changes for attribution, enforcement beyond the prompt.
- `references/competitor-research.md` - which competitors to study, reading a listing, keyword gap analysis, growth signals readable from outside, review mining, positioning.
- `references/measurement-and-cadence.md` - the funnel by source, the clock, change cadence, reverting, diagnostics, the one-week Apple Ads conversion test, reading sources with paid channels running, rank noise, the change journal.
- `references/data-inputs.md` - what every step needs (popularity, ranks, difficulty, top results, 30-day ratings, competitor keywords, metadata per localization, funnel numbers, ad reports, attribution), where each comes from, how to read it, manual fallbacks.
- `references/anti-patterns.md` - the mistakes that recur in real listings and campaigns, each with the fix.
