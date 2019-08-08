# Buttons

Ahh, the simple button. Possibly the simplest component of them all, yet still somehow one that has been the subject of continual confusion in web and application development.

### Introduction

The rule of thumb is this: if it takes the user from one URL to another, use a link. If otherwise, use a button element. 

Of course, there are benefits of using the `<button>` element - semantic HTML code is machine readable, and there are pre-existing browser defaults for interaction, such as using the `ENTER` or `SPACE` key to activate the button's `click` and `keydown` events.  

### Part One: Considering Markup

#### Standard buttons

This is the most common markup associated with the `<button>` element: 

```markup
<button>text</button>
```

#### Icon buttons

Special care should be given when deciding to include a button with only an icon in it. In order to be machine-readable, information should be added depending on your icon approach. 

Whether the icon is an image file, an emoji, or an SVG file, the `aria-label` attribute should be added to the `<button>` element. It should also be explicitly ensured that the image is not available to other machines, which can be achieved by adding the `aria-hidden` attribute to the . 

Example:  

```markup
<button aria-label="Delete this item forever">
  <span aria-hidden="true">🗑</span>
</button>
```

This markup will return the following accessibility tree: 

![Chrome DevTools Accessibility Tree](../../.gitbook/assets/image%20%281%29.png)



#### Toggle buttons

Toggle buttons can be a little tricky because they have multiple small details that must be included in order to be appropriately effective. 

TODO toggle button details

#### Buttons in forms

While using `<input type="submit">` is still technically a valid, it is also an outdated approach, and it is recommended to avoid use. Additionally, `<button>` elements are considerably easier to style than `<input>` elements. 

TODO submit/reset

TODO form considerations

### Part Two: The Ember Component  

TODO component sample

TODO using the component sample



