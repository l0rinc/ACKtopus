<h1>
  <svg width="28" height="28" viewBox="0 0 64 64" style="vertical-align:middle">
    <path d="M22 16Q27 5 32 7Q37 5 42 16" fill="#505870" stroke="#7080a0" stroke-width="1.2"/>
    <rect x="28" y="5" width="8" height="6" rx="2" fill="#607090" stroke="#8090b0" stroke-width=".6"/>
    <circle cx="32" cy="5" r="2.8" fill="#e30" opacity=".8"/><circle cx="32" cy="5" r="1.4" fill="#fa0"/>
    <ellipse cx="32" cy="27" rx="18" ry="15" fill="#454d65"/>
    <ellipse cx="32" cy="26" rx="16" ry="13" fill="#556080"/>
    <ellipse cx="32" cy="24" rx="13" ry="8" fill="#6070a0" opacity=".3"/>
    <circle cx="14" cy="23" r="5.5" fill="#454d65" stroke="#6070a0" stroke-width=".6"/>
    <circle cx="14" cy="23" r="3.2" fill="#607090"/><circle cx="14" cy="23" r="1.2" fill="#f40" opacity=".3"/>
    <circle cx="50" cy="23" r="5.5" fill="#454d65" stroke="#6070a0" stroke-width=".6"/>
    <circle cx="50" cy="23" r="3.2" fill="#607090"/><circle cx="50" cy="23" r="1.2" fill="#f40" opacity=".3"/>
    <rect x="17" y="21" rx="4" width="30" height="11" fill="#1a1a2a" stroke="#7080a0" stroke-width=".8"/>
    <circle cx="26" cy="26" r="4" fill="#300"/><circle cx="26" cy="26" r="3" fill="#c00"/>
    <circle cx="26" cy="26" r="1.6" fill="#f40"/><circle cx="26" cy="26" r=".8" fill="#fe0"/>
    <circle cx="38" cy="26" r="4" fill="#300"/><circle cx="38" cy="26" r="3" fill="#c00"/>
    <circle cx="38" cy="26" r="1.6" fill="#f40"/><circle cx="38" cy="26" r=".8" fill="#fe0"/>
    <circle cx="26" cy="26" r="6" fill="#f40" opacity=".1"/>
    <circle cx="38" cy="26" r="6" fill="#f40" opacity=".1"/>
    <line x1="22" y1="26" x2="-4" y2="15" stroke="#f40" stroke-width="2.2" stroke-linecap="round" opacity=".9"/>
    <line x1="22" y1="26" x2="-1" y2="9" stroke="#f60" stroke-width="1.2" stroke-linecap="round" opacity=".5"/>
    <line x1="42" y1="26" x2="68" y2="15" stroke="#f40" stroke-width="2.2" stroke-linecap="round" opacity=".9"/>
    <line x1="42" y1="26" x2="65" y2="9" stroke="#f60" stroke-width="1.2" stroke-linecap="round" opacity=".5"/>
    <circle cx="-4" cy="13" r="1.2" fill="#f60" opacity=".7"/><circle cx="68" cy="13" r="1.2" fill="#f60" opacity=".7"/>
    <ellipse cx="32" cy="34" rx="8" ry="5.5" fill="#7080a0"/>
    <circle cx="29" cy="33" r="1.3" fill="#454d65"/><circle cx="35" cy="33" r="1.3" fill="#454d65"/>
    <path d="M27 37Q32 41 37 37" fill="none" stroke="#2a2a3a" stroke-width="1.5" stroke-linecap="round"/>
    <path d="M16 36L10 40L8 38" fill="none" stroke="#6080a0" stroke-width="3.5" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M48 36L54 40L56 38" fill="none" stroke="#6080a0" stroke-width="3.5" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M20 38L16 46L18 48" fill="none" stroke="#5a7090" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M44 38L48 46L46 48" fill="none" stroke="#5a7090" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M27 40L24 48L26 50" fill="none" stroke="#507080" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/>
    <path d="M37 40L40 48L38 50" fill="none" stroke="#507080" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/>
    <circle cx="10" cy="40" r="1.2" fill="#7080a0"/><circle cx="54" cy="40" r="1.2" fill="#7080a0"/>
    <circle cx="16" cy="46" r="1" fill="#7080a0"/><circle cx="48" cy="46" r="1" fill="#7080a0"/>
    <circle cx="22" cy="19" r="1.2" fill="#8090b0"/><circle cx="42" cy="19" r="1.2" fill="#8090b0"/>
  </svg>
  ACKtopus
</h1>

ACKtopus is a GitHub userscript for [Tampermonkey](https://www.tampermonkey.net/) that adds a small floating toolbar and a handful of review helpers on pull requests and issues (optimized for Bitcoin Core-style review).

## Highlights

<img src="screenshots/floating%20acks.png" alt="Floating ACK toolbar and ACK panel">

_Floating toolbar with ACK/NACK parsing and jumpable review signals._

<img src="screenshots/tooltip%20on%20selection.png" alt="Selection helper tooltip">

_Selection helper with quick explain/fact-check/simplify/proofread actions._

<img src="screenshots/pr%20lightbulb.png" alt="PR lightbulb overview">

_PR lightbulb overview with high-level context and reviewer-oriented guidance._

<img src="screenshots/copy%20context.png" alt="Context copy actions">

_Clipboard-ready PR, commit, and comment context for sharing or LLM use._

<img src="screenshots/start%20review%20from%20reply.png" alt="Start review from reply">

_Pending-review helpers directly from Conversation replies and the main comment box._

<img src="screenshots/per%20PR%20clipboard%20commands.png" alt="Per-PR clipboard commands">

_Per-PR clipboard helpers for ACKs, checkout, range-diff, and review commands._

<img src="screenshots/commit%20lightbulb.png" alt="Single commit lightbulb">

_Single-commit lightbulb with summary, why-it-matters, pseudocode, and concerns._

<img src="screenshots/commits%20lightbulb.png" alt="Commits page lightbulb">

_Commits-page lightbulbs showing how each commit fits into the stacked PR._

<img src="screenshots/comment%20lightbulb.png" alt="Comment lightbulb">

_Comment explanation in context for understanding review remarks quickly._

<img src="screenshots/chat%20with%20navigation.png" alt="Chat panel with navigation">

_LLM chat panel with page context and navigation-aware review assistance._

<img src="screenshots/proofread.png" alt="Proofread flow">

_Proofread flow with diff-style review before applying text changes._

<img src="screenshots/commit%20review%20prefix.png" alt="Commit review prefix">

_Automatic commit prefix on single-commit views so inline comments stay revision-specific._

<img src="screenshots/compare%20closing%20unrelated.png" alt="Compare page focusing unrelated files">

_Compare-page cleanup that collapses unrelated files and keeps focus on the PR-relevant diff._

<img src="screenshots/expand%20closed%20sections.png" alt="Expand closed sections">

_Bulk expansion of hidden, minimized, outdated, or otherwise collapsed review content._

<img src="screenshots/navigate%20to%20comment.png" alt="Comment navigation">

_Chronological comment navigation for quickly walking long review discussions._

<img src="screenshots/queue.png" alt="Queue panel">

_Personal review queue for pull requests you want to revisit later._

<img src="screenshots/settings.png" alt="Settings panel">

_Settings for tokens, providers, maintainer list, caches, and compact toolbar behavior._

## What it helps with

- Copying ACK-style messages for the current PR head commit
- Copying PR, commit, or comment context to your clipboard
- Navigating long PR discussions quickly
- Expanding/collapsing hidden or resolved sections in bulk
- Leaving comments on single-commit views with a clear “this comment is about *this* commit” prefix
- Quick actions on comments and selections (explain, proofread, edit, delete, fact-check, simplify)

## Toolbar (top-right)

### 👥 ACK panel

Shows detected ACKs/Concept ACKs/NACKs (and similar signals) and lets you jump to the comment that contained them.

### SHA / ACK copy

Copies useful snippets based on the PR head commit, such as:

- `ACK <sha>` / `Concept ACK <sha>`
- Checkout helpers (`git fetch …`, `gh pr co …`)
- Range-diff / rebase-diff helpers (useful after force-pushes)
- Convenience commands for benchmarks/tests/fuzz/functional tests when relevant files are involved

These buttons always **copy to your clipboard** (they never insert text into a comment box).

Tip: hold **Ctrl** for ~0.5s to show the hotkey chooser. Press the letter to copy that format, or press **Enter** to copy the currently selected format (the one shown on the main SHA button).

If the PR changes C/C++ files, additional per-PR helpers appear:

- `clang-format-diff`: apply formatting only to changed lines
- `clang-tidy-diff`: run clang-tidy only on changed lines
- `IWYU (changed)`: run include-what-you-use only on changed `src/*.h` / `src/*.cpp` files

These three commands are generated with the PR’s exact changed C/C++ file paths already filled in, so they are ready to run as-is.

### 📦 Show hidden

Expands content that GitHub often hides behind extra clicks, such as:

- “Load more…” comment pagination
- Minimized/outdated blocks
- “Load diff” buttons for large diffs

### 📂 Show resolved

Expands resolved review threads so you can scan discussions without opening them one-by-one.

### 💬 Comment navigation

Jumps between comments in chronological order so you can quickly review conversations.

### 📎 Context copy

Copies the PR’s context (title/description, commits, diff, and visible comments) to your clipboard for sharing or pasting into an LLM.
On single-commit pages like `/changes/<sha>` and `/commits/<sha>`, the same button copies **commit-only** context instead: the parent PR metadata/description, the current commit patch, and visible comments tied to that commit.
Each comment’s `...` menu also gets a **Copy comment context** action, which copies just that comment plus its surrounding thread and location metadata (file, line, commit, author, permalink).

### 🤖 Chat

Opens an assistant panel that can:

- Summarize a PR or a single commit
- Explain a single commit with high-level pseudocode and performance/simplification notes
- Explain a specific comment in context
- Proofread text before you post it

For explain/proofread/fact-check flows, ACKtopus includes PR-level context (description, commit messages, diff) with larger context windows to improve response quality.

The **main PR description lightbulb** is treated specially: after generating the high-level overview, it also precomputes commit lightbulb caches (commits view + single-commit view) using richer PR context (including discussion/replies), so those views can open their lightbulb panels immediately from cache.

### ☑️ Queue

Keeps a simple personal list of PRs you want to come back to.

### Settings

Lets you configure optional tokens/keys and tweak behavior (for example, compact toolbar mode). Selection popups use the same active provider/model as the rest of ACKtopus (no separate selection-helper settings).

## In-page review helpers

### Commit prefix on single-commit views

On single-commit pages like `/changes/<sha>` and `/commits/<sha>`, when you open a new inline comment box (new thread), ACKtopus pre-fills it with a commit link prefix. This makes it obvious which revision the comment refers to (especially helpful after rebases/force-pushes).

### Explain / Chat / Fact check on selections

When you select text on a PR page (diff lines, commit messages, or comments), ACKtopus shows a small popup with a short (1-2 line) context summary and:

- **Explain**: quick explanation of the selected snippet in the context of the commit
- **Fact check**: checks whether the selected claim is accurate using the full PR context
- **Simplify**: proposes a simpler version (for code: fewer moving parts / less duplication; for text: simpler language)
- **Proofread**: useful when the selection is prose (docs/comments); it won’t try to rewrite code, uses the same diff accept/reject flow as regular proofreading, and may apply small structural markdown upgrades when clearly appropriate (alerts, better `<summary>` labels, obvious fence languages)
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

- **Explain**: summarize/explain the comment in context
- **Proofread**: improve clarity/grammar without changing meaning while preserving intentional paragraph spacing/blank lines (available while editing; it won’t auto-edit a closed comment). When clearly useful, it can also convert `Note`/`Tip`/`Important`/`Warning`/`Caution` lead-ins (with or without `:`) to GitHub alerts, upgrade generic collapsible summaries, and preserve/update code-fence languages suggested by the proofread result.
- **Edit / Delete**: shortcuts to GitHub’s native actions (in delete confirmations, **Enter deletes** and **Escape cancels**)

When editing an existing comment, clicking **Update comment** without changing the text is treated as **Cancel** (no server update), so the comment content stays byte-for-byte unchanged. For comment editing, ACKtopus prefers the nearby native `edit_form` fragment when it is already available, and otherwise falls back to it when GitHub’s action menu is slow or incomplete.

### PR creation proofreading

On compare-based **new PR** pages, ACKtopus also adds proofreading to the draft title and body editors, so you can clean up the PR before it is created.

### Wrap selection in collapsible details

Adds a helper button near the comment editor to wrap the current selection in a collapsible details block (handy for long logs or optional context).

### Sticky edit toolbar

Keeps the comment formatting toolbar accessible while editing longer comments.

### Faster reactions

Makes reacting faster by reducing clicks (for example: hover to open the picker and quick cycling on click).

### Focused compare/diff views

On compare-style views, ACKtopus can collapse files that are unrelated to the PR so the diff stays focused on what you’re reviewing.
After collapsing unrelated files, it also scrolls to the first remaining open file.
