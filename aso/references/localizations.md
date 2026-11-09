# Localizations as extra keyword budget

The US storefront supports ten languages, and Apple documents that people can search with localized keywords in every storefront where that localization's language is supported. In practice the US indexes the name, subtitle and keyword field of all ten localizations for US searches, in any language, which turns about 160 characters of indexed metadata into about 1,600. Each localization is a sealed silo: words combine inside it and never across it. Indexing rules are in `references/fundamentals.md`, how to pick the terms is in `references/keyword-research.md`, and how to write each set, field limits included, is in `references/metadata-writing.md`.

## Which localizations the US indexes

| Storefront | Supported localizations (Apple-documented, November 2026) | Keyword-field budget |
|---|---|---|
| United States | English (U.S.) default, plus Arabic, Chinese (Simplified), Chinese (Traditional), French, Korean, Portuguese (Brazil), Russian, Spanish (Mexico), Vietnamese | 10 x 100 = 1,000 characters (about 1,600 with names and subtitles) |

- Apple's storefront table lists this set, and it matches the reverse-engineered table dated 2023-04-25, Korean and Portuguese (Brazil) included. All nine extras are safe to use.
- Any language indexes (observed). English words in the Vietnamese set rank for US English searches; the language of the text does not matter to the index. Apple documents that localized keywords are searchable, not that the text's language is ignored.
- No priority among the ten (observed, reverse-engineered). Apple documents no weighting between them.
- History: Apple expanded the US set from English plus Spanish (Mexico) to the nine extras between 2020 and April 2023. English plus Spanish (Mexico) is still the most common pair because it was the original one.
- Scope: iOS and Mac apps on the App Store. Google Play has no equivalent.
- Byte budget: App Store Connect Help gives the keyword field as 100 bytes, Apple's developer pages as 100 characters. Parked English text is unaffected. Real Arabic, Chinese, Korean or Russian keywords may fit only about 33 to 50 characters if bytes means UTF-8; plan those sets to the byte count and check what App Store Connect accepts (details in `references/metadata-writing.md`).
- App Store Tags are generated from the en_US metadata, United States only (Apple-documented). The English (U.S.) set is the one that shapes them; keep it broad and accurate.

## Other storefronts

Apple lists every storefront's default language and its additional supported languages (Apple-documented, November 2026). (contested) A November 2025 reading says the parking technique "works for the US only"; Apple documents that localized keywords are searchable wherever the language is supported. That every supported language adds a full keyword set for every searcher is the US reading carried over, not something Apple states. Spot-check a storefront with a throwaway term before relying on its extra set.

| Storefront | Default plus additional languages (Apple-documented) |
|---|---|
| United Kingdom, Ireland, South Africa | English (U.K.) only |
| Australia, New Zealand | English (Australia) plus English (U.K.) |
| Mexico | Spanish (Mexico) plus English (U.K.) |
| Greece | English (U.K.) plus Greek |
| Japan | Japanese plus English (U.S.) |
| Germany, France, Italy, Korea, mainland China, Hong Kong, Taiwan, Brazil, Portugal, the Netherlands, Sweden, Austria | Local language plus English (U.K.) |
| Most Spanish-speaking Latin American storefronts | Spanish (Mexico) plus English (U.K.) |
| Uruguay, Belize | English (U.K.) plus Spanish (Mexico) |
| Switzerland | German plus English (U.K.), French, Italian |
| Belgium | English (U.K.) plus Dutch, French |
| Spain | Spanish (Spain) plus Catalan, English (U.K.) |
| Canada | English (Canada) plus French (Canada) |
| Russia | Russian plus English (U.K.), Ukrainian |
| Ukraine | English (U.K.) plus Russian, Ukrainian |
| Luxembourg | English (U.K.) plus French, German |
| India | English (U.K.) plus Bangla, Gujarati, Hindi, Kannada, Malayalam, Marathi, Odia, Punjabi, Tamil, Telugu, Urdu |
| Singapore | English (U.K.) plus Chinese (Simplified) |
| Most smaller storefronts | English (U.K.) default; check Apple's table for any additional language |

- Older guidance (the 2023 table) put Australia, New Zealand, Mexico and Greece at their primary localization only and gave Japan English (U.K.) as its extra. The current table replaces it. In Japan, park English keywords in English (U.S.), not English (U.K.).
- For the other non-English storefronts whose extra is English (U.K.), park English keywords in the English (U.K.) localization. In Apple's current table English (U.S.) appears only in the US and Japan.
- A single-language storefront (the United Kingdom, Ireland, South Africa) gets exactly one set: everything must fit in 160 characters there.
- India supports twelve languages; Australia and New Zealand two English sets. Treat each extra set as candidate budget and confirm with a rank check, per the contested note above.
- Metadata can be localized in 50 languages and locales (Apple-documented).

## Budget math

- Each localization adds 30 + 30 + 100 = 160 characters. Ten localizations turn about 160 into about 1,600; counting keyword fields alone, 10 x 100 = 1,000.
- You need neither all ten nor full fields. More than about eight distinct focuses is rare, and weight is a fixed split per set, so a padded set is a weak set.
- Perfect the English set first, then add one more. One localization done well beats ten half done (rule of thumb).
- Extra characters remove no competition. Every keyword in an extra set still needs its popularity and difficulty checked with the opportunity test in `references/keyword-research.md`; the extra budget buys eligibility, not rank.
- Localizations add slots, not visibility: one developer went from 50 to 600 ranked keywords, all below rank 100 (observed). Each set still needs ratings to climb.
- Track every secondary-localization keyword exactly like a primary one. After the measurement window, double down on the ones that rank and replace the rest.

## No combination across localizations

- Words never combine across sets. "habit" in English plus "tracker" in Russian is not "habit tracker". A multi-word term must sit complete inside one set, and a competitive one contiguous in that set's name.
- Repeating a word across localizations is not duplication and does not demote anything, but it adds no boost, and a set whose text is identical to another set is ignored. (contested) An October 2026 reading recommends repeating the most important terms in every silo anyway. Under that uncertainty: repeat at most the one or two terms you most need, never fill a set with duplicates, and watch whether rank moves.

## One focus per localization

- Give each set one theme, and put the theme keyword in that set's name, not only its subtitle. Name placement carries the same weight advantage inside every localization.
- Observed: an AI voice app gave each localization one activity and reached number one for "accent training" through its Vietnamese set. A four-localization experiment on another AI app followed the same pattern.
- Plan the sets as themed clusters: name states the theme, subtitle extends it with words that combine with the name's hub noun, keyword field holds that theme's long tail. Rules in `references/metadata-writing.md`.
- (dated: 2020) The older pattern spent the extra characters four ways instead of one theme per set: long-tail phrases ("learn to play guitar" for a guitar tabs app), extension modifiers that need not combine with each other (city names beside "weather" and "forecast"), seasonal terms with a short shelf life, or simply more good keywords. Prefer one theme per set. The four patterns still describe what a themed set's keyword field can hold, and seasonal terms belong in the throwaway set.

## Adding a localization in App Store Connect

Apple-documented unless marked, as of November 2026.

1. Sign in with the Account Holder, Admin, App Manager or Marketing role. Languages can be managed only while the app status is editable, so create a new app version first; keywords are a version property.
2. Add the target language. App Store Connect copies screenshots and other properties from the primary language but not the description or the keywords; enter both.
3. Enter the researched keywords, in any language, in that localization's keyword field, with every multi-word phrase complete inside this one localization. Write that localization's name and subtitle for the same theme.
4. Save and submit the version. Apple's pages speak of a new version, not a new binary; older guidance (2020) said a new binary was required. App information changes can take up to 24 hours to appear.
5. After release, track the new set's keywords like primary ones and swap the ones that do not rank at the next round.

- Deleting a language sends its regions back to the primary language's metadata. Before deleting a parked set, move any keyword that still ranks.
- App Store Connect languages are metadata only, separate from localizing the binary.
- A language can become primary only after a version carrying it was approved, with approved screenshots at the current primary sizes for every platform and every custom product page. Check all of these before planning a primary-language switch.

A new or changed localization counts as a metadata change under the cadence rules in `references/measurement-and-cadence.md`: one change per round, no more than every 2 to 3 weeks.

## Launch blueprint

- Ship with at least three localizations:
  1. English (US): broad. Cover everything the app does, since this is the page most US users see and the set that shapes App Store Tags.
  2. One set per extra focus, each a single theme with its keyword in the name.
  3. One throwaway set for experiments: misspellings, or a popular keyword the top apps lack. Use a far-out locale for this.
- Promote a winning experiment into a focus set at the next metadata round; replace it in the throwaway set with the next test.
- Do this before launch. The new-app boost is small now (see `references/fundamentals.md`), so there is nothing to wait for.
- Judge each set on its own schedule per `references/measurement-and-cadence.md`.

## Device language and what the searcher sees

- Apple-documented: the language shown depends on the App Store language for the location, the device language settings, the languages the developer added and the primary language. A French localization shows to users whose language setting is French and in regions that support French but not English. With no matching localization the next most relevant one is used, otherwise the primary language.
- So the localization that matched is not the page the searcher sees: a US user on an English device found through a Vietnamese keyword lands on the English page (observed, consistent with the rule above).
- Therefore the English set stays broad and the other sets stay specific. The English page, its screenshots and captions must convert for every keyword that any set ranks for.

## Real localization versus parked English keywords

- A localization carrying English keywords for US rank is a parking lot, not a translation. Switching Spanish (Mexico) from parked English to real Spanish loses those keywords unless you move them to another set first.
- When you localize for a market, research local winners in a keyword research tool; do not translate the English set. Demand and word forms differ by language, and other languages may index plurals separately. Apple recommends tailoring keywords to each market and localizing the description, keywords, previews and screenshots, with the name optionally translated.
- (dated: 2024) To seed the list for a new country, pull the keywords competitors pay for in that storefront with a tool that estimates competitors' paid keywords, and machine-translate the list only to judge relevance, never to produce the metadata.
- English dominates search in many countries, while Arabic or Portuguese terms can be popular inside the US. Check demand per storefront and per language before deciding which direction a set faces.
- Identical text to the English set is ignored. A "localized" set that copies English adds nothing.
- Scope of real localization (dated: 2019): localize the name, the text-bearing screenshots and the description. Metadata localization drives the download; in-app localization drives retention. Start with the app's top 3 to 5 countries.
- Read low conversion in one territory as a sign to check that territory's localization (Apple recommends).
- Apple favors multi-language apps when featuring (rule of thumb), so real localization is a featuring argument as well as a search one.

## Custom product pages and localizations

- Apple documents custom product page keywords as selected per localization, repeating the selection for each one, from the latest approved app version (since iOS 26). A page can carry keywords in any localization; older guidance that only the main localization's field is pickable is superseded.
- Unknown: whether a keyword from one of the nine extra US localizations shows the page to a US searcher whose device is set to English. Until that is tested, route the phrases that matter most through the English (U.S.) set, and treat an extra-localization selection as an experiment you verify with a search on an English US device. Routing rules: `references/custom-product-pages-and-events.md`.

## Worked example

A schematic habit app with two secondary audiences:

- English (US): name leads with "Habit Tracker", subtitle extends with streak and routine words, field holds the long tail. Broad, because every US user lands here and tags come from it.
- Spanish (Mexico), parked English: one theme, "Water Reminder", with that phrase in this set's name, hydration words in the subtitle and field. Nothing repeats the English set.
- Vietnamese, throwaway: a misspelling of the head term and one popular keyword the top apps lack in their names. Checked in a rank tracker after the measurement window; a winner moves into a focus set.
- Wrong: "habit" in English and "tracker" in Spanish (Mexico) expecting "habit tracker"; a Vietnamese set that copies the English set word for word; "Water Reminder" only in the Spanish subtitle with a brand-only name; parked English in English (U.K.) for the Japan storefront, which supports English (U.S.).

## Checks

- Every multi-word target sits complete inside one localization, contiguous in that set's name when competitive.
- Each extra set has one theme and carries its theme keyword in the name.
- The English (U.S.) set covers everything the app does, its page converts for every ranked term, and its metadata is accurate enough to shape App Store Tags.
- No set is padded to full fields; no set copies another set's text.
- At least three sets at launch: English broad, focus sets, one throwaway experiment set.
- Every keyword in an extra set passed the opportunity test; none was added because the characters were free.
- Non-Latin keyword fields were planned to the byte count and checked in App Store Connect.
- A new localization has its own description and keywords entered; none were assumed copied from the primary.
- Keywords parked in a set you plan to localize for real, or delete, have a destination set before the switch.
- Custom product page keywords are selected in every localization that should route to the page; the most important ones sit in the English (U.S.) set.
- Outside the US, parked English sits in the English variant Apple's current table lists (English (U.S.) in Japan, English (U.K.) elsewhere), and no extra set is assumed for a single-language storefront.
- The localization shipped with an app version, and the change is logged as a metadata change for the cadence rules.
- Ranks are read per set and per storefront.

## Open questions

- Whether the ten US sets carry equal weight and whether the text's language matters: both reverse-engineered, not documented.
- Other storefronts: Apple documents each storefront's languages and that localized keywords are searchable there; a November 2025 reading calls the parking technique US-only, and no rank test outside the US is published.
- Cross-locale repetition: "no boost" versus "repeat the key terms in every silo" (October 2026, contested).
- Whether a custom product page keyword selected in an extra US localization shows the page to a US searcher on an English device.
- Keyword field 100 bytes versus 100 characters, and therefore the real budget of a non-Latin set.
- How other languages handle stemming beyond "plurals may index separately".
