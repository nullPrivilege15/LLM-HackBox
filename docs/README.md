
## Phase 2 (planned)

Extends this lab beyond direct prompt injection into two additional OWASP LLM Top 10 (2025) categories:

- **RAG + indirect prompt injection** — a small local document store where a poisoned document (not user input) becomes the injection vector, mapped to **LLM08:2025 — Vector and Embedding Weaknesses**.
- **MCP-style tool calling + excessive agency** — an intentionally over-privileged tool wired into a minimal function-calling loop, demonstrating how injected instructions can drive real actions, mapped to **LLM06:2025 — Excessive Agency**.

Scoping and implementation to begin after Phase 1 (prompt injection, improper output handling, and their patches) is fully documented.
