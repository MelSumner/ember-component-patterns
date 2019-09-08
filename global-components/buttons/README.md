# Buttons

Ahh, the simple button. Possibly the simplest component of them all, yet still somehow one that has been the subject of continual confusion in web and application development.

### Introduction

There are benefits to using the `<button>` element - semantic HTML is machine-readable code, and there are pre-existing browser defaults for interaction, such as using the `ENTER` or `SPACE` key to activate the button's `click` and `keydown` events.  

### Part One: Considering Markup

{% hint style="info" %}
Link or Button? The rule of thumb is this: if it takes the user to a URL, use a link. Otherwise, use a button!  
{% endhint %}

#### Standard buttons

This is the most common markup associated with the `<button>` element: 

```markup
<button id="some-id">text</button>
```

#### Icon buttons

Special care should be given when deciding to include a button with only an icon in it. In order to be machine-readable, information should be added depending on your icon approach. 

Whether the icon is an image file, an emoji\(not advised\), or an SVG file, the `aria-label` attribute should be added to the `<button>` element. It should also be explicitly ensured that the image is not available to other machines, which can be achieved by adding the `aria-hidden` attribute. 

Example:  

```markup
<button aria-label="Delete this item forever">
  <span aria-hidden="true">🗑</span>
</button>
```

This markup will return the following accessibility tree: 

![Chrome DevTools Accessibility Tree](../../.gitbook/assets/image%20%283%29.png)

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

![toggle button when aria-pressed is true](../../.gitbook/assets/image%20%281%29.png)

To see how the styling would work in this case, a [CodePen](https://codepen.io/melsumner/pen/wVErBw) has been created as a demonstration. 

Assistive technology interprets the existence of the `aria-pressed` attribute as a signal that this is a toggle button. Typically, a screen reader should read out "\(Option Text\) toggle button" when `aria-pressed` is false. When `aria-pressed` is set to true, "\(Option Text\) toggle button pressed" will be heard instead. 

#### Buttons in forms

While using `<input type="submit">` is still technically valid HTML, it is also an _outdated_ approach, and it is recommended to avoid use. Additionally, `<button>` elements are considerably easier to style than `<input>` elements. 

When inside of the `<form>` element, setting the button `type` attribute can indicate intent. If there is only one button in the `<form>` element, the button will be treated as though `type="submit"` were declared. However, explicit declaration of type is typically preferred when components are abstracted for use in many places. 

Submit button: 

```markup
<button type="submit">Submit this form</button>
```

If providing a form reset method is desired, the markup would look like this: 

```markup
<button type="reset">Clear form</button>
```

### Part Two: Creating the Ember Component  

#### The Generic Button Component

Generate the generic button component: 

```bash
ember generate component button-generic -gc
```

The appropriate markup can then be added to the `button-generic.hbs` file. Note that because button classes will so often need extra classes for styling,  `...attributes` should be added to allow a bit more flexibility when using the component, as it is practical.

```markup
<button 
  {{on "click" this.handleInteraction}}
  class="button"
  ...attributes
>
{{@accessibleName}}
</button>
```

Since a button should do something when it is interacted with, an action will be added to the `button-generic.js` file. For the purpose of this document, the action will only put a message in the console log:

```javascript
import Component from '@glimmer/component';
import action from '@ember/object';

export default class ButtonGenericComponent extends Component { 
  @action handleInteraction() { 
    console.log('computer says hello'); 
  } 
} 
```

The component can then be added to the page template:

```markup
<ButtonGeneric 
 @accessibleName="Say Hello"
/>
```



### References

* [Inclusive Components: Toggle Buttons](https://inclusive-components.design/toggle-button/)
* [Switch Component: Toggle Button](https://scottaohara.github.io/a11y_styled_form_controls/src/toggle-button-switch/)
* [&lt;button&gt;: The Button Element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button)
* [When to Use The Button Element](https://css-tricks.com/use-button-element/)







