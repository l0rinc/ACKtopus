<h1><img src="screenshots/acktopus-logo.svg" alt="ACKtopus" width="28" height="28"> ACKtopus</h1>

ACKtopus is a GitHub userscript for [Tampermonkey](https://www.tampermonkey.net/) that adds a floating review toolbar, context-copy tools, LLM review recipes, proofreading, pending-review helpers, and queue/navigation shortcuts on GitHub pull requests and issues (optimized for Bitcoin Core-style review).

## Highlights

<img src="screenshots/floating%20acks.png" alt="Floating ACK toolbar and ACK panel">

_Floating toolbar with ACK/NACK parsing and jumpable review signals._

----

<img src="screenshots/tooltip%20on%20selection.png" alt="Selection helper tooltip">

_Selection helper with quick explain/fact-check/simplify/proofread actions._

----

<img src="screenshots/pr%20lightbulb.png" alt="PR lightbulb overview">

_PR lightbulb overview with high-level context and reviewer-oriented guidance._

----

<img src="screenshots/copy%20context.png" alt="Context copy actions">

_Clipboard-ready PR, commit, and comment context for sharing or LLM use._

----

<img src="screenshots/start%20review%20from%20reply.png" alt="Start review from reply">

_Pending-review helpers directly from Conversation replies and the main comment box._

----

<img src="screenshots/comment%20feedback.png" alt="Comment feedback">

_Pending-comment feedback that simulates the likely author response before you post._

----

<img src="screenshots/per%20PR%20clipboard%20commands.png" alt="Per-PR clipboard commands">

_Per-PR clipboard helpers for ACKs, checkout, range-diff, and review commands._

----

<img src="screenshots/commit%20lightbulb.png" alt="Single commit lightbulb">

_Single-commit lightbulb with summary, why-it-matters, pseudocode, and concerns._

----

<img src="screenshots/commits%20lightbulb.png" alt="Commits page lightbulb">

_Commits-page lightbulbs showing how each commit fits into the stacked PR._

----

<img src="screenshots/comment%20lightbulb.png" alt="Comment lightbulb">

_Comment explanation in context for understanding review remarks quickly._

----

<img src="screenshots/chat%20with%20navigation.png" alt="Chat panel with navigation">

_LLM chat panel with page context and navigation-aware review assistance._

----

<img src="screenshots/proofread.png" alt="Proofread flow">

_Proofread flow with diff-style review before applying text changes._

----

<img src="screenshots/commit%20review%20prefix.png" alt="Commit review prefix">

_Automatic commit prefix on single-commit views so inline comments stay revision-specific._

----

<img src="screenshots/compare%20closing%20unrelated.png" alt="Compare page focusing unrelated files">

_Compare-page cleanup that collapses unrelated files and keeps focus on the PR-relevant diff._

----

<img src="screenshots/expand%20closed%20sections.png" alt="Expand closed sections">

_Bulk expansion of hidden, minimized, outdated, or otherwise collapsed review content._

----

<img src="screenshots/navigate%20to%20comment.png" alt="Comment navigation">

_Chronological comment navigation for quickly walking long review discussions._

----

<img src="screenshots/queue.png" alt="Queue panel">

_Personal review queue for pull requests you want to revisit later._

----

<img src="screenshots/settings.png" alt="Settings panel">

_Settings for tokens, providers, maintainer list, caches, and compact toolbar behavior._

## What it helps with

- Tracking ACK/Concept ACK/NACK signals and jumping back to the source comments
- Copying ACKs, checkout commands, range-diffs, local pre-push range-diffs, and focused test/format commands
- Copying PR, issue, commit, patch, comment, and visible discussion context to the clipboard
- Revealing hidden conversations, resolved threads, minimized comments, outdated sections, and deferred diffs in bulk
- Navigating long PRs by comment, file, and commit
- Reviewing with LLM chat, local reproducer prompts, maintainer summaries, commit lightbulbs, selection helpers, and cached PR/commit infographics
- Proofreading comments, PR descriptions, selected prose, and draft PR text with a diff preview before applying changes
- Starting/submitting pending GitHub reviews from the Conversation tab
- Keeping a personal PR review queue

## Toolbar (top-right)

### 👥 ACK panel

Shows detected ACKs/Concept ACKs/Approach ACKs/NACKs/Stale ACKs and lets you jump to the comment that contained them. Repository members are highlighted, configured maintainers get stronger highlighting, and PGP-signed ACK details can show verification badges when a key is available.

### SHA / ACK copy

Copies useful snippets based on the PR head commit, such as:

- `ACK <sha>`
- `git fetch ... && git switch --detach FETCH_HEAD`
- all PR commit hashes copied as one oldest-first, space-separated string
- checkout-parent and `gh pr co ... && git pull --rebase "$REMOTE" <base>` helpers, with `upstream`/`origin` remote fallback
- `git range-diff` from your last ACK or the latest quick force-push burst
- rebase-both-sides-and-diff commands for cleaner force-push burst comparisons
- pre-push `git range-diff "$BASE..@{u}" "$BASE..HEAD"` for comparing the pushed tracking branch with local `HEAD`
- benchmark, unit-test, fuzz, and functional-test commands when changed files make those targets discoverable

These buttons always **copy to your clipboard** (they never insert text into a comment box).

Tip: hold **Ctrl** for ~0.5s to show the hotkey chooser. Press the letter to copy that format, or press **Enter** to copy the currently selected format (the one shown on the main SHA button).

If the PR changes C/C++ files, additional per-PR helpers appear:

- `clang-format-diff`: apply formatting only to changed lines
- `clang-tidy-diff`: run clang-tidy only on changed lines
- `IWYU (changed)`: run include-what-you-use only on changed `src/*.h` / `src/*.cpp` files

These three commands are generated with the PR’s exact changed C/C++ file paths already filled in, so they are ready to run as-is.

### 📦 / 📂 / 🪟 Expand dropdown

The expand control can run three related actions:

- **Show hidden**: loads hidden conversation/comment pagination
- **Show resolved**: expands resolved review threads
- **Open collapsed**: opens minimized comments, outdated sections, and “Load diff” buttons for large diffs

The context-copy dropdown also has **Reveal all**, which walks through hidden conversations, resolved threads, collapsed sections, and deferred diffs before copying.

### 💬 Comment navigation

Jumps between comments by date on PR pages, and between visible files on compare pages. Hold **Shift** to reverse direction. The delayed Ctrl hotkey chooser exposes this as **Ctrl+N** after the chooser is armed.

### 📎 Context copy

Copies page context to your clipboard for sharing or pasting into an LLM. The dropdown supports:

- **Patch**: PR description, commits, and patch
- **Comments**: description plus visible comments, without the patch
- **Full**: URL, title, description, commits, patch, and visible comments
- **Reveal all**: expands hidden/resolved/collapsed content before copying

Hold **Shift** while clicking **Patch**, **Comments**, or **Full** to reveal hidden/resolved/collapsed content first, then run the chosen copy action. ACKtopus shows a 📂 hint next to the active context-copy button while Shift is held.

On single-commit pages like `/changes/<sha>` and `/commits/<sha>`, the same button copies **commit-only** context instead: the parent PR metadata/description, the current commit patch, and visible comments tied to that commit.
Each comment’s `...` menu also gets a **Copy comment context** action, which copies just that comment plus its surrounding thread and location metadata (file, line, commit, author, permalink).

### 🤖 Robot recipes / Chat

Opens a robot panel backed by the active Claude, ChatGPT, or Gemini provider. The dropdown supports:

- **Chat**: ask about the page, use `/find ...` to navigate visible comments/code, or use `/quiz` for high-leverage review questions
- **Reproducer**: generate the direct outcome-focused local-agent prompt for a no-peek reimplementation only, omitting raw patch and comment context from the LLM request
- **Suggestions**: generate the follow-up local-agent prompt for splitting the actual PR, rebasing the local reproducer, and adding evidence-backed suggestion commits
- **Audio guide**: generate a direct audio-agent prompt that tells the audio-enabled assistant to investigate the PR itself before starting the discussion
- **Maintainer view**: summarize mergeability, unresolved threads, reviewer positions, and suggested maintainer focus
- **Infographic**: generate a cached OpenAI PR or current-commit infographic for a high-level visual overview

Hold **Shift** while clicking copyable recipes such as **Reproducer**, **Suggestions**, **Audio guide**, or **Maintainer view** to copy the exact LLM request prompt instead of running the recipe. Shift-clicking **Infographic** copies the visual prompt without generating the image. ACKtopus shows a 📋 hint next to those recipe buttons while Shift is held. The comment/file jump button shows an ⬆ hint while Shift is held because Shift reverses navigation direction.

Chat answers can cite visible comments/code with clickable `[ref:N]` links. For explain/proofread/fact-check flows, ACKtopus includes PR-level context (description, commit messages, and PR-body diff context) with larger context windows to improve response quality while regular comment proofreading stays focused on the PR description, commit messages, thread, and local code context instead of attaching the full unified diff. Reproducer, Suggestions, Audio guide, and Maintainer view prompts also show the exact generated system/user prompt in a collapsible section so they can be inspected or reused directly. The generated Reproducer prompt now stops at the no-peek local rediscovery artifact: it omits raw patch and raw comment context from the prompt-generation LLM call, strips fenced source blocks, uses commit metadata only to create high-level commit-by-commit target jobs, uses a smaller Claude-safe source and output budget, forbids existing code, raw PR comments, patch text, and submitted-implementation details in the generated prompt, asks for local commits and verification, and tells the target agent to stop before any actual-PR comparison. Its final checks are target-agent work checks, not self-referential checks about prompt generation. It also asks for follow-up handoff notes so later dedicated Suggestions, Audio guide, Infographic, or Maintainer prompts can start from a simpler final report. When a PR is too large for the prompt context, the Reproducer source context is explicitly marked as truncated and the generated prompt tells the target local agent to treat ACKtopus context as a problem-evidence index, fetch only no-peek-safe missing metadata before approval, and mark missing evidence instead of guessing. The Suggestions prompt is the approved follow-up: it asks the local agent to inspect and split the actual PR where useful, prove split/squash equivalence, rebase or replay the local rediscovery work on top, and add each meaningful difference as the smallest possible suggestion commit with a review-comment-style commit message and GitHub evidence URLs. The standalone Audio guide prompt is now meant to be pasted directly into the audio-enabled assistant: it tells that assistant to use ACKtopus context, GitHub/internet access, and the ACKtopus-attached patch to investigate the PR, commits, review threads, hard parts, tests, and evidence links itself, then respond only with the OK gate once it has enough data to start the spoken discussion. It still includes a local-agent fallback if the same prompt is used in a checkout, but it no longer asks a local agent to generate a separate handoff document first. ACKtopus omits the patch from the prompt-generation LLM call, fetches the PR patch itself afterward, and appends it below the generated prompt as source evidence so no model has to print the patch back. It ends with an OK-only gate so the user can paste it first and start audio mode afterward.

The infographic flow first asks OpenAI to distill the source into a semantic-compression prompt, then calls OpenAI image generation (`gpt-image-2`) for a high-quality PNG 16:9 landscape technical visual brief. On normal PR pages it produces a PR cover card; on `/changes/<sha>` and `/commits/<sha>` it produces a commit review card, using PR context only to explain why that commit matters. The image prompt carries the source PR URL and current page URL for reference, asks for the single overall concept reviewers should understand first, chooses the best visual grammar (threshold curve, sequence diagram, ownership map, before/after data path, state machine, evidence plot, or scenario matrix), preserves high-level technical details, and prioritizes the most complicated, important, risky, or hard-to-explain parts so the output compresses the review target rather than listing details. It asks visuals to carry relationships that are hard to explain in prose, and text callouts to carry exact terms, invariants, constraints, outcomes, caveats, and test hooks that are hard to draw accurately. It also tells the model not to invent benchmark numbers or measured evidence. Results are cached per PR head or commit SHA/model/image settings/prompt version and can be reopened, downloaded, closed, or inspected by copying the generated image prompt. Image generation uses the high-context request timeout and surfaces timeout/network errors with the manual prompt fallback instead of leaving the card spinning indefinitely. The exact image prompt is always shown in a collapsible section when available, including the organization-verification fallback path so it can be pasted into `gpt-image-2` manually.

The **main PR description lightbulb** is treated specially: after generating the high-level overview, it also precomputes commit lightbulb caches (commits view + single-commit view) using richer PR context (including discussion/replies), so those views can open their lightbulb panels immediately from cache.

When GitHub fails to resolve an old review-comment permalink like `#discussion_r...` on a large PR conversation page, ACKtopus keeps the conversation view open, expands hidden/resolved/collapsed sections, suppresses the toolbar refresh loop during the reveal, and scrolls to the comment once GitHub renders it.

### ☑️ Queue

Keeps a personal list of PRs you want to come back to. You can add the current PR, search GitHub by PR number or text, open queued PRs in a new tab, reorder entries, remove entries, and see the queue count on the toolbar. The delayed Ctrl hotkey chooser exposes this as **Ctrl+L**.

### Settings

Lets you configure the optional GitHub PAT, Claude/OpenAI/Gemini API keys, active provider, maintainer logins, custom instructions for each recipe, full-patch context, LLM caching, cache clearing, and factory reset. ACKtopus uses Claude Sonnet 4.6 for normal Claude requests, Claude Opus 4.7 for high-context Claude recipes, ChatGPT `gpt-5.5`, and Gemini `gemini-3.5-flash`. Settings validation checks every model version ACKtopus can call for the provider, including high-context Claude Opus and the OpenAI image model; secondary model failures are shown as warnings when the primary model is usable. Provider key, usage, and billing links point to each provider's own console, including Google AI Studio for Gemini. High-context recipes use the larger request timeout for every configured provider. The toolbar background toggles compact mode. Selection popups use the same active provider/model as the rest of ACKtopus (no separate selection-helper settings).

## In-page review helpers

### Commit prefix on single-commit views

On single-commit pages like `/changes/<sha>` and `/commits/<sha>`, when you open a new inline comment box (new thread), ACKtopus pre-fills it with a commit link prefix. This makes it obvious which revision the comment refers to (especially helpful after rebases/force-pushes).

### Commit navigation and lightbulbs

On PR conversation, commits-list, single-commit, and changes views, ACKtopus adds floating commit navigation that shows commit messages and position and supports the delayed **Ctrl+J/K** shortcuts. For larger commit stacks, clicking the middle commit chooser opens a searchable commit list; typing filters immediately by SHA, position, or message, then asynchronously searches each commit patch so terms that appear only in the diff also surface matching commits. **Up/Down** changes the selected row, **Enter** opens it, and **Esc** or outside click closes it. Commit lightbulbs generate structured review aids with summary, context, why-it-matters, high-level pseudocode, verification notes, performance/simplification notes, concerns, message checks, and dependency notes.

### Explain / Chat / Fact check on selections

When you select text on a PR page (diff lines, commit messages, or comments), ACKtopus shows a small popup with a short (1-2 line) context summary and:

- **Explain**: quick explanation of the selected snippet in the context of the commit
- **Fact check**: checks whether the selected claim is accurate using the full PR context
- **Simplify**: proposes a simpler version (for code: fewer moving parts / less duplication; for text: simpler language)
- **Proofread**: useful when the selection is prose (docs/comments); it won’t try to rewrite code and shows an inline diff/result
- **Chat**: docked on the right of the popup output area; opens the Chat panel with the selection quoted and file/line/commit context included, plus any popup output already shown

For short replies like “sure, done”, **Fact check** also includes the surrounding reply thread so the claim can be interpreted in context.

If a cached PR-level lightbulb overview exists, ACKtopus feeds that into these quick selection helpers (especially the short summary / explain / simplify paths) to improve relevance without turning them into slow, heavy requests. The helper also includes the surrounding parent text block so the selected snippet is interpreted in context instead of isolation.

The popup keeps the action buttons on a single row, prefers to open below the selection when there is room, stays viewport-clamped, and can be dismissed by clicking anywhere outside of it.
The quick 1-2 line summary is fetched automatically after a short stable-selection delay when an LLM provider is configured. If the selection is cleared or immediately copied with `Cmd+C` / `Ctrl+C`, ACKtopus suppresses the tooltip and skips the LLM call.

### Start a review (from Conversation replies)

On the PR Conversation tab, reply boxes normally only show **Comment**. ACKtopus adds a **Start a review** button next to it (only on replies), so you can start a review without navigating to the Files/Changes views.

When a pending review already exists, ACKtopus marks reply and inline comment buttons with `⏳`, and adds a **Submit review** button to the main Conversation comment box.
If the main comment box is empty, it submits the pending comments only.
If it has text, that text is used as the review summary while submitting the pending comments.

### Quick actions on comments

ACKtopus adds small action buttons on comments to speed up common tasks:

- **Explain**: summarize/explain the comment or PR body in context
- **Expected author reply**: simulate the likely author response for your own pending/review comments
- **Proofread**: improve clarity/grammar without changing meaning, keep replies friendly and professional, preserve intentional spacing, and prefer simple punctuation over em dashes or double-hyphen punctuation (available while editing; it won’t auto-edit a closed comment). For PR descriptions, it also nudges the text toward concise Bitcoin Core contributor style, preferring compact prose or `**Problem:**` / `**Fix:**` / `**Notes:**` prefixes over markdown section headings when the original structure fits, and folding following prose onto the same prefix line even when blank lines separate it from the heading. It avoids folding when the following content starts as block content such as a table, image, list, code fence, or HTML block. The proofread prompt asks the model to preserve structural blank-line separators around protected Markdown/HTML blocks so collapsibles and fences do not accumulate empty lines. When clearly useful, it can also convert `Note`/`Tip`/`Important`/`Warning`/`Caution` lead-ins to GitHub alerts and upgrade generic collapsible summaries.
- During proofreading, ACKtopus rewrites GitHub commit-diff line-range URLs through `redirect.github.com` so `#diff-...Lx-Ly` fragments survive GitHub Markdown rendering, and briefly marks the proofread button with `🔗` when that happens.
- **Edit / Delete**: shortcuts to GitHub’s native actions (in delete confirmations, **Enter deletes** and **Escape cancels**). **Alt+Shift+E** edits the focused post, or the first visible post if focus is elsewhere; **Alt+Shift+P** proofreads or suggests for the focused editor, or the first visible editor.

Proofread and edit-review dialogs can switch between word, paragraph, and before/after views; word mode still supports click-to-revert changes, paragraph mode splits on newlines, and before/after keeps both full texts while coloring only the changed text. While the diff dialog is open, **Cmd/Ctrl+Enter** accepts it, **Esc** rejects it, and **Cmd/Ctrl+Up/Down** jumps between changed sections without submitting the underlying GitHub form. While editing a comment or PR description, **Cmd/Ctrl+Escape** clicks GitHub's native cancel button.

Inline review comments also get a quick link back to the Changes tab when ACKtopus can identify the review comment id, and pending comments get a readable “just now (pending)” timestamp. When editing an existing comment or PR description, ACKtopus marks the save/update button with `🧾` and shows the same switchable diff dialog against the previous version before submitting changes; **Accept and update** submits, while **Reject** returns to editing. Clicking **Update comment** without changing the text is treated as **Cancel** (no server update), so the content stays byte-for-byte unchanged. For comment editing, ACKtopus prefers the nearby native `edit_form` fragment when it is already available, and otherwise falls back to it when GitHub’s action menu is slow or incomplete.

### PR creation proofreading

On compare-based **new PR** pages, ACKtopus adds proofreading to the draft title and body editors. If the draft body is empty, the proofread flow can generate a short two-paragraph PR description from the draft title, commit messages, and compare patch.

### Wrap selection in collapsible details

Adds a helper button near the comment editor to wrap the current selection in a collapsible details block (handy for long logs or optional context).

### Sticky edit toolbar

Keeps the comment formatting toolbar accessible while editing longer comments.

### Faster reactions

Makes reacting faster by reducing clicks (for example: hover to open the picker and quick cycling on click).

### PGP signature badges

ACKtopus scans visible comment details blocks for cleartext PGP signatures, fetches keys from `keys.openpgp.org`, verifies signatures with `openpgp.js`, caches results, and marks valid, invalid, or failed checks inline.

### Focused compare/diff views

On compare-style views, ACKtopus can collapse files that are unrelated to the PR so the diff stays focused on what you’re reviewing.
After collapsing unrelated files, it also scrolls to the first remaining open file.
On repository pages, ACKtopus marks recent-push compare buttons with 🏠 and rewrites one-sided compare links so new PRs target the current repository’s base branch instead of GitHub’s upstream-parent default. If the page does not expose the base branch in the DOM, ACKtopus fetches and caches the repository default branch before rewriting the button.

## Development checks

- `pnpm run check` runs a Node syntax check over the userscript.
- `pnpm run build` runs TypeScript over the JavaScript source without emitting files.
- The in-browser self-test runner is available from ACKtopus settings on GitHub pages and covers DOM-dependent behavior against the live page.
- Console errors from `collector.github.com/github/collect` are GitHub Hydro analytics failures, not ACKtopus requests.
