---
description: Want to hide content in `iframe` elements from screen readers? Here's a guide.
---

# iFrames and Screen Readers

### 

| Screen reader | `iframe` + `hidden` | `iframe` + `display:none` | `iframe`  `aria-hidden=true` + `tabindex=-1`+ `role=none` |
| :--- | :--- | :--- | :--- |
| JAWS | not announced | not announced | not announced |
| NVDA | not announced | not announced | not announced |
| Narrator | not announced | not announced | `iframe` content announced and operable |
| VoiceOver Mac | not announced | not announced | `iframe` is in navigation order and announced as “application”, content of `iframe` is hidden. |
| VoiceOver iOS | not announced | not announced | not announced |
| Talkback Android | not announced | not announced | In Chrome if navigating by heading the heading in the iframe is announced. Not in Firefox. |



