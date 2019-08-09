# Buttons

Ahh, the simple button. Possibly the simplest component of them all, yet still somehow one that has been the subject of continual confusion in web and application development.

### Introduction

There are many benefits of using the `<button>` element - semantic HTML code is machine readable, and there are pre-existing browser defaults for interaction, such as using the `ENTER` or `SPACE` key to activate the button's `click` and `keydown` events.  

{% hint style="info" %}
Link or Button? The rule of thumb is this: if it takes the user to a URL, use a link. If not, use a button! 
{% endhint %}

### Part One: Considering Markup

#### Standard buttons

This is the most common markup associated with the `<button>` element: 

```markup
<button id="some-id">text</button>
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

{% hint style="info" %}
For an improved user experience, consider adding text along with the icon. _**All**_ users will benefit from the added clarity, especially since the meaning of icons can differ from country to country! 
{% endhint %}

#### Toggle buttons

Toggle buttons can be a little tricky because they have multiple small details that must be included in order to be appropriately effective. 

While a toggle button can visually present in many different ways, the use of pseudo elements can still allow semantic markup to achieve the desired outcomes. 

```markup
<button aria-pressed="true" class="button-toggle">
  Option Text
  <span aria-hidden="true" class="button-toggle-on"></span>
  <span aria-hidden="true" class="button-toggle-off"></span>
</button>
```

Which can, with appropriate styling, produce a toggle that would appear like this: 

![toggle button when aria-pressed is true](../../.gitbook/assets/image%20%282%29.png)

To see how the styling would work in this case, a [CodePen](https://codepen.io/melsumner/pen/wVErBw) has been created as a demonstration. 

#### Buttons in forms

While using `<input type="submit">` is still technically a valid, it is also an outdated approach, and it is recommended to avoid use. Additionally, `<button>` elements are considerably easier to style than `<input>` elements. 

TODO submit/reset

TODO form considerations

### Part Two: The Ember Component  

TODO component sample

TODO using the component sample

### References

* [Inclusive Components: Toggle Buttons](https://inclusive-components.design/toggle-button/)
* [Switch Component: Toggle Button](https://scottaohara.github.io/a11y_styled_form_controls/src/toggle-button-switch/)
* [&lt;button&gt;: The Button Element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button)
* [When to Use The Button Element](https://css-tricks.com/use-button-element/)
* 




