# Contributing to Clade

## The Philosophy

Clade has no adapter layer. The LLM reads any format directly. This means contributions look different from most open source projects.

## What We Need

### 1. Real-World Testing (Most Valuable)

Point Clade at your actual agent memory files. The ones your tools produce in production. Run a sync. Tell us:

- What format were your files?
- Did the LLM correctly identify the format?
- Did it extract all memories accurately?
- Were conflicts detected correctly?
- What broke?

Open an issue with your findings. Anonymize any personal data.

### 2. Format Samples

If your agent stores memories in a format we haven't tested, share an anonymized sample. We'll add it to the test suite.

Formats we've tested: JSON, Markdown, YAML, plaintext

Formats we want to test: SQLite dumps, CSV, TOML, XML, Letta blocks, LangChain stores, MemGPT archives, CrewAI logs

### 3. Edge Cases

- Stores with 500+ memories
- Memories in multiple languages
- Conflicting timestamps across time zones
- Mixed formats within a single file
- Emoji and special characters in memories
- Very long individual memories (1000+ words)

### 4. Model Testing

Clade works with any Ollama model. We've tested:
- llama3.1:70b (best quality, slow)
- qwen2.5:72b (good quality, slow)
- llama3.1:8b (good enough for small stores, fast)

Test with your preferred model and report accuracy.

### 5. Integration Guides

Want to embed Clade in your app or framework? The engine is ~150 lines and MIT licensed. Write a guide and we'll link it.

## Pull Requests

- Keep it simple. Clade is ~150 lines for a reason.
- Don't add adapters. The LLM is the adapter.
- One feature per PR.

## License

By contributing, you agree your code is MIT licensed.
