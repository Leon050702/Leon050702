
# GitHub profile README — fill-in template
Paste the block below into `README.md` in your `<username>/<username>` repo, replace
every `{{TOKEN}}`, then delete the guidance.
---
```html
<!--
  Profile README for {{USERNAME}}
  Replace every {{TOKEN}}, then delete this comment.
  Name / role / tagline / handle are ALSO painted into the banner image.
  If you change them, update the CONFIG block in scripts/make_assets.py and run:
      python scripts/make_assets.py
-->
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/hero-dark.png">
  <img src="assets/hero-light.png" width="880" alt="{{NAME}} - {{ROLE}} in {{CITY}}, open to {{AVAIL_SHORT}}">
</picture>
**[Résumé]({{RESUME_URL}})** · [Email](mailto:{{EMAIL}}) · [LinkedIn]({{LINKEDIN_URL}}) · [Website]({{WEBSITE_URL}})
{{YEAR}} {{DEGREE}} student at {{UNIVERSITY}}. I build {{WHAT_YOU_BUILD}} — {{WHY_IT_MATTERS}}. Right now: {{CURRENT_PROJECT}}, and {{CURRENT_LEARNING}}.
**Open to** {{AVAIL_LONG}} — {{ROLE_TARGETS}}. {{CITY}} · {{WORK_MODE}}.
---
## 01 · Selected work
**{{PROJECT_1_NAME}}** · [demo]({{P1_DEMO_URL}}) · [source]({{P1_SOURCE_URL}})<br>
{{P1_ONE_LINER}}<br>
`{{P1_STACK}}` `{{P1_STACK}}` `{{P1_STACK}}` — {{P1_PROOF}}
**{{PROJECT_2_NAME}}** · [source]({{P2_SOURCE_URL}})<br>
{{P2_ONE_LINER}}<br>
`{{P2_STACK}}` `{{P2_STACK}}` `{{P2_STACK}}` — {{P2_PROOF}}
**{{PROJECT_3_NAME}}** · [demo]({{P3_DEMO_URL}})<br>
{{P3_ONE_LINER}}<br>
`{{P3_STACK}}` `{{P3_STACK}}` `{{P3_STACK}}` — {{P3_PROOF}}
## 02 · Stack
**Languages** — {{LANG_1}} · {{LANG_2}} · {{LANG_3}} · {{LANG_4}}<br>
**Frameworks** — {{FW_1}} · {{FW_2}} · {{FW_3}} · {{FW_4}}<br>
**Tooling** — {{TOOL_1}} · {{TOOL_2}} · {{TOOL_3}} · {{TOOL_4}}
## 03 · Proof
<!-- The four SVGs below are committed by .github/workflows/profile-cards.yml.
     Until that Action has run once, this section shows broken images.
     No Action yet? Delete section 03 entirely. -->
<table>
<tr>
<td valign="top">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/cards/stats-dark.svg">
  <img src="assets/cards/stats-light.svg" width="420" alt="GitHub stats: stars, commits, pull requests and rank">
</picture>
</td>
<td valign="top">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/cards/streak-dark.svg">
  <img src="assets/cards/streak-light.svg" width="420" alt="Contribution streak: current and longest">
</picture>
</td>
</tr>
</table>
## 04 · Elsewhere
<details>
<summary><b>Beyond the pin board</b></summary>
<br>
- **Reading** — {{BOOK}}, {{BOOK}}
- **Working in** — {{EDITOR}}, {{TERMINAL}}, {{MACHINE}}
- **Learning** — {{LEARNING_1}}, {{LEARNING_2}}
- **Off-screen** — {{HOBBY}}, {{HOBBY}}, {{HOBBY}}
</details>
<sub>Hero, palette and cards are generated inside this repo — no third-party scripts, no tracking.</sub>
```
---
## Fill guide
| Token | Write | Bar to aim for |
|---|---|---|
| `{{TAGLINE}}` (in Python) | One sentence, plain verbs | ≤ 90 characters |
| `{{WHAT_YOU_BUILD}}` | The category, not the framework | "small tools for people who live in terminals" |
| `{{WHY_IT_MATTERS}}` | The user or the constraint | "mostly things I needed and couldn't find" |
| `{{CURRENT_PROJECT}}` | Something real, dated | "shipping a deadline tracker used by 200+ students" |
| `{{AVAIL_LONG}}` | Term + year + team type | "Spring and Summer 2027 internships — backend or infra" |
| `{{P1_ONE_LINER}}` | What it does, no adjectives | "Merges three banks' CSV exports into one ledger" |
| `{{P1_PROOF}}` | A number someone could check | "200+ weekly users", "40k rows/sec", "1.2k stars" |
| `{{P1_STACK}}` | 2–4 technologies, no more | "Python · SQLite · Typer" |
## Rules that keep it looking designed
1. **Keep every `<br>`.** Markdown folds adjacent lines into one paragraph — remove them and the project list becomes a run-on wall.
2. **Three projects, three lines each.** If a block needs a fourth line, cut words, not facts.
3. **Every project needs a number.** No number means no proof — it reads as a school assignment.
4. **No emoji, no badge rows, no "still learning".** The layout carries the personality.
5. **`## 03 · Proof`** is the only section that can break. Delete it rather than ship broken images.
## If you are skipping the banner image
Replace the whole `<picture>` block with one line, and drop `assets/`:
```html
## {{NAME}} — {{ROLE}}
{{TAGLINE}}
```
