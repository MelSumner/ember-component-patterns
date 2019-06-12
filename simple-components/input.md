# Input

### Requirements

* Input fields must have associated label elements. To do this, add the `for` attribute to the `label` element. Assign the `id` of the `input` element as the value. 
* Input fields should ensure that  they have properly associated error message. To do this, add the `aria-describedby` attribute to the `input` element. Assign the `id` of the `span` of the error message as the value. 

### Sample Markup

When rendered to the browser, this is what the simplified markup for an input with an associated error message would look like \(_note: this markdown sample is reduced to focus on accessibility- simply copying and pasting this code will not produce a complete result_\): 

```markup
<label for="email">Email</label> 
<input type="text" id="email" aria-describedby="email__error-message" aria-invalid="true"> 
<span id="email__error-message" role="alert">
  Please enter a valid email address.
</span> 
```

### References



