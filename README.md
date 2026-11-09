<h1 align="center">ASO Agent Skill</h1>

<p align="center">
    <img src="https://img.shields.io/badge/App%20Store-iOS%2026%20%2F%20iOS%2027-2980b9.svg" alt="App Store, iOS 26 / iOS 27" />
    <img src="https://img.shields.io/badge/version-1.0.0-blueviolet.svg" alt="Version 1.0.0" />
    <img src="https://img.shields.io/badge/knowledge%20current%20to-Nov%202026-FF2D55.svg" alt="Knowledge current to November 2026" />
    <img src="https://img.shields.io/badge/license-MIT-lightgrey.svg" alt="MIT License" />
    <a href="https://agentskills.io/home">
        <img src="https://img.shields.io/badge/Agent%20Skills-Compatible-purple.svg" alt="Agent Skills Compatible" />
    </a>
</p>

An agent skill that helps AI coding agents like Claude Code, Codex, Cursor, and Gemini do App Store Optimization for iOS apps the way a careful practitioner would in 2026: audit and write App Store Connect metadata, pick keywords that can actually be won, plan localizations as extra keyword budget, review screenshots and product pages, design custom product pages and in-app events, run a ratings strategy, set up Apple Ads and Meta app campaigns so they work with organic search instead of against it, and get the App Tracking Transparency prompt right.

It uses the [Agent Skills](https://agentskills.io/home) format, so it works smoothly with Claude Code, Codex, Gemini, Cursor, and more.


## What It Covers

- **Fundamentals** - the two-stage model (eligibility from metadata words, then ordering by new ratings in the last 30 days per storefront and by keyword placement), indexed fields and weights, word combination within a localization, token rules (word breaks, English plural stemming only, stop words), what is not indexed, screenshot captions as a reinforcing surface, index memory, visibility slots, what is and is not a ranking input, and a dated change log for 2025-2026
- **Keyword research** - the search popularity score (Apple Ads shows 1-5; keyword tools show a 5-100 log scale, re-normalized in fall 2025), difficulty as a tiebreaker, the top-5 winnability test, the research waterfall from competitors' organic keywords, intent and relevance, "AI" as a token, pruning
- **Metadata writing** - name, subtitle and keyword field rules with worked examples: keyword first and brand last, hub nouns, one idea per metadata set, do not fill the fields, the no-repeat rule and its exceptions, keep a subtitle, the organic custom product page exception for phrase entries
- **Localizations** - the storefront's indexed localizations as ten times the keyword budget, no combination across localizations, one focus per localization, the launch blueprint, device language and what the searcher sees, parked English keywords versus real translation
- **Screenshots and product page** - sequence and story, captions at thumbnail scale and the keyword reinforcement rule, real UI versus marketing slides, icon (and the contested icon-versus-screenshots lever), preview video, description and promotional text, the iOS 27 header and search assets, product page optimization tests, conversion benchmarks
- **Custom product pages and in-app events** - 70 pages per app, pages for paid traffic, pages for organic keywords since iOS 26 and the keyword-field attachment rule, page design, in-app events and result slots, pages versus product page optimization, approval and attribution limits
- **Ratings and reviews** - ratings as the ranking currency (count over stars, contested since Apple lists rating quality; 30 days; per storefront; velocity), the App Review rules on prompts and incentives, ratings as social proof, when and how to prompt, downloads-per-rating and velocity benchmarks, review text and replies, what Apple removes
- **Apple Ads** - placements and the auction (two paid search slots since March 2026), how much to spend and when to scale, campaign structure and match types, Search Match, negative keywords, keyword choice from organic ranks, bids and Apple's suggested bid over time, custom product pages per keyword theme, reading TTR, CPT, CPA and impression share, Apple Ads and organic rank, brand and competitor bidding
- **Meta Ads** - who app-install campaigns suit, creative-led targeting, aligning the ad with the product page, how view-through traffic shows up as App Store Search, web-to-app versus app install, Meta Ads and organic rank
- **Meta campaigns and measurement** - Meta's own rules for iOS app campaigns: Advantage+ app campaigns and what they can target, optimization goals and the events they need, the learning phase, budgets and bid strategies, account limits, Aggregated Event Measurement and SKAdNetwork, why Ads Manager, your attribution provider and App Store Connect disagree
- **App Tracking Transparency** - whether your app needs the prompt at all, Apple's pre-prompt rules (the ones that get builds rejected), purpose string and pre-prompt copy, timing, opt-in rates with their caveats, what consent changes for Apple Ads and Meta attribution
- **Competitor research** - which competitors to study, reading a listing, keyword gap analysis, growth signals readable from outside, review mining, turning findings into positioning
- **Measurement and cadence** - the funnel by source, the clock (hours to index, weeks to settle), change cadence, when to revert, diagnostics for a stuck or falling rank, the one-week Apple Ads conversion test, the change journal
- **Data inputs** - what every step needs (popularity, ranks, difficulty, top results, 30-day ratings, competitor keywords, metadata per localization, funnel numbers, ad reports, attribution) and how to read each without being fooled; tool-agnostic, with manual fallbacks
- **Anti-patterns** - the mistakes that keep appearing in real listings and campaigns, each with the fix


## Installing

You can install this skill into Claude Code, Codex, Gemini, Cursor, and more by using `npx`:

```bash
npx skills add https://github.com/n0an/ASO-Agent-Skill --skill aso
```

If you get the error `npx: command not found`, it means you don't currently have Node installed. You need to run this command to install Node through Homebrew:

```bash
brew install node
```

And if *that* fails it usually means you need to [install Homebrew](https://brew.sh) first.

When using `npx`, you can select exactly which agents you want to use during the installation. You can also select whether the skill should be installed just for one project, or whether it should be made available for all your projects.

### Alternative install methods

**Claude Code:**

```bash
/plugin install n0an/ASO-Agent-Skill
```

**Gemini:**

```bash
gemini extensions install https://github.com/n0an/ASO-Agent-Skill.git --consent
```

Alternatively, you can clone this whole repository and install it however you want.


## Using the ASO Skill

The skill is called ASO, and can be triggered in various ways. For example, in Claude Code you would use this:

> /aso

And in Codex you would use this:

> $aso

In both cases you can provide specific instructions if you want only part of the work. For example, `/aso Audit our App Store listing and tell me what to fix first` on Claude, or `$aso Rewrite the name, subtitle and keyword field; here is the current metadata for all localizations` in Codex.

You can also trigger the skill using natural language:

> Use the ASO skill to pick keywords for a plant identification app; we rank nowhere for "plant identifier".

> Our Apple Ads campaign spends $50 a month and shows nothing. What is wrong?

> Search traffic in App Store Connect rose with our Meta spend. Is that organic?

> Review our ATT pre-prompt and purpose string before we submit.

The skill is tool-agnostic. It states the data each step needs (search popularity, ranks per storefront, the top results for a term, 30-day ratings, App Store Connect funnel numbers, ad reports) and uses whatever keyword research, rank tracking, market intelligence or attribution tool is connected to your agent, with manual fallbacks described in `references/data-inputs.md`.


## Why Use an Agent Skill for ASO?

App Store ranking is barely documented and it moved several times in 2025-2026: screenshot captions became a ranking surface, Apple re-normalized the search popularity scale, custom product pages started serving organic keywords, the page cap doubled, and a second paid slot pushed organic visibility to the top three. Most LLM training data predates all of that and repeats older folklore. As a result, agents routinely:

- Put the brand first in the name and the searched term last, when weight falls left to right and name placement beats hundredfold rating gaps
- Repeat the same word across name, subtitle and keyword field, which keeps only the last instance
- Fill the keyword field with phrases, spaces and "app", "free" and "best", which are dropped or rejected
- Add "AI" to a name because it is fashionable, when "AI voice memo" has a fraction of the demand of "voice memo"
- Quote popularity thresholds from before the fall 2025 re-normalization
- Judge a metadata change after three days and revert, or change metadata weekly, which confuses the algorithm
- Treat ad spend as a direct ranking lever, when installs pay back in organic rank mainly through the ratings they produce
- Read a rise in App Store Search as organic growth while Meta spend is rising, when view-through users are searching the brand
- Assume the description, preview video or custom product page screenshots are indexed
- Target age and gender in Meta app campaigns, which Advantage+ app campaigns do not offer, or add an ATT pre-prompt with an "Allow" button or a reward, which gets the build rejected

This skill:

- **Dates every rule and labels its status** - rule of thumb, observed, Apple-documented, or contested with both sides given - so the agent knows what it is standing on
- **Puts the opportunity test before the tool score** - the live top-5 results and their 30-day ratings decide winnability, difficulty scores only order candidates
- **Covers the paid side** - Apple Ads, Meta app campaigns and App Tracking Transparency as they interact with organic search, not as separate disciplines
- **Checks mechanics against the platforms' own documentation** - App Store Connect Help, Apple Ads Help, WWDC and Meta's documentation decide limits, definitions and review rules; observed rules cover what the platforms never document, such as ranking weights
- **Stays tool-agnostic** - it names the data a step needs and the manual fallback, never a product to buy
- **Catches the anti-patterns** that keep appearing in real listings and campaigns, each with the fix

Scope: the iOS App Store first; Google Play only where a rule differs. Apps, not games. Ranking weights are reverse-engineered from rank data, because Apple lists the inputs but never their weights. Mechanics are checked against Apple's and Meta's own documentation as of November 2026: field limits, custom product page and test limits, metric definitions, review rules, Apple Ads behavior, Meta campaign rules and the ATT review rules. The skill decides and reviews campaigns, prompts and measurement; it does not walk through SDK integration or ad-platform click paths. Knowledge is current to November 2026; re-verify date-dependent rules against App Store Connect and Apple's documentation when they matter.


## Contributing

Contributions are welcome - whether adding new checks, updating a dated rule after Apple changes something, or fixing typos.

- Keep Markdown concise. There is a token cost to using skills, so respect the token budgets of users.
- Do not repeat things LLMs already know. Focus on what changed, on numbers, and on common mistakes.
- Keep rules dated and labeled (rule of thumb, observed, Apple-documented, Meta-documented, contested). Do not name analytics products or other tools; the skill is tool-agnostic.
- All work must be licensed under the MIT license.


## License

Available under the [MIT License](LICENSE), which permits commercial use, modification, distribution, and private use.
