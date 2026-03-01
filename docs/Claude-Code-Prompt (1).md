# Claude Code — Clade Launch Prompt

Copy and paste this entire prompt into Claude Code:

---

I have a project called Clade in my home directory at ~/clade (or wherever you extracted the tarball). It's a local-first memory sync tool — two AI agent memory stores get reconciled by a local LLM through conversation.

Here's what I need you to do, in order:

## 1. Find and set up the project

Look at the clade/ directory. Familiarize yourself with the structure: clade.py, README.md, examples/, adapters/, BLOG.md, TWITTER_THREAD.md, CONTRIBUTING.md, LICENSE, requirements.txt.

## 2. Replace placeholder GitHub username

Replace every occurrence of `yourusername` in README.md, BLOG.md, and TWITTER_THREAD.md with my actual GitHub username: [PUT YOUR USERNAME HERE]

## 3. Initialize git and create the GitHub repo

```
cd clade
git init
git add .
git commit -m "Initial commit — memory sync through conversation"
gh repo create clade --public --description "Sync AI agent memories through conversation. No protocol needed. Local LLM as the universal translator." --source . --push
```

If `gh` isn't installed, install it first (`brew install gh`).

## 4. Test the actual sync

Make sure Ollama is running (`ollama serve` if not). Then run:

```
pip install -r requirements.txt
python clade.py --store-a examples/scope_agent.json --store-b examples/openclaw_agent.json --dry-run --review
```

Look at the output. Check:
- Did it return valid JSON?
- Did it correctly identify the Berlin/Frankfurt conflict?
- Did it merge the duplicate memories about dark mode and the project name?
- Did it propagate unique memories correctly?

## 5. Fix whatever breaks

The LLM will probably get something wrong. Common issues:
- JSON parsing errors (markdown fences in the response)
- Misclassifying conflicts as duplicates
- Missing memories in the analysis
- Hallucinating content not in either store

Fix the prompt in `build_sync_prompt()` or the parsing in `parse_sync_response()` as needed. Run again until the example sync produces clean, correct output.

## 6. Commit the fixes

```
git add -A
git commit -m "Fix sync prompt and parsing from real-world testing"
git push
```

## 7. Tag v0.1.0

```
git tag -a v0.1.0 -m "First release — JSON sync with conflict detection"
git push --tags
```

## 8. Verify

- Check that the repo is live at github.com/[username]/clade
- Make sure the README renders correctly on GitHub
- Confirm the example files are in the repo

That's it. Don't add anything. Don't refactor. Don't improve the code beyond what's needed to make the example sync work. Ship it.

---
