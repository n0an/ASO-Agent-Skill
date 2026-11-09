# Ratings and Reviews

On the App Store a rating is the currency that turns downloads into rank: the working model is that the algorithm counts new ratings per storefront over roughly 30 days and ignores the star value. Apple documents only that ratings and reviews "can influence" search rank, so the count, window and velocity rules are rules of thumb from rank data, while the prompt, incentive, quoting and reply rules are Apple-documented and binding. Ratings are also social proof on the product page and in search results; review text is research, a support channel and, since 2025, the input to Apple's review summaries. Keyword placement: `references/keyword-research.md`. Popularity numbers are a search popularity score (Apple's relative demand, 5-100, logarithmic), pre-renormalization unless dated 2026. "(dated: year)" marks an older rule that still holds.

## Hard constraints (App Review Guidelines, Apple-documented)

Not tactics: breaking one gets the build rejected, ratings deleted or the developer removed. Check every rating or review feature against these first.

- **System prompt only (Guideline 5.6.1).** Apps must use the provided API (SKStoreReviewController) to prompt for ratings and reviews; Apple disallows custom review prompts. Never build your own star picker, rating dialog or "Rate us" screen. A custom screen before the system prompt is allowed only if it does not itself request a rating or review.
- **No sentiment gate.** A "Do you like the app?" step that sends happy users to the prompt and unhappy users to a feedback form is review gating: a custom review prompt under 5.6.1 and review manipulation under 5.6.3. The guidelines name no exception.
- **Never force or pay for a rating (Guideline 3.2.2(x)).** Apps must not require users to rate, review, download other apps or take other store-related actions to access functionality, content or use of the app. Incentives are allowed only for in-app actions, such as completing a level or watching an ad. Never offer a discount, a cheaper subscription, coins or anything else for a rating or review; that falls under 5.6.3's ban on manipulating reviews (inference) and has risked rejection and removal since at least 2020.
- **No manipulation (Guideline 5.6.3).** Manipulating ratings, reviews, charts, search or referrals is discovery fraud; under Guideline 5.6, repeated manipulative or fraudulent conduct removes the developer from the Apple Developer Program. This covers bought ratings and installs, rating farms, review swaps and fake reviews.
- **Quotes need permission; ratings must be current.** Customer reviews may appear in marketing materials only with the reviewer's permission, and the app's rating only while it matches the current rating. Apple does not say whether product page screenshots are marketing materials; treat them as such (inference). Get permission before a quote goes into a screenshot, custom product page or ad; update or remove a printed rating when the real one changes.
- **Clean responses (Guidelines 5.6 and 5.6.1).** Respectful, never harassing or bullying, targeted to the user's comments, no personal information, spam or marketing.
- **Prompt cap.** SKStoreReviewController can prompt at most three times in a 365-day period (Apple-documented). Older guidance said "three per user per year"; Apple does not say whether the count runs per user, device or install. Treat every display as scarce.

## Ratings as the ranking currency

- Two stages: words in the name, subtitle and keyword field decide which apps are eligible for a query; then a performance metric, mainly new ratings, orders them, weighed with where the keyword sits in the metadata (rule of thumb since 2019). Apple confirms only that ratings and reviews "can influence" rank. In-app usage stays out for privacy; deletions and crashes weigh little.
- The signal is the count of new ratings, not their value: a 1.47 and a 4.85 are the same, and a run of one-star ratings still raises rank (observed). Contested by older material: a 2020 reading says top results have more ratings and a higher average, and a 2019 snapshot found 70% of the top 1,000 free US iPhone apps and 50% of the top 100 at 4 stars or higher. Use the star-blind reading, held 2022 through 2026: apps that ask earn both more ratings and a higher average, and the 2019 figure is a top-chart snapshot.
- Only the last roughly 30 days count, only in the storefront being ranked (working model, not Apple's). 42 lifetime ratings outside the window leave an app equal to any other with the same name keywords; 34 recent ratings do not compete against a rival's 2,400 lifetime; 130 a month worldwide mean nothing for US rank unless they are US ratings, where the top result for "AI image generator" earned about 740 a month (observed).
- Attribution (Apple-documented): the summary rating is specific to each territory, and a rating belongs to the storefront where the customer first downloaded the app. App Store Connect shows ratings per country or region but no history over time; track new ratings per day per storefront in your rank tracker.
- Velocity must be steady. Ratings on one day out of 30 do not help; weekly arrivals over about a month lift the app for its metadata keywords. A gradual increase shows within a few days to a week; a spike from a large ad push needs about a week of the new steady state (observed). A 2022 "massive spike" exception was never quantified.
- Below about rank 20, one rating in a week moves a new app almost instantly; no recent ratings caps it where it is.
- The count is relative to the apps holding the keyword: 100 new ratings against competitors at 1,000, or 1,000 against 10,000, is not enough. Stay within about 20% of the top results' new-rating count or the top 5 is out of reach (rule of thumb since 2020).
- Downloads from any channel rank only through the ratings they produce. Apple Ads spend has no direct effect, or the heaviest spenders would be first for every keyword. Paid installs that never become ratings move neither store conversion nor blended cost.

## Ratings as a conversion input

- The summary rating shows on the product page and in search results, beside up to three screenshots or previews (Apple-documented). Apple's only conversion statement: few ratings "may discourage" downloads (Apple recommends). The lift is unmeasured; a 2016 survey found 77% read at least one review before downloading. A low average says people dislike the app, a low count says too few use it (dated: 2021). Layout: `references/screenshots-and-product-page.md`.
- Thresholds for pasting a count into screenshots (rules of thumb, contested within 2025): February, 450 five-star ratings is fine proof; April, show the count only above about 1,000 and the average only above roughly 4.3 to 4.4, ideally 4.5; July, 10,000 or even 5,000 reads as a lot. Apply the April rule, the strictest. The store-rendered count is social proof at any size, 3 or 300,000 (dated: 2021).
- With a handful of ratings, remove rating and App Store badges. "5.0 worldwide rating" beside nine visible ratings says the app is too small, and with 1,200 other habit trackers the user moves on (observed).
- A "#1" claim needs roughly 10,000 ratings at 4.9. With one rating use a real review quote, with permission, or wait. Without a feature or press mention, put the best and shortest permitted reviews in the first screenshot.
- Summary-rating reset (Apple-documented): an optional per-version switch that clears the displayed rating in all countries when the version ships, keeps written reviews and cannot be undone; until enough users rate, the page says the rating was recently reset. Apple recommends it sparingly, for an update that fixes what earlier reviews complained about. Steps under Procedures.
- Reviews are research input. Your 4- and 5-star reviews hold the words satisfied users use for the app's job; aim ads, screenshots and custom product pages at recurring terms. Your 1- and 2-star reviews are a bug report once grouped by version; App Store Connect filters by version, star rating, country or region and edited or responded status (Apple-documented). Competitors' reviews show what their users lack; before launch their good-to-bad rating ratio signals room for entry (dated: 2020). A sudden drop in a competitor's new-rating volume marks an event that upset users, such as a price change or an AI feature; read that window (observed). See `references/competitor-research.md`.

## When and how to ask

- Ask. Apps with growing, paying user bases that never ask get almost no ratings; once they ask, ratings rise overnight, and two to four extra a week beats zero. Uncontrolled cases: a pool game went from 217 to about 9,818 new daily ratings (circa 2019 to 2020); a file-transfer app grew ratings 3,000% (2022). Apple lists positive ratings and reviews among featuring considerations, with no threshold (Apple-documented).
- Timing (contested, none measured). 2025-2026 main line: as early as makes sense after the first use or two, not inside onboarding. October 2025 counter-position: inside onboarding after delivering an insight, because 75% or more of users are gone by the next day; this cut downloads per rating for many apps. 2020 position: right after the user completes the task they came for, and safer to wait too long than too little. Apple recommends asking when users are most likely satisfied, "such as when they've completed an action, level, or task", without interrupting (Apple recommends): it sides with 2020 against onboarding, as advice, not a rule. Asking before use, such as before the paywall, may yield more but lower-quality ratings; test.
- Never interrupt a task or a game level; a badly timed prompt becomes a negative rating at worst (dated: 2020). Deliver value first; a social proof screen ("X people already rated us five stars") before the system prompt is fine only if it asks for nothing itself. Never prompt on the launch screen.
- Make support contact easy to find in the app and on the product page (Apple recommends).
- Since August 2026 Apple has been deleting ratings and reviews prompted too early in the session; "too early" is undefined. An April 2025 rumor held that ratings requested within seconds of first launch may be discounted.
- Diagnose by funnel: about 200 downloads a day stuck at one rating means the trigger fires at the wrong time; check how many users reach it and move it earlier gradually. A dismissed prompt spends one of the three displays.
- Paid installs: every ad-driven download should hit a well-placed prompt; ratings are the only benefit ads bring to organic rank. Before any campaign confirm prompt timing and that keyword targets match your rating position. Apple Ads users rate more than Meta users. Run a ratings-driving campaign in one country at a time. At launch, a brief run of cheap long-tail Apple Ads seeds the 10 to 20 ratings a thin niche needs; counts like 9, 3, 261, 18 and 32 at the top of "tattoo design" (14) are reachable from community posts without ads (observed). See `references/apple-ads.md` and `references/meta-ads.md`.

## Benchmarks: downloads per rating and velocity

- Downloads per rating: estimated downloads over the last 30 days divided by new ratings over the same 30 days, in one storefront; lower is better. It tells you how many downloads buy one rating and whether prompt changes work. At 10 against a competitor's 40 you earn ratings four times as fast, but the absolute count is what ranks.
- Rule of thumb: ideal 1, under 30 good, above 100 ugly. Large apps that ignore ratings sit in the high hundreds. 240 means the app is not asking; peers in one result set sat at 318 and 323 (observed).
- Observed: the "AI calorie tracker" (38) top 10 ranged from 21 to about 100 on average; Expedia 10, TripAdvisor 17, Roadtrips 291 for "trip planner"; Cal AI needs 15 to 17 installs per rating against 24 to 25 for MyFitnessPal, which is how it overtook an app with 2.1 million US ratings on "calorie" (51), read from estimated downloads; 22 at roughly 200,000 downloads is okay.
- Velocity (rules of thumb): at small counts every rating counts, and 9 against 31, 24 and 20 is the whole gap. At hundreds or thousands, stay within about 20 to 30% of the competitor's 30-day count; to take a head term, match or exceed the incumbent's. Where the top apps hold 5 to 13 ratings, six to eight new ratings per 30 days is competitive, sustained monthly; 10 to 20 more move rank 5 to 1 or 2.
- Observed ladder: 2 ratings is third for "AI calorie tracker" (38) when nobody targets the exact phrase; 6 new ratings is third for "weather forecast" (29) with the phrase intact in the name; 57 holds first for "volume booster" (53); 26 stays top 10 for "OBD2 scanner" against 1,300; 81 is seventh for "Master English" (38) against 1,000 to 128,000; 509 lifetime with about 60 in the best month is not enough for "step counter" (59); weight-loss leaders earn about 5,000 new US ratings in 30 days.
- Spend ratings where they count. Never fight for a popularity-5 keyword against apps with 1,000 to 18,000 ratings. A "bad" keyword is one you cannot win at your rating level; expand it into longer variants. Only an app earning thousands of new ratings a month can afford many terms in its name and subtitle.

## Reviews: text, summaries and replies

- Ratings are the stars, reviews the written part; most users leave only a rating. Apple-documented: written reviews on iOS, iPadOS, macOS, visionOS and watchOS (from the paired iPhone), ratings only on tvOS. One rating per user: an edit or new submission replaces the earlier one.
- App Store ranking: the working model since 2022 is that review text does not count; Apple's "ratings and reviews can influence" leaves it open. Plan no keyword gains from App Store review text and no ranking effect from replies.
- Review summaries (Apple-documented, since WWDC25): Apple's large language models write a short paragraph from individual reviews for apps with enough reviews, refreshed regularly. As of November 2026 they show in the United States, Australia, Canada, India, Ireland, New Zealand, Singapore, South Africa and the United Kingdom, in English. App Store Connect shows the summary and its generation date; report a wrong one with Report a Concern next to it (iOS platform). Your most repeated complaint now sits on the page, so fixing it is a product page task (inference).
- Reply as support (dated: 2018 to 2021, unmeasured): reply to 1- and 2-star reviews to get them changed; they often come from a misunderstanding, and unanswered ones make the app look abandoned.
- Reply mechanics (Apple-documented): respond to any review, however old; the reviewer is notified and can update it. One response displays per review and stays public after the customer edits. Anyone with the role can edit or delete it; edits show "edited". Responses take up to 24 hours to appear. Replying needs the Account Holder, Admin or Customer Support role, in App Store Connect or through its API.
- Priorities (Apple recommends): lowest stars and current-version bugs first; concise, friendly, personalized replies in the brand's voice; after a fix ships, note it in the release notes and reply to the reviews that raised it; reply promptly after a major release; turn on email alerts for edits to reviews you answered.
- Do not reply (Apple-documented): send downloading errors and billing issues to Apple Support; report offensive material, spam and Terms and Conditions violations with Report a Concern, which does not notify the reviewer.

## What Apple removes or penalizes

- Bought ratings or installs: discovery fraud and grounds for removal (Hard constraints). Apple eventually terminates farm accounts and deletes their ratings; Google bans for life in ways that block new developer accounts (observed).
- Guideline 5.6.4 (Apple-documented): excessive negative reviews, customer reports and refund requests indicate low quality and may weigh on Code of Conduct decisions; an account-standing rule with no threshold.
- Farms train accounts by rating random apps; report an off-topic review that feels wrong. When Apple purges those accounts, honest apps lose those ratings. The deletion engine dates from roughly 2022 to 2023 and is the usual reason ratings vanish after an onboarding prompt (observed).
- August 2026: Apple said it fights fake ratings aggressively, more than fake reviews. Even friendly indie-to-indie review swaps risk attention.
- Review gating: an app flagged for it lost rankings; fixed and approved in November 2025, its category ranks had not returned by January 2026 (observed). Recovery: restart on focused long-tail keywords and rebuild category rank with ads.

## Google Play differences

- Play weighs rating quality as well as count, plus all-time downloads, immediate deletes, crashes, uninstalls and inbound links; on Apple only recent ratings count (since 2020).
- Play indexes review text, replies apparently not: phrase rating requests and replies so users write the terms you want. Bought keyword-stuffed reviews work until the account is banned; a competitor's fake reviews with irrelevant terms bring wrong users, so flag them early (observed).
- The top Play result for one keyword had 17,000 new ratings against hundreds on the App Store.

## Procedures

1. Prompt moment, in order of preference (dated: 2020; Apple recommends the first): after the user completes the task they came for; after they gain something, such as an unlocked section or a first notification; after a usage threshold when no magic moment exists, longer for feature-rich apps; after a good support interaction. Then apply every Hard constraint, and never prompt inside onboarding, on the launch screen, before first use or mid-task.
2. Iteration loop: implement one placement; track new ratings per day and downloads per rating by country; count users reaching the trigger; move it, earlier gradually when few reach it; compare; repeat.
3. Reward-first flow (dated: 2020, checked against 3.2.2(x)): give a small in-app reward unconditionally or for an in-app action; then show the system prompt; never tie the reward to the rating in copy or logic or lock anything behind a rating. A bingo game reported about 4x new positive ratings in 2019; a 2025 recollection says 50% to 2x. Apple is silent on prompting right after a reward.
4. Keyword pre-check: reject single-digit popularity; reject keywords where your new-rating count sits more than about 20% below the top results'; classify each target by the top 5 to 10 apps' metadata mistakes and new-ratings rate; confirm your app prompts; drop out-of-reach terms.
5. Three-pass review analysis (dated: 2020; yours and competitors'): loved features, 4-5 stars, search great, love, like, awesome, amazing; pain points, all stars, search hate, terrible, dislike, bad, slow, load, missing; nice-to-haves, 3-4 stars, search wish, add, recommend, suggest, feature, need. Narrow each theme with its word; tally repeats and rank by count.
6. Review mining (2026): pull the last 30 days of 1- and 2-star reviews; group by app version and find where each problem began; quote examples; flag urgent items; draft replies only for unanswered reviews and have a human edit before posting.
7. Triage (Apple-documented): download or billing issue, Apple Support; offensive, spam, Terms violation or farm review, Report a Concern, no reply; wrong review summary, Report a Concern on it; everything else, item 8.
8. Reply checklist (dated: 2018, with Apple's additions): submit within hours, at most a day, since display takes up to 24 hours; read the full review; acknowledge the feeling; use the brand voice; personalize; get to the point; avoid "unfortunately", "can't", "impossible", "never"; proofread; be honest about fixes and timelines; apologize only when warranted, then fix the cause; offer your support email, never personal information, spam or marketing; never reply angry; thank positive reviewers.
9. Rating reset: only for a version that fixes what most low ratings complain about; confirm new-version volume will rebuild a visible rating fast; strip printed counts and averages from screenshots in the same version; select "Reset rating when this version is released" on the version page with the Admin or App Manager role. Limits (Apple-documented): all countries at once, only that platform for universal apps, not for app bundles, irreversible after release.

## Dated changes

- March to September 2025: the roughly 7-day new-app boost mostly disappeared; rank holds only with correct keywords and downloads converted into ratings.
- June 2025 (WWDC25): Apple announced LLM review summaries; review text became a product page surface.
- August 2026: Apple deleting too-early ratings and stating aggressive anti-fake enforcement.
- November 2026: Apple's undated documentation confirms the three-prompt cap per 365 days, the system API as the only prompt, the rating reset, review summaries in nine English storefronts and Guidelines 3.2.2(x), 5.6.1, 5.6.3 and 5.6.4 as current.

## Checks

- Hard constraints: SKStoreReviewController only, no custom rating screen, no sentiment gate, nothing locked behind a rating, no reward for a rating? Review quotes used without permission? A printed rating that no longer matches? Fix first.
- Downloads per rating per storefront, last 30 days: under 30 good, above 100 ugly, above 200 no working prompt.
- Prompt: not on the launch screen, not within seconds of first launch, not mid-task, after the first use or two? How many users reach it? Support contact easy to find?
- 30-day new ratings per target storefront against the top three per keyword: within 20 to 30% at scale, six to eight a month in thin niches, weekly?
- Keywords unwinnable at the current rating count, or a paid campaign without confirmed prompt timing?
- Count below about 1,000 or average below about 4.3 printed on the page? Remove. "#1" without roughly 10,000 ratings at 4.9? Use a permitted quote.
- Unanswered 1- and 2-star reviews older than a day? Triage, then reply. This month's grouped by version?
- Review summary misstating the app or repeating a fixable complaint?

## Open questions

- Prompt timing: none of the three positions measured; the August 2026 deletions have no documented threshold.
- Prompt cap: per user, device or install, silent suppression and whether a write-review link counts are undocumented.
- Whether a rating reset or a storefront change affects what search ranking reads.
- Review summaries: "enough reviews", refresh cadence and the next storefronts are undefined; Apple gives both iOS 18.1 and iOS 18.4 as minimums.
- Star value and review text in rank: the star-blind, text-blind model was never re-tested against the 2019-2020 correlations, and Apple is silent. Nobody measured how often a reply gets a review changed.
- No ratings-to-rank curve; the 30-day window and spike filter are not Apple's; social proof thresholds untested; the "within 20%" rule did not say new or lifetime; Cal AI over MyFitnessPal is read from estimates.
- Reward-then-prompt: 4x versus 50% to 2x, games only, untested under 2026 enforcement. 5.6.4's "excessive" has no threshold. Prompt case numbers have no controlled sample. Whether a paid-install rating weighs the same as an organic one is assumed.
