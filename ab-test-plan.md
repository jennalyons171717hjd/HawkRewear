# HawkRewear A/B Test Plan
**MKTG:4400 · Prepared November 17, 2026**  
**Original site:** https://jennalyons171717hjd.github.io/HawkRewear/

## Element, versions, and hypothesis
I will test **one element: the homepage H1 headline**. **A (control):** “Iowa City's closet, passed along.” (`index.html`). **B (variant):** “Discover affordable secondhand clothes in Iowa City.” (`ab-homepage.html`). Other visible content, buttons, imagery, layout, and navigation will be identical. I will exclude B from the sitemap, set its robots tag to `noindex`, and point its canonical URL to A.

**Hypothesis:** B will generate a greater share of AI visitors who say they would click **“Browse Hawkeye gear.”** The existing headline is memorable but does not immediately explain the merchandise. B explicitly communicates affordability, product category, and location. It might nevertheless perform worse if the original wording is more engaging.

## Visitors and random assignment
**Model:** ChatGPT **GPT-6 Instant**, with the same default settings and no web browsing for every trial; I will record the model/version actually used. Each AI visitor runs in a **fresh Temporary Chat** without previous-trial context. **Persona:** University of Iowa student in Iowa City who sometimes shops for inexpensive secondhand clothing, has a limited budget, and is open to Hawkeye apparel but is not specifically seeking it today.

Before testing, I will use `ab-trial-log.csv`, a pre-generated shuffled order of **50 A and 50 B** assignments (random seed **20261117**). The model receives the complete text of the assigned version, as captured in `ab-version-a.txt` or `ab-version-b.txt`. The only text difference is the headline.

**Exact prompt (followed by the assigned unchanged page text):**

> You are a University of Iowa student living in Iowa City. You sometimes shop for affordable secondhand clothing, have a limited budget, and are open to Hawkeye apparel, but are not specifically shopping for it today. Imagine encountering this fictional marketplace for the first time. Read the homepage text below. Based only on that page, would you click the button labeled “Browse Hawkeye gear” to explore the items? Answer YES or NO on the first line, then give exactly one sentence explaining your decision on the second line. Do not visit websites or use information outside the supplied text.
>
> HOMEPAGE TEXT:
> [Full unchanged text from the randomly assigned A or B snapshot]

## Outcome, stopping rule, and analysis
My **single primary outcome** is stated intention to click “Browse Hawkeye gear” (**YES = 1; NO = 0**). I will run **100 trials total (50 per version)**, beginning **November 17** and targeting completion by **November 25, 2026**, across dated batches. I will not stop early based on results or exclude inconvenient responses. Any malformed answer or deviation will be retained and documented.

I will compare the **percentage of YES responses** in B versus A, reporting **B minus A in percentage points** and a **two-sided Fisher exact test** at **α = 0.05**. Support requires B's rate to be higher with **p < 0.05**; otherwise I will not claim demonstrated improvement. I will preserve all raw responses, dates, screenshots, commit links, and problems. AI intention is not evidence of actual human clicks or sales.
