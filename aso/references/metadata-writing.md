# Metadata writing: name, subtitle, keyword field

These rules turn a chosen keyword set into the three indexed fields of one localization: name, subtitle and keyword field. The governing idea is focus: one theme per metadata set, the best keyword first in the name, no word spent twice, and no field filled for its own sake. Apple documents the limits, the keyword-field formatting and what gets a keyword rejected; the placement and weighting rules (keyword first, no repeats, tokens combine, do not fill) are tested rules that have held from 2019 through 2026, and the one rule that flipped is field filling, marked below. Keyword choice is in `references/keyword-research.md`; the indexing model behind every rule here is in `references/fundamentals.md`.

## Field limits and what needs a new version

Apple-documented, as of November 2026:

| Field | Limit | When it can change |
|---|---|---|
| Name | At least 2, at most 30 characters | App information |
| Subtitle | 30 characters | Only with a new app version |
| Keyword field | 100 bytes (App Store Connect Help) or 100 characters (Apple's developer pages); each keyword longer than two characters | Only with a new app version |
| Promotional text | Does not affect search ranking | Any time, without a new version |

- The keyword-field unit is an Apple-internal conflict (captured November 2026). For Latin-script text bytes and characters are the same. If bytes means UTF-8 bytes (Apple does not say), a Chinese or Korean character takes three bytes and a Cyrillic or Arabic one two, so those fields would hold roughly 33 to 50 characters. Plan a non-Latin keyword field to the byte count and check what App Store Connect accepts before you finalize it.
- Keywords, description and screenshots are version properties. Promotional text is the only text field Apple marks as changeable without a new submission, which makes it the place for news, never for terms.
- App information changes can take up to 24 hours to appear on the App Store (Apple-documented). Do not read a missing change as a failure before then.
- Keyword-only changes to a custom product page go live without review (Apple-documented, since iOS 26); see the custom product page section below.
- Since iOS 27 the product page header and the search result image or video are approved once in the Asset Library and can be swapped on a live version without a new version (Apple-documented, WWDC 2026). Whether their text is indexed is undocumented; plan no keywords there.
- A metadata change reaches an Apple Ads ad within two hours (Apple-documented).

## Name

- Lead with the most valuable searched keyword. Put the brand last and short, three or four characters if possible. Keep to about three words. Keyword first unless the brand is searched more than the function has been the rule since at least 2019-2022; many top results that do not put the keyword first leave room for a weaker app to squeeze in by moving it earlier.
- (contested) Apple recommends a simple, memorable name that is easy to spell, hints at what the app does, is distinctive and avoids generic terms, and Guideline 2.3.7 asks for a unique name (Apple-documented). That is advice, not a documented ranking mechanism, so the tested keyword-led rule stands. Satisfy both: write the keyword lead so the whole name still reads as a unique brand phrase ("LiDAR Scanner - Acme", not "Scanner").
- Guideline 2.3.7 bans packing the metadata with trademarked terms, popular app names or pricing information (Apple-documented). "Free" in a name or subtitle falls under the pricing ban.
- Used to be (dated: 2019): brand, then a colon or hyphen, then a 3-5 word function phrase ("LittleWeather: Weather Forecast and Alerts"). Superseded by keyword first. The hyphen or colon remains the standard separator between keywords and brand; both are word breaks.
- Brand first only when the brand itself is searched by name (Uber, Tinder).
- Always keep a brand in the name. An app ranks number one for its exact name, and word of mouth needs something to type. A brand-only name gives the algorithm nothing: a "clean" name with keywords only in the subtitle surfaces mainly for brand searches (observed 2020), and by 2026 even Tinder and Uber carry keywords.
- Never lead the name with a keyword scoring 5 to 9. The first word gets the most weight; spend it on demand.
- Keep a competitive multi-word term contiguous in the name and in the order people type it. Split between name and subtitle it ranks only with momentum; reversed, it is a different keyword (observed 2022).
- Put a hub noun in the name that combines with every subtitle word. Polycam's "scanner" turns subtitle words into "CAD scanner" and "LiDAR scanner" without spelling either phrase. The same pattern from 2019: "book" in the subtitle extends "hotels" and "flights" in the name.
- A keyword at the end of the name is the page-two mistake (observed). Move it to the front.
- Before using "&" or ":" in a full-length name or subtitle, apply the 30-character window rule in `references/fundamentals.md`. Apple says special characters such as # or @ carry no extra weight in search (Apple recommends).
- Changing the name to a new keyword transfers no weight from the old one; only ratings carry over. Plan a name change as a restart for that term.

## One idea per metadata set

- Expedia, with about 70,000 ratings, is ninth for "trip planner" while an app with 42 ratings and the phrase in its name is fourth. "PGA Tour" outranks "PGA Tour Golf Shootout" despite 4 to 5 times fewer ratings (observed). Expedia was already the example in 2019: "Expedia: Hotels, Flights & Car" with the subtitle "Trip planner & travel deals" mixed five themes and ranked high for none despite more ratings than any competitor; the proposed rewrite was "Expedia: Hotels Deals" with "Book cars and flights". Focus has been rewarded since before 2019.
- Pick one theme per localization. The name states it, the subtitle extends it, the keyword field holds its long tail. A second theme gets its own localization; see `references/localizations.md`.

## Subtitle

- Keep a subtitle. Removing an existing one is penalized (observed; Apple documents no penalty), never having one forfeits 30 characters, and in 2026 you must set one. It used to be optional (dated: 2019, framed as a 3-5 word main-benefit phrase).
- Fill it with words that combine with the name's hub noun and that the name does not already contain. The subtitle adds new words, never repeats.
- Write a concise phrase about features or typical uses, not generic praise such as "world's best app" (Apple recommends). Guideline 2.3.7 bans references to other apps and unverifiable claims in it (Apple-documented).
- Separators are not needed for indexing. Write for humans anyway: "hug kiss generator" reads as stuffing and costs conversion. A name and subtitle can target about ten phrases through token combination and still read as a sentence (second worked example below).
- Weight: below the name. (contested) Below the keyword field's or roughly equal to it; put the second-best term here regardless. Apple ranks no field against another.

## Keyword field

- Format: comma-separated, no spaces after commas (Apple-documented: commas instead of spaces maximize the character count). Single words, singular only, no quotes, no dashes. Example of the shape: `lidar,cad,floorplan,measure,roomplan`.
- Phrase entries are valid. Apple documents spaces inside a phrase, as in `Property,House,Real Estate`, so a phrase is not a format error. Still enter single words by default: a single word saves the space, and the store builds phrases from tokens across name, subtitle and field within the localization (observed). Use a whole-phrase entry only to route an organic custom product page (below).
- The field is invisible to users, so it needs no readability. Use it for secondary words that combine with name and subtitle tokens into extra phrases. Example (dated: 2019): `buy,shoe,sneaker,shop,accessories` replaces five quoted phrases such as "buy shoes" and "shop for shoes", because the store builds the phrases itself.
- Put the stem in the name and the long-tail variations here. The most important field word goes leftmost.
- Leave out (Apple recommends unless noted): the app name and the company name, since the app is already searchable by both; the category name, since the primary and secondary categories are indexed from their own fields; plurals of words already included (Apple-documented: "climbs" beside "climb" is a duplicate); "app" and "game"; filler words such as "the" and "to" and the rest of the stop-word list in `references/fundamentals.md`; special characters unless part of the brand; words of two characters or fewer (Apple-documented).
- Never enter (Apple-documented rejection reasons): unauthorized trademarked terms, celebrity names and other protected words, names of other apps or companies (competing app names are a common rejection), irrelevant terms, inappropriate or offensive terms, and pricing information such as "free". "For Kids" and "For Children" are reserved for the Kids category (Guideline 2.3.8), and "AR" may appear in the name, subtitle or keywords only for apps with real augmented reality features. Apple may modify inappropriate keywords at any time. "HD" and "for iOS" are observed rejection triggers that Apple does not name; leave them out too.
- Keywords must accurately describe the app (Apple-documented, Guideline 2.3.7). An irrelevant term is a rejection risk as well as a wasted slot.
- Do not fill the field. Used to be (dated: 2019-2020): use every one of the 100 characters and refill freed space with closely related secondary terms. Superseded after a half-filled keyword field reached number one and filling it dropped the rank (observed 2025). Two or three strong keywords beat 100 characters of weak ones, because weight is a fixed split across every word you provide. Apple frames its advice as fitting more words into the limit but never says to fill the field, so it settles nothing here.
- A field word where you rank outside the top 10 is not helping; review it at the next round per `references/keyword-research.md`.

## Keyword-field compression procedure (dated: 2019)

Start: `shopping, sneakers, sneaker, shop, shopping app, buy sneakers, buy accessories, shoes, shop sneakers` (100 characters).

1. Split every phrase into single words and delete duplicates: `shopping, sneakers, sneaker, shop, app, buy, accessories, shoes` (63 characters). This also creates combinations the phrase list never had.
2. Delete the spaces after commas (56).
3. Delete plural forms and keep the singular (about 47).
4. Delete stop words, here "app" (about 45).
5. Drop the app name, the company name and the category name if present.
6. Swap long or complicated words for the short casual synonym people type.
7. Leave the freed characters empty unless a closely related secondary term passes the opportunity test. The 2019 step refilled them; the 2025-2026 reading stops here with the field half full.
8. Order the list most important first, long-tail or low-competition terms last.

Result shape: `shopping,sneaker,shop,buy,accessories,shoe`, well under half the field. Apple's own keyword checklist matches every step except the refill, which it neither asks for nor forbids.

## Audit order (dated: 2022)

Run this on an existing listing before any researched rewrite:

1. No word repeated across name, subtitle and keyword field, singular and plural pairs included.
2. Most important keywords at the start of the name, then the subtitle, then the field.
3. Look up every targeted keyword's popularity and drop the low ones.
4. Field is single words, deduplicated, comma-separated without spaces, singular, with no quotes, dashes, competitor names or other rejection triggers listed above.
5. Count each special character in the name and subtitle twice so nothing is truncated.
6. For each target keyword, classify the top 5-10 into the four competitor combinations in `references/keyword-research.md`.
7. Confirm the app actively prompts for ratings; see `references/ratings-and-reviews.md`.
8. Fix the quick things first (duplication, placement), then run a researched round that replaces and restructures keywords.

## Organic custom product page keywords (since iOS 26)

- Apple-documented: keywords for a custom product page are assigned from the latest approved app version and selected per localization, repeating the selection for each one. The page becomes searchable for them only once it is approved and set to visible. A keyword-only change goes live without review. Apple recommends a unique keyword selection per page. Up to 70 pages per app.
- The picker offers whole keyword-field entries (observed). A phrase you route to a page therefore goes into the field as one entry, with its internal space, which Apple's phrase format allows. Whether name and subtitle words are selectable is not documented.
- Older guidance (July 2025) said the picker shows only the main localization's field. Apple's documentation now selects per localization; treat the main-localization limit as superseded.
- Do this only for a phrase you can rank for organically or pay for in Apple Ads. Never duplicate a name keyword into the field to make it pickable; the duplicate demotes the name word. Design and routing: `references/custom-product-pages-and-events.md`. How the per-localization selection interacts with the extra US localizations: `references/localizations.md`.

## The no-repeat rule

- Never repeat a word across name, subtitle and keyword field. Only the last instance survives, so a name word repeated in the subtitle drops to subtitle weight, and one repeated in the field drops to field weight (observed). An English plural next to its singular counts as a repeat; Apple documents plurals of included words as duplicates.
- Apple recommends not repeating in the keyword field any word already in the name, subtitle or category, and calls repeats a waste of characters. It documents no penalty and no "last instance" mechanism.
- (contested) Whether the repeat is a penalty or merely wasted characters is unsettled. The 2022 readings split the same way: one says all but the last instance are ignored, the other that duplication between name or subtitle and the field once had some benefit and since 2022 is penalized with lower ranks. The position loss is the same.
- Observed: removing a duplicated "notes" would lift Otter from number 3 to number 2 for "voice notes" (popularity 36).
- Diagnostic: an exact name keyword missing from the first three pages of results usually means a duplicate of it sits in the keyword field.
- Exceptions: screenshot captions, where repetition helps (below), and other localizations, where repeating is not duplication but adds no boost. (contested) An October 2026 reading recommends repeating the most important terms in every localization; see `references/localizations.md`.

## Screenshot caption reinforcement

- Since mid-2025, repeat the name and subtitle keywords about three times across the first three screenshots in large, high-contrast caption text (observed July 2025 to September 2026). (contested, dated) A June 2025 reading found no gain from repeating a caption across screenshots beyond one mention and advised against it, marked as unproven; the later readings stand.
- Captions reinforce keywords already in the metadata, add none, and weigh less than the name or subtitle (observed since October 2025), so this is the only place where repetition helps and the wrong place to introduce a new term. Apple does not list screenshots among the searchable fields; it says App Store Tags draw on metadata including screenshots (WWDC 2025). Caption text as a ranking input stays an observation.
- Apple-documented: search results show up to three screenshots or previews depending on platform and orientation, and the first one to three screenshots appear when there is no preview. Since iOS 27 an app can show a dedicated search result image or video instead, tailored per keyword through custom product pages. When such an asset replaces the screenshots in results, keep the caption rule anyway; whether the asset's text or the hidden captions count is undocumented.
- Write each caption as an active searched phrase: "Track Sleep Patterns" yields "track sleep", "sleep patterns" and "track sleep patterns"; passive captions ("Wake Up Refreshed", "Easy to Use", "All-in-one") yield nothing. One keyword theme per screenshot. Start with the name and subtitle keywords, then long-tail variations in later screenshots.
- Legibility, caption position, fonts and the conversion side of screenshots are in `references/screenshots-and-product-page.md`.

## Description and promotional text

- Never write the description for search. Apple leaves it off the searchable fields, uses it for web search engine results, and advises against adding keywords to it to improve search (Apple-documented). Apple Ads reads it for ad relevance only; see `references/apple-ads.md`.
- Promotional text does not affect search ranking and should not carry keywords (Apple-documented).

## Worked examples

A schematic scanner app (brand "Acme" as a placeholder) whose name is brand-only and whose subtitle repeats its one keyword:

- Before: name "Acme", subtitle "3D scanner for LiDAR scans", keyword field `scanner,3d,scan,scans,lidar,app,free`.
- Problems: brand first with no keyword; "scanner" repeats across subtitle and field; "scans" is the plural of "scan", so a duplicate; "3d" is two characters and below Apple's floor; "for" is a stop word; "app" is on Apple's leave-out list and "free" is pricing information, a rejection trigger.
- After: name "LiDAR Scanner - Acme", subtitle "Room, floor plan & CAD", keyword field `measure,roomplan,photogrammetry,mesh`.
- Why: "LiDAR scanner" is contiguous and leads; "scanner" is the hub noun, so the subtitle yields "room scanner", "floor plan scanner" and "CAD scanner" without repeating it; the field holds long-tail variations only.
- Then: repeat "LiDAR scanner" and "floor plan" in the captions of the first three screenshots.

A weather app with ten target phrases from `references/keyword-research.md` (dated: 2019-2022):

- Name "Weather Line - Live Forecast", subtitle "Local Alerts, Maps, and Radar", keyword field `rain,snow,temperature,cold,wind,warning,fall,winter,storm,check,track,tracker,hurricane,advisory`.
- The tokens combine into all ten targets ("live weather forecast", "local weather alerts", "weather radar", "weather map", "weather tracker" and the rest) and reach "storm map", "rain tracker" and "hurricane alerts" with nothing repeated across fields. Both halves read as sentences.
- Read with 2025-2026 eyes: the field is nearly full, so trim it to the words that pass the opportunity test; "track" and "tracker" are separate tokens, not a plural repeat.

## Checks

- Name: 2-30 characters, most valuable keyword first, contiguous and in typed order if multi-word, brand last and short, about three words, reads as a unique brand phrase, no 5-9 keyword in front, hub noun present, one spare character per "&" or ":" when the field is full.
- Subtitle exists, is at most 30 characters, adds words that combine with the hub noun, repeats nothing from the name, makes no unverifiable claim or reference to another app, reads as a sentence to a human.
- Keyword field: within 100 bytes (count bytes for non-Latin scripts), comma-separated, no spaces after commas, single singular words except a custom product page phrase entry, every keyword longer than two characters, most important word leftmost, no app, company or category name.
- No word appears in two fields; no plural beside its singular; no stop words, "app", "game" or special characters; no trademark, celebrity, competitor or other company name; no pricing words, "for iOS" or "HD"; no "For Kids" outside the Kids category; no "AR" without AR features.
- The set carries one idea. A second idea has been moved to another localization.
- The field is not padded to 100 characters with weak terms; the compression procedure was run on any inherited phrase list.
- If a phrase sits in the field, it is there to attach an organic custom product page and is not a duplicate of a name word; the page's keywords are selected in every localization that should route to it.
- Screenshot captions are active searched phrases that repeat the name and subtitle keywords about three times across the first three screenshots and introduce no new keyword.
- No keywords were planned for the description, promotional text, header or search result asset.
- Subtitle and keyword-field changes are tied to a new app version; nothing is judged missing before 24 hours.
- The audit order above was followed: quick fixes first, researched round second.
- Measurement window, change cadence and revert rules are followed per `references/measurement-and-cadence.md`.

## Open questions

- Keyword-field unit: 100 bytes (App Store Connect Help) versus 100 characters (Apple's developer pages); unreconciled as of November 2026, and it matters only for non-Latin scripts.
- Subtitle versus keyword field weight: below or roughly equal (contested); Apple documents no weights.
- Repetition across fields: penalty versus wasted slots (contested since at least 2022); Apple calls it a waste of characters and mentions no penalty.
- Keyword-led name versus Apple's advice to avoid generic terms in the name: no documented mechanism either way.
- Caption repetition: once (June 2025) versus about three times (July 2025 onward); no controlled test. Whether iOS 27 search result assets are read, and whether captions still count when such an asset replaces the screenshots in results.
- Whether name and subtitle words can be selected as custom product page keywords.
- The special-character double count (2022) and the 30-character title truncation bug (October 2025): current status and whether they are the same thing are unknown; Apple says only that special characters carry no extra weight.
