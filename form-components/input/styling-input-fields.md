# Styling: Text Fields

## Visually Hidden Labels

This is the most common need for `<label>` elements- how to make it available to other machines \(such as screen readers\) but visually hidden for design purposes. While it should be noted that a label helps to provide clarity for all users, there are some ways to make this happen.

The most common approach was popularized by markup frameworks like [Bootstrap](https://getbootstrap.com/), and uses .sr-only \(screen-reader only\) and .sr-only-focusable \(screen-reader only, focusable elements\).

`.sr-only`  
Content which should be visually hidden, but remain accessible to assistive technologies such as screen readers, can be styled using classes such as the popular `.sr-only` class. This can be useful in situations where additional visual information or cues \(such as meaning denoted through the use of color\) need to also be conveyed to non-visual users.

CSS:

```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
```

`.sr-only-focusable`  
For visually hidden interactive controls, such as traditional “skip” links, `.sr-only` can be combined with the `.sr-only-focusable` class. This will ensure that the control becomes visible once focused.

SCSS:

```css
.sr-only-focusable {
  &:active,
  &:focus {
    position: static;
    width: auto;
    height: auto;
    overflow: visible;
    clip: auto;
    white-space: normal;
  }
}
```

