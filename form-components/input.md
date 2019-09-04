---
description: input field
---

# Input Element

### Introduction

* An input field must have associated `<label>` element. To do this, add the `for` attribute to the`<label>` element. The value of the `for` attribute must be the same as the value for the `<input>` element's `id` attribute value. 
* When the input field fails to validate, an associated error message should be shown. To do this, add the `aria-describedby` attribute to the `<input>` element. The value of the `aria-describedby` attribute must be the same as the value for the `id` of the element that shows the error message \(typically a `<span>` element\). 

### Part One: Considering Markup

_**First and foremost:**_ These samples have been simplified to focus on accessibility. Simply copying and pasting these code samples will not produce a complete result. 

#### Input Types

The `type` attribute value is the most important attribute for the `<input>` element. While it is `text` by default, there are other valid values:

* email
* password
* search
* tel \(telephone\)
* url

Other valid type values are `checkbox` and `radiobutton` , but covered in separate topics in this guide. \(See: [Radio Buttons](radio-buttons/)\) 

#### Text Input with a label

```markup
<label for="input-firstName">First Name</label>
<input type="text" id="input-firstName" name="firstName" />
```

#### Input Attributes

Some attributes are required to make the `<input>` element work properly. The `name` and `value` attributes both contain data that is submitted to the server when the form submits. It can also be useful in some cases to pre-fill the `value` attribute. 

There are also useful attributes available for use with the `<input>` element that developers should be aware of, as this prevents unnecessary JavaScript. 

`required`   
The presence of the `required` attribute will indicate that the input must be filled out by the user. It should be noted that only the attribute is required. Removing the attribute will indicate that it is not required. Example: 

```markup
<label for="firstName-input">First Name</label>
<input type="text" id="firstName-input" name="firstName" required />
```

`disabled`   
The presence of the `disabled` attribute will prevent the user from interacting with this element, and the `value` of this field will not be submitted to the server with the rest of the form data. This is useful in cases where it has been determined that the specific end user does not meet the criteria to fill out this specific form field. Disabled elements are also not required to pass [color contrast standards](https://www.w3.org/WAI/WCAG21/quickref/?showtechniques=143#contrast-minimum) as related to WCAG success criteria. Finally, it should be noted that only the presence of the attribute is required. 

```markup
<label for="firstName-input">First Name</label>
<input type="text" id="firstName-input" name="firstName" disabled />
```

`readonly`   
The presence of the `readonly` attribute will allow the user to see the current value, but will not allow the user to change the value in the input field. This is different from disabled in that the value for the readonly field will be sent to the server when the form is submitted. Again, it should be noted that only the presence of the attribute is required. Example: 

```markup
<label for="firstName-input">First Name</label>
<input type="text" id="firstName-input" name="firstName" value="Zoey" readonly />
```

`autocomplete`   
Input fields are set to `autocomplete="true"` by default. This will allow some browsers \(that provide the option\) to automatically fill in information saved by the user to the browser itself. In instances where this is not desired behavior, setting `autocomplete="false"` will turn this option off. 

Note: It is an elevated experience for users with assistive technology to include this attribute in form fields, especially where the type of questions being asked in a form are atypical of the type of autocomplete data \(such as name and address\) that a user's browser may have stored. Example: 

```markup
<label for="camping-preference">Where is your favorite place to camp?</label>
<input id="camping-preference" type="text" name="campingPreference" autocomplete="false" />
```



`pattern` setting the pattern attribute value will provide client-side form validation for the user. The `pattern` attribute expects a Regular Expression as its value. 

Example:

```markup
<label for="weather-preference">Do you prefer sunny weather or cloudy weather?</label>
<input type="text" pattern="[Ss]unny|[Cc]loudy" id="weather-preference" />
```

Using the `:invalid` and `:valid` pseudo selectors in CSS can indicate that the element is invalid: 

![A dashed red border indicates that the value in the input field is not valid.](../.gitbook/assets/image%20%283%29.png)

It should be noted that the `email` and `url` input types do not require a `pattern` attribute because they already provide their own form of pattern validation. Additionally, `pattern` is ignored in browsers that support the `number` type. 

`min-length` and `max-length` are used when it is useful to control the number of characters put into the field. Some traditional databases have a maximum character length that they can accept, so it is prudent to be aware of the limitations of where the form data is heading. 

It is also appropriate to be aware that non-traditional data may exist, and plan for those use cases. For more reading on this subject, search for "_names that break websites_", or read [People's Names that Break Websites](https://css-tricks.com/peoples-names-break-websites/). 

`placeholder` 

#### Input with associated error message

If additional guidance is desired, an error message that is associated with the input field can be added.   
This is what the simplified markup for an input with an associated error message could look like: 

```markup
<label for="input-email">Email</label> 
<input type="email" id="input-firstName" aria-describedby="email__error-message" 
aria-invalid="true" /> 
<span id="email__error-message" role="alert">
  Please enter a valid email address.
</span> 
```

Note the `aria-describedby` attribute on the `input` field, whose value matches the `id` of the element that contains the error message.

### Part Two: Ember Component\(s\)

### References

* [https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label)
* [https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)

{% hint style="info" %}
Feedback is welcome! Visit the [GitHub repository for this project](https://github.com/MelSumner/ember-component-patterns) to raise an issue or submit a PR.
{% endhint %}

