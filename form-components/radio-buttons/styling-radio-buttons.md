---
description: Coming Soon!
---

# Styling: Radio Buttons

To style the label of the default selected radio button: 

```css
input[type="radio"]:default + label {
  /* styles here */
}
```

To style the label of the currently selected radio button: 

```css
input[type="radio"]:checked + label {
  /* styles here */
}
```

Sometimes a custom style is desired. To achieve this while ensuring that the radio button markup remains appropriately available to screen readers, the radio button should be visually hidden while set up to be positioned over the styled radio button replacement. 

```css
.radio-button {
	position: relative;
}

.radio-button > input[type="radio"] {
	-moz-appearance: none;
	-webkit-appearance: none;
	appearance: none; 
	background: none;
	opacity: .00001;
	z-index: 2;
}

.radio-button > label {
	display: inline-block;
	/* set padding as desired */
}


.radio-button > input[type="radio"],
.radio-button > label:before,
.radio-button > label:after {
	position: absolute;
	/* set other properties as desired */
}

.radio-button > input[type="radio"],
.radio-button > label:before,
.radio-button > label:after {
	border-radius: 100%;
	content: " ";
}

.radio-button > label:after {
	/* set properties (such as border-color) as desired */
}

.radio-button > label:before {
	border-color: transparent;
	/* set other properties (such as box-shadow) as desired */
}

.radio-button > input:checked ~ label:before {
	border-color: transparent;
	/* set other properties (such as box-shadow) as desired */
}

.radio-button > input:focus ~ label:before {
	border-color: transparent;
}

.radio-button > input:checked ~ label:after {
	/* set properties (such as border-color/width & box-shadow) as desired */
}

```

Finally, it is important to consider high-contrast settings. Here is a media query \(and sample code\) that could be used for that purpose:

```css
@media screen and (-ms-high-contrast: active) {
	.radio-button > input:checked ~ label:before {
		background: window;
		border: 6px solid buttonface;
		box-shadow: none;
	}
}
```

To see some opinionated styles in action, visit the [CodePen sample](https://codepen.io/melsumner/pen/9333b9017df850d9fbdd0dd8f805741a) specifically created for this purpose. 

