---
description: >-
  Anti-patterns produce outcomes that are ineffective because they are not
  complete solutions, and as such are counterproductive. Developers are advised
  to be aware of anti-patterns and avoid their use.
---

# Anti-patterns: Buttons

### Anti-pattern \#1: The div as a button

Really, this should be called "the `<div>` or `<span>` as a button."

Code example: 

```markup
<div class="button">button text</div>
```

This should be considered unacceptable for the following reasons: 

* there is no machine-readable way to determine that it is a button
* a [div is not an interactive element w/o an associated role](https://www.w3.org/WAI/WCAG21/Techniques/failures/F59)
* non-interactive elements should not have interactions associated with them
* there is no way to keyboard navigate to this element
* there is no way to interact with this element using a keyboard

This pattern also causes the [Failure of Success Criterion 4.1.2 due to using script to make div or span a user interface control in HTML without providing a role for the control](https://www.w3.org/WAI/WCAG21/Techniques/failures/F59).

### Anti-pattern \#2: The "Almost" button

Code example: 

```markup
<div class="button" role="button">button text</div>
```

This sample is marked with the role of button, which provides a machine-readable way for it to be identified as a button. However, it should still be considered unacceptable for the following reasons: 

* a div is not an interactive element 
* non-interactive elements should not have interactions associated with them
* there is no way to keyboard navigate to this element
* there is no way to interact with this element using a keyboard

{% hint style="info" %}
Have an anti-pattern to submit? Open an issue \(please include sample code!\) on this project's [GitHub repository](https://github.com/MelSumner/ember-component-patterns).
{% endhint %}



