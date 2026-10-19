---
"@chatcops/core": minor
---

Upgrade the provider SDKs and the default models.

- Claude: `@anthropic-ai/sdk` 0.135. The default model is now `claude-haiku-5-5`. Thinking blocks are sent back unchanged between tool rounds, and a refusal or a context window overflow is reported as an error instead of an empty reply.
- OpenAI: `openai` 7. The default model is now `gpt-5-mini`. Requests send `max_completion_tokens` (set `maxTokensParam: 'max_tokens'` for servers that need the old name), and tool calls run in parallel like the other providers.
- Gemini: moves from the deprecated `@google/generative-ai` to `@google/genai`. The default model is now `gemini-3.5-flash-lite`, because Google shut down the old default `gemini-2.0-flash`. Function results carry the call id, and thought signatures are kept between tool rounds.
- New provider options: `effort` (default `'low'`), `baseURL` for proxies and OpenAI-compatible servers such as Ollama or OpenRouter, `organization` for OpenAI, and `maxTokensParam`.
- `temperature` is left out, with a one-time warning, on models that reject it (Claude 5.x, Claude Opus 4.7 and later, OpenAI reasoning models).
- The default `maxTokens` goes from 1024 to 4096, because thinking tokens count toward it.
- History sent to a provider now always starts with a user message, and consecutive messages from the same side are merged. This fixes Gemini errors after about 50 exchanges and after a failed reply. `normalizeHistory` is exported.

Migration: if you relied on the old default models, set `model` explicitly. `@google/generative-ai` is no longer installed with `@chatcops/core`; add it to your own dependencies if your code imports it directly.
