# Keyword research

Keyword research picks the terms whose searches you can win: enough demand to matter, results shallow enough to enter, and a searcher your app satisfies. Two numbers drive it: a search popularity score (relative demand; research tools show 5-100 on a log scale, Apple Ads shows 1-5) and a difficulty estimate derived from the apps already ranking. Neither is a threshold; the decision is always made against the new ratings and name placement of the apps in positions 3 to 5. Scope every number to one store and one country before you start, because the same term differs wildly between the App Store and Google Play and between storefronts. This file assumes the indexing model in `references/fundamentals.md`.

## The popularity score

- Two scales exist; never mix them. Apple Ads documents Search Popularity in its keyword recommendations and reports as 1 to 5, with 5 the most popular (Apple-documented). Keyword research tools show a 5-100 score on a log scale, described as derived from Apple Ads data, app-independent and therefore identical across tools, mobile searches only (observed; Apple documents no 5-100 scale, so its derivation is unverified). On the 1-5 scale a 5 is the top band; on the 5-100 scale a 5 is the floor.
- Every number in this skill uses the 5-100 scale. On it, 5 means little to no searches, "Instagram" scores 100, and a 0 is rare and means the index does not understand the term at all. Readings from 2019-2020 gave the range as 1-100; the 5 floor is current. When a user quotes a popularity from Apple Ads directly, ask or check which scale it is before applying any band.
- The scale was re-normalized in fall 2025 (late September to October). (contested) An October 2025 reading called the mass drop to 5 an accidental flip that would recover, while a March 2026 reading called it deliberate: 100 stays pinned to a growing top term, so many keywords fell below 10 and old thresholds are now too high. Treat the March 2026 reading as current.
- Observed since the renormalization: spring 2026, a 5 "now gets some traffic"; September 2026, "a 17 is not terrible these days"; November 2026, rising scores mean real demand.
- The baseline the scale moved from (dated: 2019-2022): in a study of about 11,000 US keywords most scored 10-40, single digits were treated as noise, and opportunity filters started at 10. Bands from 2025 before the renormalization (rules of thumb): long tail 20-25, not below 20 unless forced; 10-30 for a brand-new app; 18-28 "perfect"; 30 "pretty good". Do not apply any of these to a current score; use them only to read older data.
- No fixed threshold exists. Judge popularity against the 30-day ratings of the top results (the opportunity test below).
- Popularity does not convert to downloads. Estimate revenue from what the ranking apps earn. Even a 5 can mark a paying market: the top 10 "doom scrolling" apps earn about 300,000 to 342,000 dollars a month in the US. The floor still holds: being first for a keyword nobody searches is a total waste.
- Single-digit popularity. (contested, dated) Readings from 2019-2020 avoided single digits outright: any keyword not in the single digits was usable, and if every candidate was single-digit you went back and generated more ideas. Readings from 2025-2026, after the renormalization pushed real keywords into single digits, treat many 5s, 6s and 7s summed as able to match one bigger keyword. Current rule: fives are a start, not a strategy; a keyword scoring 5 to 9 never leads the name; if your whole list is single-digit, widen the research before writing metadata.
- Intuition about demand is wrong often, even for experts. "step counter" scores 59 and "steps counter" 5; "power nap" scored about 25 where 5 was expected. Look up every term and every form of it.
- Apple frames the same trade-off without numbers (Apple recommends): popular functional terms such as "jobs" or "social" and trending or seasonal terms such as "Christmas" or "summer" drive a lot of traffic but are highly competitive, especially for newer or smaller apps, while less common terms drive less traffic against less competition. Apple gives no bands and no ratings test; those stay rules of thumb.
- Head terms are hard but not locked. "weather" scores 72 and "Bible" 73 with difficulty 94, "zero chance from a subtitle". Yet "learn French" (55) is held at number one by an app with 200 ratings against 102,000, because the phrase leads its name. A head term is locked only for apps that carry it outside the name.

## Difficulty

- The difficulty estimate is a composite of the top 10 results' downloads, category rank, ratings and age (some tools add keyword density). It is good for comparing many terms fast and has no safe absolute threshold. Below 80 or 85 means nobody competes.
- Use it as a tiebreaker after the ratings check, never as the first filter. Make the final call on the actual values of the ranking apps.

## What decides rank inside the eligible set

The opportunity test below rests on these inputs. The full model is in `references/fundamentals.md`.

- Apple-documented: results rank on text relevance and on user behavior, "downloads, ratings and reviews, and more". Ratings and reviews influence search rank, and the summary rating shown in results is specific to each territory. Apple publishes no weights, windows or thresholds.
- Tested: after eligibility, the strongest measured lever is new ratings in the last 30 days in that storefront, plus name placement. Apple documents no 30-day window; it is reverse-engineered.
- (contested) Downloads: Apple lists them as a factor; tests since 2022 find that download volume without new ratings barely moves rank. Keep 30-day ratings as the yardstick and read download estimates as a secondary check, not as irrelevant.
- (contested) Star value: Apple names "the number and quality of ratings and reviews" as a factor; tests since 2022 find the star average does not move rank. Apple does not define quality. Do not plan rank around the average, but do not tell a user it never matters.
- Not inputs (Apple-documented): promotional text, and in-app event priority, which picks which event shows for the app but does not change ranking against other apps.
- Other result content (Apple-documented): search uses in-app purchase metadata; promoted in-app purchases can appear in results, consumables never do; in-app events are searchable by name. In results for an app search, the event card shows only to people who downloaded the app before. Which fields of a purchase or event are matched is undocumented, so plan no keywords around them.
- App Store Tags (Apple-documented, since WWDC 2025): terms shown in US search results and on product pages, generated from the en_US metadata, deselect-only; deselecting all may affect discoverability. Apple says tags improve relevance, not that they change rank order. Keep the English (U.S.) metadata accurate; never deselect every tag.

## The opportunity test

Run this on every candidate term, in the storefront you target:

1. Search the term and read positions 3, 4 and 5. Positions 1 and 2 are often paid or untakeable (an Apple first-party app).
2. Check where each of those apps holds the term: in the name, only in the subtitle, split or reversed, or nowhere visible (keyword field).
3. Check how many new ratings each earned in the last 30 days in that storefront. Lifetime totals and star value do not matter.
4. Call the term an opportunity when the top results lack the full, unsplit term in their name, or hold it only in the subtitle, or earn few new ratings in 30 days. Results full of apps with 0-20 recent ratings are the shape to look for. Exploit it by making the term the first words of your own name.
5. Reject the term when positions 3-5 all carry it at the start of the name and out-earn your realistic 30-day rating count by more than about 20 to 30% (rule of thumb). Subtitle placement against name placement needs about two orders of magnitude more ratings.

Rating parity, dated: a 2020 reading set the bar at within about 20% of the top results' total rating counts; since 2022 the measure is new ratings, not totals, with no fixed threshold; the 2025 reading is 20 to 30% of the competitor's 30-day count at hundreds or thousands. Use the 30-day form. Apple names ratings as a ranking input but documents no parity number.

Four competitor combinations (observed 2022). For each term, note whether the top 5-10 make metadata mistakes (duplication, brand first, split phrase, keyword late in the name) and whether they earn fewer or more new ratings than you:

| Their metadata | Their ratings | Verdict |
|---|---|---|
| Mistakes | Fewer | Easy once your own metadata is clean |
| No mistakes | Fewer | Likely, given time, if your new-ratings rates are similar |
| Mistakes | More | Tough but possible: proper keyword use is weighed first, performance second |
| No mistakes | More | Do not try; pick a term in one of the first three rows |

Competitors for ASO are whoever ranks for your keywords, not the apps with your feature set. Search the term and take the top results as the set.

Benchmark depth (contested). Readings from 2019-2020 benchmarked the top 10 results' minimum and average downloads, category rank and rating count, optimizing only where you meet the minimum and approach the average, with the top 3 instead in a brand-heavy category; sibling readings used the top 5, or wanted at least the downloads of the number 5 result and ideally more than number 3. The 2025-2026 readings check positions 3 to 5 by 30-day ratings. Default to positions 3-5 by 30-day ratings; benchmark the top 3 in a brand-heavy category; use download estimates as a secondary check: Apple lists downloads as a factor, but tests show they move rank mainly through the ratings they produce.

The target is top 3 (since the second Apple Ads placement in March 2026), formerly top 5. A term you can only reach at rank 8 is not an opportunity. See `references/fundamentals.md` for visibility.

## The research waterfall

1. Pick the store and the country. Every score, rank and competitor below belongs to that one storefront.
2. Name your head term: the two or three words a satisfied user would type.
3. Find the 3-5 competitors ranking for it. Pull their organic keywords, not their paid ones, in a keyword research tool.
4. Filter to medium popularity and ranks 1-10. Drop the 5s. Sort popularity ascending so the thin, winnable terms come first. A 2020 variant of the filter: hide terms where you already rank top 5, keep popularity 10 and up, sort difficulty ascending; a gap is a term where competitors rank high and you do not, and your own ranks 6 to 15 are the easiest wins.
5. Expand from these sources, in this order: your app's own features and benefits; related keywords with the same intent; names and subtitles of the top 10 for each target; keywords you already rank for but do not target; your 4- and 5-star reviews and competitors' reviews, several at once, for the users' own wording; repeatable patterns such as language pairs for a translation app; 3-word long-tail variants of your best-ranking keyword, which competitors rarely target and autocomplete makes viable; competitors' paid keywords where you already rank organically below 10 (observed 2024; a second source, not a replacement, read over 90 days for breadth, 7 days for trends, 30 by default).
6. Run the opportunity test on each survivor.
7. Size the output: evaluate at least 30 candidates to end with 5-10 keywords (dated: 2019), of which 3-5 main keywords carry the name and subtitle; the rest fill the field or seed one theme per localization. See `references/localizations.md`. Competitor sourcing in depth: `references/competitor-research.md`.

## Intent and relevance

- Choose terms whose searcher will be satisfied by your app. For a paper-trading app, "trading simulator", not "stock market". Apple's version (Apple recommends): use the words people would use to find an app like yours and be specific about features and functionality. Guideline 2.3.7 requires keywords that accurately describe the app (Apple-documented), so an irrelevant term is also a rejection risk.
- Irrelevant keywords also cut conversion. Remove a keyword outside the app's needs list even when it ranks well (observed 2021), because every irrelevant keyword displaces a relevant one.
- Store searches are short and name an app, a feature or a benefit; questions belong to web search. Nobody searches sentences, adjectives ("better") or calls to action ("play now"). Drop them. Apple says people can search in natural, everyday language; that describes what search accepts, not what people type, and does not change this rule.
- Prefer the short casual form. Users avoid typing complicated words.
- Do not target competitor brands. Brand searchers do not shop around, and a trademark complaint forces removal. In the keyword field this is an Apple rule, not only a strategy: names of other apps or companies are not allowed, competing app names are a common rejection reason, and trademarked terms need authorization (Apple-documented). Bidding on them in Apple Ads is a separate, contested question in `references/apple-ads.md`.
- Check whether the term is tied to a category. Very generic queries such as "games" are filled from category ranks, which you cannot buy with metadata.
- Pick the word form people type. Demand differs between singular and plural and between "tracker" and "tracking", and only English plurals merge.
- After launch, target terms where a top 5-10 rank is reachable now and escalate competitiveness as ratings grow.

## "AI" as a token

- Do not add "AI" for its own sake. People search the feature: "AI voice memo" scored 5 against 55 for "voice memo". "AI" in a name helps paid conversion, not organic search.
- Exceptions exist where the AI-prefixed term has its own demand: "AI friend" 39, "AI girlfriend" 50, "AI Dungeon" 56, "AI Photo Editor" 55 (June 2025). "AI calorie tracker" and "Bible AI" were open in 2025.
- Rule: treat "AI <feature>" as a separate candidate. Score it and run the opportunity test on it. Add it only when it has demand of its own and shallow results.

## Pruning

- A metadata keyword where you rank outside the top 10 is not doing anything for you. Review it at the next metadata round.
- An existing rank, even at 99 or 147, proves relevance and is easier to lift than a new term, because the index remembers. Prefer lifting a ranked term over adding an unranked one when the two have similar demand.
- Removed keywords persist at reduced strength, so a swap is not free of history. Swap deliberately.
- ASO alone grows an app when the niche has high-popularity keywords and competitors are not buying users. When competitors buy, pair organic with paid. The same "skip the head term" logic drives Apple Ads keyword choice; see `references/apple-ads.md`.
- Per-keyword conversion is unknowable organically. To learn which of two candidates converts, run the one-week low-budget Apple Ads test described in `references/measurement-and-cadence.md`. Two Apple-documented mechanics shape it: exact match may also match spelling variations, word rearrangements and translations, so the test reads a keyword's close variants, not one literal query; and Apple Ads keyword recommendations show Search Popularity (1-5) with install, spend and cost estimates over a seven-day period from historical data, a free demand check before you spend.

## Worked example: weather app (dated: 2019-2022 numbers)

1. Seed list of 41 terms from the app's own description and from well-ranking competitors' descriptions: weather, forecast, radar, storm, rain, NOAA, local, live, alerts, maps, tracker variants, and seasonal terms such as "fall forecast", "winter forecast" and "weather nyc". Competitor brand names excluded.
2. Single-digit popularity dropped.
3. Benchmark on the top 3 because the category is brand-heavy. For "weather radar" (popularity 59) in the US, the top 3 required the phrase in the app name, at least 90,000 US downloads a month and a rating count near the competitors' roughly 500,000. Rejected for a small app.
4. Ten terms prioritized: live weather forecast, local weather, local weather alerts, local weather forecast, weather alerts, weather forecast, weather map, weather maps, weather radar, weather tracker.
5. The metadata that reaches all ten through token combination is the second worked example in `references/metadata-writing.md`.

## How to judge a candidate term

Produce one row per term with these columns, then sort by verdict:

| Column | What to record |
|---|---|
| Term | Exact form, as typed, in the order people type it |
| Popularity | Current score; note that it is post-fall-2025 |
| Difficulty | Tiebreaker only |
| Positions 3-5 | Name / subtitle / split / field placement for each |
| 30-day ratings | New ratings for each of positions 3-5 in the storefront |
| Combination | Which of the four competitor rows the term falls in |
| Intent | Would this searcher be satisfied by your app: yes / no |
| Verdict | Name lead, subtitle, field, localization experiment, or reject |

Decisions:

- Name lead: top demand on your list, intent yes, positions 3-5 beatable on ratings or lacking the term in their name. Never a 5-9.
- Subtitle: second idea that combines with the name's hub noun. See `references/metadata-writing.md`.
- Field: long-tail variations of the name's stem.
- Localization experiment: a popular term the top apps lack, or a misspelling, parked in a throwaway locale. See `references/localizations.md`.
- Reject: intent no, competitor brand, sentence or adjective, or the "no mistakes, more ratings" row.

## Evaluating a keyword strategy (dated: 2020)

Three metrics, read together, so a gain on some terms does not hide a loss on others:

1. Share of targeted keywords you rank for at all. Target 100%. If you already sit at 100%, the list is too short or too unpopular.
2. Average rank across targeted keywords.
3. Count of keywords ranked 1-10 with meaningful popularity (10-100 on the pre-2025 scale; set your own floor on the current scale), counted across everything you rank for, not only targets.

Loop: track every target, two- and three-word combinations and singular and plural forms as separate keywords; record the three metrics as the baseline; ship one change at a time so a rank move has one cause; wait four weeks while monitoring hourly or daily; record again; ask first whether anything got worse, then whether the result beats the previous reading; keep and extend what improved, replace what did not. When you lack history, run the same three metrics on a competitor over the same window and compare the deltas. A variant plans three themed keyword sets up front, runs each for about four weeks, then merges the winners. Change cadence, measurement windows and revert rules are in `references/measurement-and-cadence.md`.

## Checks

- Store and country were fixed before any score was read.
- Every score was looked up, not guessed, including plural, "-ing" and reversed-order forms.
- No pre-fall-2025 popularity band is being applied to a current score, and no 1-5 Apple Ads value is being read on the 5-100 scale or the reverse.
- Every shortlisted term passed the opportunity test on positions 3-5 with 30-day ratings in the target storefront and has a competitor-combination row.
- Difficulty was used only as a tiebreaker; download estimates as a secondary check behind 30-day ratings.
- No competitor brand, trademark, celebrity name, sentence, adjective, call to action or complicated word form on the list; every term describes the app accurately.
- Any "AI <feature>" term has its own score and its own opportunity test.
- The keyword leading the name scores above 9 and has intent yes; the list as a whole is not single-digit.
- At least 30 candidates were evaluated before the shortlist of 5-10 was fixed.
- Ranked-but-weak terms were considered for lifting before being swapped out.
- A baseline of the three strategy metrics exists before the change ships.

## Open questions

- How the 5-100 score research tools show relates to Apple Ads' documented 1-5 Search Popularity: undocumented.
- Popularity renormalization: accidental and recovering (October 2025) versus deliberate and permanent (March 2026). No restated thresholds on the new scale beyond "a 17 is not terrible"; the only reference for how far it moved is the pre-2025 baseline (most keywords 10-40).
- Benchmark depth: top 10, top 5 or top 3 (2019-2020) versus positions 3-5 (2025-2026); and downloads versus 30-day ratings as the yardstick.
- Single-digit popularity: out (2019-2020) versus a start (2025-2026); unresolved whether the 2025-2026 view holds if the scale recovers.
- No quantified relationship between ratings and rank; only the 20%, 20 to 30% and 10 to 20 ratings rules of thumb. Apple lists downloads and the "number and quality" of ratings as factors without weights; whether downloads and star average move rank beyond what tests show is unresolved (contested).
- Whether App Store Tags, generated from the en_US metadata including the description and screenshots, feed rank order or eligibility; Apple says only "improved relevance", and the misaligned results seen in the September 2025 beta were never followed up.
- Whether LLM-driven discovery sends installs that would change which terms are worth targeting: no data.
