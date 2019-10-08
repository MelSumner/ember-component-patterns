# Tooltips

### Introduction

A tooltip is a useful way to provide the user with a hint. It is typically activated on hover, but should also be able to be activated via keyboard interaction. 

### Part One: Markup

#### Tooltip in Input Field

It is possible to provide an accessible tooltip in an input field- without any JavaScript. By using the `aria-describedby` attribute and the appropriate CSS, the helpful hint can be made visible once the user has focused the input field. 

The following code would be valid inside of a &lt;form&gt; element:

```markup
<div class="form-group">
  <label for="input-userName">Username</label>
  <input type="text" id="input-userName" aria-describedby="userName-hint" name="userName" />
  <div role="tooltip" id="username-hint">Your username or email address is acceptable</div>
</div> 
```

By setting the `div[role="tooltip"]` \(or adding an explicit class to the element for this purpose\) to `display: none;`, the tooltip can then be revealed with a bit of additional CSS: 

```css
input:focus + [role="tooltip"] {
  display: block;
  position: absolute;
  top: 100%;
}
```



### Part Two: Ember Component

coming soon

### Part Three: Abstracting for Reuse

coming soon!

### References

1. [Accessible Input Tooltips](http://heydonworks.com/practical_aria_examples/#input-tooltip) by Heydon
2. [Building Accessible Tooltips](https://www.sarasoueidan.com/blog/accessible-tooltips/) by Sara Soueidan

