# App Tracking Transparency

App Tracking Transparency (ATT) makes an app ask through a system prompt before it tracks a user across other companies' apps and websites or reads the advertising identifier. For a marketer it decides what paid channels outside the App Store can attribute: without consent, Meta and other networks fall back on aggregated measurement (AdAttributionKit or SKAdNetwork, Meta's Aggregated Event Measurement), while Apple Ads attribution through AdServices does not depend on the prompt. The pre-prompt sits in onboarding next to the rating prompt; treat its review rules as hard constraints and the copy and timing advice as tactics. Apple's and Meta's documentation (current November 2026) wins on mechanics; copy patterns date from 2021 and opt-in numbers are industry samples, never Apple figures.

## Decide whether the app needs the prompt

- Tracking means linking user or device data from your app with other companies' apps, websites or offline data for targeted advertising or advertising measurement, or sharing it with a data broker (Apple-documented).
- On iOS, iPadOS and tvOS 14.5 or later, tracking or reading the advertising identifier needs ATT permission. Without it the identifier is all zeros and no other tracking method is allowed (Apple-documented).
- Every identifier counts: advertising identifier, session ID, hashed email or phone number, fingerprint or device-graph IDs (Apple-documented).
- You own your SDKs' behavior. An SDK that combines your users' data with other developers' data for ads makes your app a tracker even if you never use that feature; so does single sign-on that tracks. Some SDKs track by default until told otherwise (Apple-documented).
- Deep-linking tools need ATT when they pass unique identifiers or build a shared identity across companies for ads or data brokers. Tracking in a webview that serves app functionality is app tracking unless it lets the user browse the open web (Apple-documented).
- Exempt: linking data only on the device; broker sharing solely for fraud prevention or security; credit reporting; the identifier for vendor (IDFV) across your own apps, if not combined to track across companies (Apple-documented).
- Website consent does not cover in-app tracking. Legal consent screens may run alongside ATT, but the ATT answer always wins; such a control should say so and show the current ATT status (Apple-documented).
- If nothing tracks, do not show the prompt. Calling ATT "mandatory for all applications which collect data" overstates it (contested, Apple governs).

## The system prompt, the purpose string and re-prompting

- The app must include the NSUserTrackingUsageDescription key (the purpose string) or it crashes; the string sits between the app name and the buttons (Apple-documented).
- Write one brief, specific sentence in sentence case and active voice, ending with a period, without the app name, saying what the data is used for (Apple recommends). Apple's model for any permission: "The app records during the night to detect snoring sounds." Its bad examples: "Microphone access is needed for a better experience." and "Turn on microphone access."
- Guideline 5.1.1(ii): purpose strings must clearly and completely describe the data use (Apple-documented).
- Answers: authorized, denied, restricted (cannot be asked) or notDetermined (dismissed without a decision; call again). The system silently skips the prompt when tracking is restricted, the user turned off "Allow Apps to Request to Track", a request is pending, the call comes from an extension or the app is not active; a request fired during launch is lost (Apple-documented).
- Child accounts and shared iPads can never be asked (Apple-documented, as of 2020). Users can change the answer in Settings any time: check the status every launch, never cache it (Apple recommends, 2020).
- Outside the EU: after notDetermined, call again; after a denial, offer a Settings shortcut; nothing else is documented (Apple-documented). "The prompt fires only once" holds only there, for a user who answered (dated: 2021).
- In the EU: the system blocks the prompt for a year after any answer, then the app may ask again, accept or reject, unless the user turned off the request switch ("Allow Apps to Request to Link Your Activity Across Companies") (Apple-documented).
- EU alternative prompt (Apple-documented, timing contested): one Apple page says developers "will have the option" from iOS 27.2 and iPadOS 27.2, with new formatting and an optional "Additional Information" button, the only version allowed in Germany, France, Italy, Poland and Romania; the framework reference describes a full-page sheet there as current, with an optional NSUserTrackingMarkdownUsageDescription for rich text. When permission is required does not change.
- In the layered prompt, put the key information in the purpose string and say what Additional Information offers; nothing may be used until the user allows in the ATT prompt itself (Apple-documented).
- Do not show the ATT prompt to users who opted out of all relevant legal consent choices; the string may refer to consent already given (Apple-documented).

## Pre-prompt hard constraints (App Review Guidelines, Apple-documented)

Not tactics: breaking one gets the build rejected, and sharing data without consent can remove the app from sale and the developer from the Apple Developer Program.

- **Transparent explanation only (5.1.1(iv)).** A custom screen before the prompt may explain the data use; manipulating, tricking or forcing consent is banned.
- **No gating, no incentives (5.1.2(i), 5.1.1(ii)).** Never require tracking to use the app, its functionality or content, or to receive money or compensation, gift cards and codes included. Paid functionality must not depend on data access.
- **No look-alikes, no steering.** Rejected: an incentive (Apple's example: "get a $100 credit"), an "Allow Tracking" button that mimics the request, an image of the system alert, annotations behind the alert (an arrow with "Choose Allow"), anything that confuses, misleads or exploits quick tapping.
- **One button that opens the alert.** "Continue" or "Next", never "Allow" or anything similar in meaning or visual weight.
- **No exit that skips the alert** (close, cancel, "Not now") unless a legal consent requires it. A "Don't allow" option that withholds the prompt for later (observed, 2021) is ruled out.
- **Legal consent screens are allowed** before or after the alert. An app that tracks from launch shows the alert before collecting tracking data. No repurposing data without further consent.
- Parallel with ratings, where only the system prompt may ask (`references/ratings-and-reviews.md`): a pre-prompt may explain, but nothing on your screen may steer the tap.

## Writing the pre-prompt and purpose string

Written in the weeks after iOS 14.5 shipped and never measured: each rule is a rule of thumb, dated: 2021, unless marked, and must still pass the hard constraints.

- Spend the effort on the pre-prompt; the system prompt holds one sentence.
- Open with what is happening, why the app interrupts and what it asks. Confused users mostly decline, knowing they can opt in later.
- Lead with the user's benefit; "personalized ads" is not one. Keep the tone positive.
- Do not exaggerate: Meta's early pre-prompt implied that opting in keeps its apps free. Overclaiming also collides with 5.1.1(iv).
- Keep it short: one intro sentence, three short benefit bullets. No threats about declining, no tapping instructions.
- Purpose string: the main benefit in the user's words, no "Identifier for Advertisers (IDFA)" jargon, vendor names or scare lines. Without a pre-prompt it is the only persuasive copy.
- Put benefit and use in one sentence: a benefit without the use fails 5.1.1(ii) (Apple-documented); the developer's gain alone converts badly.
- Worked example (untested; check every claim against the SDKs): pre-prompt "Next, iOS will ask whether we may use your activity from other companies' apps and websites.", three true benefit bullets, one "Continue" button. Purpose string: "Your activity from other companies' apps and websites is used to show you more relevant ads and to measure which of our ads work."
- Iterate: study other apps' prompts, test versions like screenshots, change one element at a time, and judge by installs, revenue and ad performance, not opt-in alone. ATT copy is a growth lever beside ASO, not part of the listing (rule of thumb, 2026).

## Timing

- The app may prompt whenever it chooses; the identifier comes back only after the user allows (Apple-documented).
- Apple's general permission advice: ask at the feature that needs access, not at launch unless the app needs the data to function (Apple recommends, not ATT-specific).
- Onboarding placement (contested in emphasis only): tracking is not a feature the user reaches, so teams put an explanation and the alert in onboarding (rule of thumb, 2023; observed common, 2026). Apple's ATT text allows it for apps that track from launch.
- Request only with the app active, and hold tracking SDKs until the answer; Meta tells older-SDK users to initialize after consent (Meta-documented).
- The rating prompt has its own timing rules: check it against `references/ratings-and-reviews.md` whenever onboarding changes.

## Opt-in rates and how to read them

Every figure is one vendor's or publisher's sample, with no stated sample size or denominator (per prompt shown or per install). Apple publishes no ATT opt-in rate. Use them as dated context, never as a target.

- Q2 2023, one vendor's client sample (industry data, 2023): average 34%, up from 29% at an undated earlier check. Gaming 37%, food and drink 36%, e-commerce 34%, fintech 29%, social 26%, travel 25%, entertainment 25%, education 7%.
- Games: hyper casual 44%, sports 43%, racing 40%, hybrid casual 39%; family 2%, educational 4%, music 8%, casino 15%, trivia 16%.
- Countries: UAE 49.6%, Brazil 47%, Vietnam 45%; Germany 20%, Japan 22%, Australia 23%, Canada 23%, United States 24%, Italy 24%.
- Cross-promotion: hyper casual installs from the publisher's other apps opted in at 59% against 44%; multi-app publishers can test it, expecting a few points elsewhere (rule of thumb, 2023).
- 2026 figures (contested, treat as undated): under half of users opt in, games 39%, UAE near 50%, no period or sample. Possibly recycled: the UAE matches 2023's 49.6%.
- Personalized Ads is a different consent, Apple's ad-personalization setting, prompted since iOS 15: 78% of App Store search volume on iOS 17+ came from devices with it off (Apple-documented). Its effect on audiences: `references/apple-ads.md`.
- Plan for a consenting minority and center measurement on AdAttributionKit or SKAdNetwork (rule of thumb, 2023). Measure your own rate as authorized answers over prompts shown.

## What consent changes for attribution

- Without consent the network receives no user ID and learns nothing about the conversion (Apple-documented, 2020).
- Web onboarding to avoid ATT limits on paid attribution (observed, 2025) moves attribution off the device; it does not license in-app tracking (Apple-documented).

### AdAttributionKit and SKAdNetwork (no permission needed)

- Apple verifies that enough users converted, then a signed report tells the network only that a campaign moved some number of users (Apple-documented, 2020). Since 2021: view-through ads, postbacks to a winner plus up to five runner-ups, a copy for the developer (Apple-documented, 2021, may have changed).
- AdAttributionKit, built on and interoperable with SKAdNetwork, measures installs since iOS 17.4 and re-engagement since iOS 18. Apple urges migration and says it covers 77% of referral-based App Store conversions (Apple-documented).
- Crowd anonymity: at low volume the publisher app ID drops, source identifiers shrink from 4 digits to 2, and conversion values arrive coarse (low, medium, high) or not at all (Apple-documented). Small campaigns get thin data.
- Fine values run 0 to 63 over three windows; locking ends a window, delivery is randomly delayed (Apple-documented). Design the schema with each network and your attribution provider, and lock on the highest-value early event (Apple recommends).
- As of 2025: clicks under 30 days and views under 1 day compete by default, windows and cooldowns are configurable, and a storefront country code arrives only in a bonus tier above four crowd-anonymity tiers (Apple-documented).
- Web ads: Private Click Measurement is on-device, outside ATT (Apple-documented, 2021).

### Apple Ads (AdServices)

- Works without the prompt: Apple said in 2020 it does not track across companies; AdServices uses first-party data, sends no user or device identifier, attributes to keyword level and keeps data 21 days (Apple-documented). Apple's ATT pages do not tie the token to the ATT answer.
- Unrelated limits: age or gender ad groups return no attribution; AdServices and other networks can claim the same install, with AdAttributionKit the official last click; Apple Ads registered with AdAttributionKit on April 10, 2025, click-through only (Apple-documented). Detail: `references/apple-ads.md`.
- App Store Connect documents no ATT opt-in report and no postbacks; postback copies go to an endpoint you declare (Apple-documented).

### Meta (Aggregated Event Measurement)

- iOS 14.5+ app promotion campaigns are "iOS 14+ campaigns", attributed by Aggregated Event Measurement (AEM) or SKAdNetwork. AEM covers opted-out users by removing identifiers, adding differential privacy and aggregating (Meta-documented).
- AEM now covers app promotion, rolling out per account: no SKAdNetwork event setup required, more optimization events, SKAdNetwork optional for a cross-platform view (Meta-documented, November 2026). Older "set up SKAdNetwork events first" advice is stale for those accounts.
- With app event or value optimization, AEM campaigns get 1-day and 7-day click reporting, the 7-day click window and Audience Network delivery; custom event optimization is unsupported (Meta-documented).
- Since October 9, 2024, measurement partners receive AEM data. Meta's iOS SDK 17.0.0+ on iOS 17+ reads ATT status itself; older SDKs and server-side events need a per-event opt-in flag (Meta-documented). Setup: `references/meta-ads.md`.
- Limits (documented in 2023, not restated in current help pages): 8 conversion events for AEM and 9 campaigns / 5 ad sets per app. Treat them as a possible ceiling.
- Expect smaller custom audiences; Meta suggests broad targeting. Never compare AEM and SKAdNetwork results line for line (Meta-documented).

## Enforcement beyond the prompt

- Privacy labels: each app and update declares its practices, SDK data included; the product page shows "Data Used to Track You" before download (Apple-documented). Review it with the screenshots (rule of thumb).
- Privacy manifests: SDKs declare data use and tracking, and Xcode's privacy report feeds the label; listed SDKs need a signed manifest, enforced from spring 2024 (Apple-documented, as announced in 2023).
- Since iOS 17 the system blocks declared tracking domains for users who declined; split dual-use domains (Apple-documented).
- Banned even with consent: fingerprinting, collecting installed apps for advertising, re-identifying anonymized data, advertising use of HealthKit, HomeKit or face data (Apple-documented).

## Procedures

1. Tracking decision: list SDKs and services receiving user data; check each manifest and defaults; rule out exemptions. Nothing tracks: no prompt, no tracking declared, measure via AdAttributionKit and AdServices. Anything tracks: purpose string, SDKs gated on authorized, tracking domains declared, label matched to the privacy report.
2. Copy: write the purpose string (use plus benefit); add a pre-prompt only if the moment does not explain itself; run the hard-constraint gate; check claims against SDK behavior.
3. Placement: app active, expected moment; re-call on notDetermined, Settings on denied; EU re-prompt after a year. After launch track opt-in, installs, revenue and ad performance.
4. Channel brief: no age or gender on Apple Ads ad groups needing attribution; Meta attribution method, optimization event and SDK opt-in handling confirmed; one conversion value schema per network.

## Dated changes

- 2020 (WWDC20): ATT announced. April 2021: enforcement with iOS 14.5; copy rules written soon after.
- 2023: privacy manifests and domain blocking (WWDC23); 34% opt-in for Q2; Meta documents AEM limits.
- 2024: AdAttributionKit with iOS 17.4; Meta SDK 17+ reads ATT; AEM data to partners from October 9.
- April 10, 2025: Apple Ads joins AdAttributionKit.
- November 2026: Meta's per-account AEM for app promotion; Apple documents the EU prompt and one-year re-prompt.

## Checks

- Every SDK, deep link, sign-on and webview classified? Prompt shown without tracking? SDKs tracking before the answer?
- Purpose string: one active sentence, use plus benefit, no app name, jargon or vendor names?
- Pre-prompt: one "Continue"/"Next" button; no "Allow", skip exit, incentive, gate, threat, alert image or arrow?
- Request only when active; notDetermined, denial and EU re-prompt handled?
- Opt-in measured over prompts shown; industry figures read as dated samples?
- Label matches the privacy report; tracking domains declared?
- Apple Ads age or gender settings? Meta method, event and SDK flag confirmed?

## Open questions

- Is the EU alternative prompt live, and does the one-year re-prompt depend on it?
- Outside the EU, no documented re-ask after an answer.
- Whether Meta's 2023 AEM limits still apply.
- No opt-in data with stated sample or denominator; no measured pre-prompt lift; testing and localizing copy undocumented.
- Apple Ads attribution for declined users rests on Apple's 2020 statement.
- Which web-collected data stays out of ATT scope after install is unmapped.
