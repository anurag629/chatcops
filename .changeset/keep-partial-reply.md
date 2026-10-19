---
"@chatcops/widget": patch
---

When a reply fails after some of it has streamed, the widget keeps that text and shows the error as a short note under it, with Retry as before. Before, the error message replaced the whole bubble. A failure that throws partway through also no longer adds a second copy of the bubble.
