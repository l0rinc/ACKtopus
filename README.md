# ACKtopus

ACKtopus is a GitHub userscript that adds a small floating toolbar and a handful of review helpers on pull requests and issues (optimized for Bitcoin Core-style review).

## What it helps with

- Copying ACK-style messages for the current PR head commit
- Navigating long PR discussions quickly
- Expanding/collapsing hidden or resolved sections in bulk
- Leaving comments on single-commit views with a clear “this comment is about *this* commit” prefix
- Quick actions on comments (explain, proofread, edit, delete)

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

If a cached PR-level lightbulb overview exists, ACKtopus feeds that into these quick selection helpers (especially the short summary / explain / simplify paths) to improve relevance without turning them into slow, heavy requests.

The popup is intentionally small and terse, keeps the action buttons on a single row, reserves three wrapped lines for the quick summary without scrollbars, prefers to open below the selection when there is room, stays viewport-clamped, and can be dismissed by clicking anywhere outside of it.
The quick 1-2 line summary is fetched automatically on mouseup with a short debounce when an LLM provider is configured, and is designed to be fast/cheap and cache-friendly.

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

### Wrap selection in collapsible details

Adds a helper button near the comment editor to wrap the current selection in a collapsible details block (handy for long logs or optional context).

### Sticky edit toolbar

Keeps the comment formatting toolbar accessible while editing longer comments.

### Faster reactions

Makes reacting faster by reducing clicks (for example: hover to open the picker and quick cycling on click).

### Focused compare/diff views

On compare-style views, ACKtopus can collapse files that are unrelated to the PR so the diff stays focused on what you’re reviewing.
After collapsing unrelated files, it also scrolls to the first remaining open file.
