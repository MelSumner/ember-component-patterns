# Styling: Checkboxes

## Preventing Text Selection

Occasionally, when a checkbox is activated or deactivated, the input's label text appears selected. If this is bothersome, a little CSS can help:

```css
label {
    user-select: none;
}
```

