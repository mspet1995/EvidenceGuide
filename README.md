# Evidence Guide
Evidence Guide is an interactive medical/psychiatric evidence grading tool for Zotero, with short questions, explanatory help, and a live score gauge which functions as an independent implementation of Dr. Chris Aiken Grading Evidence method (available at https://chrisaikenmd.com/ebm/).
Not affiliated with Chris Aiken, MD & not an official product of Dr. Aiken or Zotero. 

# Install in Zotero
Download the attached evidence-guide-1.1.0.xpi. Keep the .xpi extension; do not unzip it. 

Open Zotero, then choose Tools → Plugins.

Drag the downloaded .xpi into the Plugins window, or use its gear menu and click "Install Plugin From File…". Approve installation when Zotero asks.

Close and reopen any article reader tab that was already open. Look for Grade in the reader toolbar.

Click Grade to open the scoring window. Complete the guided walkthrough to manually score and grade psychiatric research. 

Zotero’s documented plugin installation method is to download an XPI and drag it into Tools → Plugins (
Zotero plugin instructions
). If the toolbar is crowded, or a reader tab predates installation, use Tools → Grade Article with Evidence Guide… instead.

# Compatibility and updates
The manifest targets Zotero 7 through 10. The release package was installed and exercised in a clean Zotero 10.0.2 Linux profile; Windows, macOS, Zotero 7–9, EPUB, and snapshot readers were not runtime-tested, so their compatibility is a target rather than a verified guarantee.

This is a manually distributed first release, without a hosted update service. Install a newer XPI manually when one is supplied.

Zotero requires an HTTPS update URL in the plugin manifest. This package uses a reserved .invalid address rather than an unowned real domain; Zotero may attempt an update check that cannot resolve, but there is no remote update manifest or automatic update delivery. You can turn off automatic updates for this plugin in its Plugins Manager details. The scoring code itself makes no background network requests.

# Grade an article
Choose a study design: Start with observational study or randomized controlled trial. Only relevant questions appear.

Read explanations: Hover over a grey ?, click it to keep the explanation open, or focus it with the keyboard. Each question and each answer level has help. Escape closes the explanation.

Preview a choice: Hover over an answer to see its provisional effect on the gauge. This does not save that answer. Clicking the radio button commits it; Continue remains a separate action.

Record your reasoning: Expand Add rationale or a page reference to note the relevant methods, results, or uncertainty. Answers and notes save immediately to this Zotero profile.

Move freely: Use Back, or click a criterion in the completed summary, to revise judgments. Changing the initial study design clears the old branch’s answers and notes.

Keep reading: The scoring window is modeless, so you can work in the article reader alongside it. Reopening Grade for the same attachment focuses the existing window.

The gauge uses the bands in your reference image: 1–2 very low, 3–5 low, 6–8 moderate, and 9–10 high. It shows a provisional appraisal until the required questions are finished, not the probability that a treatment works.

## Saved drafts
There is one current appraisal per attachment, keyed by library ID and attachment key. Two PDFs attached to the same bibliographic item therefore have separate appraisals.

Drafts are stored locally in Zotero preferences, not inside the PDF, not as annotations, and not as synced Zotero notes. Closing and reopening the scoring window restores your answers and rationale. Starting a new appraisal replaces the current one after confirmation; export the old review first if you want a history.

Uninstalling the plugin does not intentionally delete its saved preferences. Exported workbooks remain ordinary files wherever you saved them.

## Observational quality walkthrough
At step 3, expand Walk through the quality components. Review adequate sample size, control of confounders, prospective design, and additional support; each has a dropdown and its own explanatory ?.

Choose Yes or No where the evidence supports a judgment. Unclear / not reported and Not applicable prevent missing information from being forced into a binary answer. Component responses are saved with the appraisal and included in the Excel export.

These are supporting judgments, not extra points. Choose Higher, Typical/mixed, or Lower quality yourself after weighing the importance of the findings; there is no automatic majority-vote score. The supplementary size, confounding, and design explanations draw on 
NHLBI’s study quality assessment guidance
, while the original overall adjustment remains unchanged.

## Export to Excel
Finish the questions, review the summary, then click Export Excel and choose a location. The output is a genuine .xlsx workbook, not a CSV renamed as Excel.

The workbook has three standard sheets, plus a fourth for observational appraisals:

Summary: Article metadata, Zotero attachment identifier, study design, starting score, raw arithmetic or override, final score, evidence band, export time, and rules version.

Scoring: Each criterion and question, your selected answer, point change or special action, running totals, rationale/page references, answer guidance, and the original method URL. Criteria bypassed by the early-stop rule are marked as not scored.

Method notes: The implementation choices and limitations described below, with the original method URL.

Quality walkthrough (observational only): Component questions, your judgments, detailed guidance, and its source URL. No component-level points are assigned.

Scores are numeric cells. Reviewer text is written as text rather than spreadsheet formulas. Cancelling the Save dialog leaves the draft unchanged.

# Description of Method Implementation
Randomized trials begin at 10 and lose points for the listed methodological concerns; observational studies start at a design-specific level and receive an overall quality adjustment. The plugin covers the RCT criteria, observational baselines, explanatory guidance, and special early-stop rule on that page.

The original method leaves some discretion or ambiguity. These choices are explicit in the plugin’s Method panel and exported workbook:

Judgment within a range: The original ranges remain selectable. Short labels such as “stronger impact” are interface guidance, not additional validated thresholds. Select a point level using the article and the fuller help text.

Zero deductions: Zero means a flaw is absent or nonmaterial. When a relevant flaw is present, use its listed nonzero range.

Inconclusive outcomes: The special “more than 50% negative AND inconclusive” outcome case sets the score to 2. It replaces preceding deductions, ends the RCT checklist, and prevents further deductions. It is not merely a two-point deduction.

Minimum score: The page describes converting a score below zero to 1, but does not resolve exactly zero despite using a 1–10 scale. This implementation floors every raw total below 1, including zero, at 1; the workbook preserves the raw arithmetic.

“Other” concerns: Plausibility, relevance, and population fit are unnumbered items beneath the source’s final checklist heading. Here, each is a separate optional one-point deduction, an interpretation rather than an explicit independent point value in the source.

Observational adjustment: High quality adds 1, low quality subtracts 1, and typical/mixed quality leaves the baseline unchanged. The neutral option makes the workflow usable without forcing a high/low judgment; it is an explicit implementation choice. Only one overall adjustment applies.

Observational maximum: A dramatic observational finding can start at 5 and gain 1 for quality under the source’s rules. A resulting 6 is shown in the moderate band; the color does not redefine its design as randomized.

Exactly 40 participants: The source’s less-than/greater-than 40 example leaves this boundary unspecified. The help flags this instead of inventing a hard threshold.

This educational appraisal tool is not formal GRADE, is not clinically validated, and does not establish treatment efficacy, safety, or a patient-specific recommendation. It deliberately requires a reviewer’s judgment rather than presenting a score as objective truth.

# Optional AI scoring assist
A small AI scoring assist button helps with the current question only. It never reads or uploads the entire PDF automatically and never changes an answer without a reviewer’s action.

## Easiest option: browser handoff
Click AI scoring assist.

Paste the published article’s methods or results passage relevant to the current question.

Click Copy prompt, then Open ChatGPT.

Paste the prompt into your own chat when you are ready to share it.

Review the response against the article and select the answer in the wizard yourself.

This requires no API key. ChatGPT offers a free tier with usage limits; provider account requirements, availability, and privacy terms apply (
OpenAI free-tier FAQ
).

The AI window explains its purpose first, then shows three short ChatGPT steps. Its ? contains response-format details and sharing behavior; expand Use local Ollama instead for that option’s three-step process and separate detailed help.

Opening ChatGPT alone does not send the excerpt. Pasting and submitting the prompt does share it with that provider; use only material you are permitted to share.

## In-window suggestions: optional local Ollama
If you already have Ollama running with a downloaded local model, expand In-window suggestions with local Ollama, click Find installed models, choose one, and check the explicit consent box. Then click Suggest for this question.

The plugin connects only to http://127.0.0.1:11434, the default local Ollama service, and uses its model-list and chat endpoints; local API access does not require a key (
Ollama API documentation
). Models identified as cloud/remote are excluded, and the plugin does not install software or download models for you.

It displays the suggested option, rationale, evidence quote, and uncertainty when the response is usable. Use this suggestion is a separate confirmation that applies the option and records an AI-assisted note; you can edit it afterward. Missing evidence or malformed responses do not silently assign a score.

Local model installation is optional and outside the zero-setup manual workflow. No live Ollama model was available for end-to-end inference testing in this build; that integration is implemented but should be treated as experimental.

# Privacy and permissions
The plugin uses normal Zotero desktop-plugin privileges to read the selected item’s metadata, store drafts, open its window, copy prompts when asked, and save a workbook to a chosen path. It includes no analytics, remote scripts, automatic article extraction, or background AI calls.

Manual scoring and Excel creation operate offline. The only scoring-code network actions are explicitly opening the method page or ChatGPT, or requesting a local Ollama model list/suggestion; Zotero’s own plugin update checks are separate. AI excerpt text is not stored in the draft, although an explicitly accepted local suggestion saves its rationale and evidence quote.

# Testing completed
Release installation: The actual production XPI installed and activated in Zotero 10.0.2 on Linux, separate from the test-instrumented build.

Native reader: Reader toolbar injection, modeless window, correct article metadata, score updates, fixed-score early termination, local draft/rationale restoration, and Tools fallback passed.

Lifecycle and isolation: Separate attachments retained separate appraisals. Disabling the plugin removed its toolbar button, Tools menu item, and open scoring windows; re-enabling restored its operation.

Native Excel: Generated a workbook from the installed plugin and saved through Zotero’s native Save dialog. Independently read the resulting Excel workbook with openpyxl.

Rules and workbook tests: All 15 automated tests passed, including all observational combinations, deduction arithmetic, floors, changing answers, cross-branch isolation, non-scoring component checks, and ZIP checksums.

Version 1.1 upgrade: The production update preserved an existing RCT draft. The new observational dropdowns saved and restored correctly, left the score unchanged until an overall choice, and exported their own workbook sheet. The revised AI instructions and help also rendered in native Zotero.

Browser interaction: Tested complete RCT and observational paths, answer previews, tooltips, keyboard controls, editing, restart, dark mode, 375-pixel mobile layout, and exported workbooks. The preview and installed plugin share their rules and UI code.

Not tested: real Ollama inference, macOS/Windows execution, older Zotero versions, EPUB/snapshot readers, or automated compatibility with future Zotero releases. This first release has no code-signing identity, hosted updater, cloud synchronization, batch grading, or automatic PDF analysis.

# Troubleshooting
No Grade button: Close and reopen the reader tab, check the plugin is enabled, or use the Tools fallback. Restart Zotero if needed.

Download opens as an archive: Do not extract it. Install the .xpi through Zotero, not a web browser’s extension manager.

Unsupported Zotero version: This build declares support for versions 7–10 only. A future major version needs a compatibility review and updated manifest.

Draft does not follow you to another device: This is expected; drafts are local. Export an Excel record before moving devices.

No local models found: Ensure Ollama is running and has a local model downloaded. Browser handoff and all manual scoring still work without it.

Save cancelled or failed: Your draft remains. Retry Export Excel and choose a writable destination.

Method changes later: This build uses a fixed rules snapshot, aiken-2026-09-16.v1, not a live scrape. Reappraise when the rules change rather than silently mixing versions.
