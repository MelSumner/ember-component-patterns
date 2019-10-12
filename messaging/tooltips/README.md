# Tooltips

### Introduction

A tooltip is a useful way to provide the user with a hint or additional context about a specific user interface. It is typically activated on hover, but should also be able to be activated when the element is brought into focus via keyboard interaction. 

It is always advisable to make room for text with icons; however the reality of things is that sometimes sufficient care has not been taken to provide room for them in the design. If this is the case, sufficient effort should be made to have the necessary conversations about adopting a more inclusive design. 

{% hint style="info" %}
It is with all certainty that I say this: if text is important, design will make room for it. If there is "no room" it means that it wasn't important _enough_ to those responsible for the design. 
{% endhint %}

This guide will cover traditional tooltips and two variations- tooltips for input fields, and tooltips that toggle and will work for touch interactions. 

### Part One: Markup

#### Traditional Tooltips

The standard tooltip will appear when the user hovers over the element, or tabs to the interactive element and brings it into focus. Moving the mouse away from the element, or pressing the `ESC` key should both close the tooltip. 

For this example, a tooltip will be attached to a button element: 

```markup
<div class="wrapper-tooltip">
	<button aria-describedby="tooltip">I have a tooltip</button>
	<div id="tooltip" role="tooltip">Tooltips provide additional context or additional help text for the user.</div>
</div>
```

A little CSS will help this work:

```css
.wrapper-tooltip {
  position: relative;
}

[role="tooltip"] {
	background-color: #2d2d2d;
	border-radius: 6px;
	color: white;
	display: none;
	margin-top: 0.2em;
	padding: 0.5em;
  position: absolute;
	width: 300px;
}

button:hover + [role="tooltip"],  
button:focus + [role="tooltip"] {  
  display: block;
}
```

![The basic rendered tooltip is displayed when the button has hover or focus](../../.gitbook/assets/image%20%2811%29.png)

This is a very basic pattern; there is more to consider if additional positioning is desired. JavaScript will need to be used to provide the ability to dismiss the tooltip with the `ESC` key:

```text
//TODO
```

#### Tooltips For Input Fields

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

#### Tooltips on Interaction

 Tooltips that are touch-screen friendly will act more like a toggle than a traditional tooltip. 

//TODO include pattern                                                                                                                                                                                                                                                                                                                                         





### Part Two: Ember Component

coming soon!

### Part Three: Abstracting for Reuse

coming soon!

### References

1. [Accessible Input Tooltips](http://heydonworks.com/practical_aria_examples/#input-tooltip) by Heydon
2. [Building Accessible Tooltips](https://www.sarasoueidan.com/blog/accessible-tooltips/) by Sara Soueidan
3. [ARIA Tooltip](http://pauljadam.com/demos/tooltip.html) by Paul Adam

