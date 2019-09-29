---
description: >-
  Anti-patterns produce outcomes that are ineffective because they are not
  complete solutions, and as such are counterproductive. Developers are advised
  to be aware of anti-patterns and avoid their use.
---

# Anti-patterns: Radio Buttons

When considering how to craft a useful radio button group component, it is also necessary to consider what _not_ to do. If any Ember addon is evaluated for use, it is not only the Ember code itself that needs to be evaluated, but the output to the browser itself that should be evaluated. 

### Anti-pattern \#1: divs and spans

Consider this markup:

```markup
<div class="radio-button-group">
  <div class="radio-row">
    <div class="ember-view radio-button">
      <input class="ember-view radio-input" type="radio">
      <span class="form-label radio-label">True</span>
    </div>
  </div>
  <div class="radio-row">
    <div class="radio-button">
      <input class="radio-input" type="radio">
      <span class="form-label radio-label">False</span>        
    </div>
  </div>
</div>
```

This should be considered unacceptable for the following reasons: 

1. there is no `<label>` element associated with the `<input>` element
2. the radio buttons are not associated as a group with the use of the `name` attribute.

### Anti-pattern \#2 - label first

Consider this markup: 

```markup
<label for="radio_true">True</label>
<input id="radio_true" name="question_001" value="true" />
```

This would put the label first, and the radio button second. This should be considered an anti-pattern because it is not placing the radio button where the user has been trained to expect it, i.e., to the left of the  label. 



{% hint style="info" %}
Have an anti-pattern to submit? Open an issue \(and include the sample code\) on this project's [GitHub repository](https://github.com/MelSumner/ember-component-patterns).
{% endhint %}

