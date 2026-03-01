# Claude Code — Rename Clade to Clade

The repo at ~/clade needs to be renamed to Clade. Here's what to do:

## 1. Rename everything in the codebase

Search every file in the project and replace:
- "Clade" → "Clade"
- "clade" → "clade"
- "CLADE" → "CLADE"

This includes: README.md, BLOG.md, TWITTER_THREAD.md, CONTRIBUTING.md, clade.py → clade.py, and any references in examples/ or adapters/.

Make sure the main script is renamed from `clade.py` to `clade.py` and all internal references (argparse descriptions, logging, config file references like `clade.yaml` → `clade.yaml`) are updated.

## 2. Update the project description and tagline

The old tagline was about negotiation/discussion. The new one leans into biology:

**Repo description:** "Sync AI agent memories through conversation. A clade is a group sharing a common ancestor — your agents share you."

**README subtitle/tagline:** Update to reflect the clade metaphor. The core concept hasn't changed — natural language as integration layer, local LLM as universal translator — but the framing is now biological: agents that share a common ancestor (the user) reconciling their inherited knowledge.

## 3. Rename the GitHub repo

```
gh repo rename clade
```

This updates the remote URL automatically.

## 4. Commit and push

```
git add -A
git commit -m "Rename to Clade — a group sharing a common ancestor"
git push
```

## 5. Re-tag

```
git tag -d v0.1.0
git push --delete origin v0.1.0
git tag -a v0.1.0 -m "First release — memory sync through conversation"
git push --tags
```

## 6. Verify

- Repo is live at the new URL
- README renders correctly
- `python clade.py --help` works
- All references to "clade" are gone (grep -ri "clade" to confirm)

Don't add anything new. Don't refactor. Just rename and push.
