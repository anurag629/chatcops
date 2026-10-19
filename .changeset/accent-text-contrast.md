---
"@chatcops/widget": patch
---

Text on the accent color now always reaches WCAG AA contrast (4.5:1). With the default accent, white text in the visitor's own messages was at 4.47:1. The widget now picks the text color from `theme.accent`: white when it passes, near-black on light accents (which keep their exact color), or white on a slightly darker shade of the accent. Icons on the launcher and send button use the same text color. New CSS variables: `--cc-on-accent` and `--cc-accent-contrast`.
