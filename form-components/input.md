---
description: input field - search field - text area
---

# Input Elements

### Introduction

* An input field must have associated `<label>` element. To do this, add the `for` attribute to the`<label>` element. The value of the `for` attribute must be the same as the value for the `<input>` element's `id` attribute value. 
* When the input field fails to validate, an associated error message should be shown. To do this, add the `aria-describedby` attribute to the `<input>` element. The value of the `aria-describedby` attribute must be the same as the value for the `id` of the element that shows the error message \(typically a `<span>` element\). 

### Part One: Considering Markup

_**First and foremost:**_ These samples have been simplified to focus on accessibility. Simply copying and pasting these code samples will not produce a complete result. 

#### Input with a label

```markup
<label for="input-firstName">First Name</label>
<input type="text" id="input-firstName" name="firstName" />
```

#### Input with associated error message

This is what the simplified markup for an input with an associated error message could look like: 

```markup
<label for="input-firstName">Email</label> 
<input type="text" id="input-firstName" aria-describedby="email__error-message" 
aria-invalid="true" /> 
<span id="email__error-message" role="alert">
  Please enter a valid email address.
</span> 
```

### Part Two: Ember Component\(s\)

### References

* [https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label)
* [https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)

{% hint style="info" %}
Feedback is welcome! Visit the [GitHub repository for this project](https://github.com/MelSumner/ember-component-patterns) to raise an issue or submit a PR.
{% endhint %}

