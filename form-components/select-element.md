# Select Element

### Introduction

As a general rule, the `<select>` element should be used \(instead of radio buttons\) if any of the following cases are true: 

1. there are more than 5-7 choices
2. there are a large number of _familiar_ options available \(there is no need to be able to compare the options\)
3. the default choice is the recommended choice

It is a common misconception that the select element is not enough for web development. While there are  some constraints on styling, the select element serves a specific purpose and should be used in those use cases. It is ill-advised to disregard the select component entirely simply because it does not support more complex use cases out of the box. 

### Part One: Markup

The select element markup is rather straight-forward- all of the options are grouped together in one list, or option groups are indicated. 

```markup
<div class="form-select">
	<label for="select-color">Select your preferred color:</label>
	<select name="colorPrefs" id="select-color">
		<option value="red">Red</option>
		<option value="orange">Orange</option>
		<option value="yellow">Yellow</option>
		<option value="green">Green</option>
		<option value="blue">Blue</option>
		<option value="indigo">Indigo</option>
		<option value="violet">Violet</option>
	</select>
</div>
```

Benefits provided by the semantic html element: 

* if a user clicks on the label, the focus will automatically go to the select element
* keyboard navigation is built in
* assistive technology \(like screen readers\) will already understand what this code is meant to do

If grouping is desired, the `<optgroup>` markup can be used:

```markup
<div class="form-select">
	<label for="select-activity">Select your preferred activity:</label>
	<select name="activityPrefs" id="select-activity">
		<optgroup label="Indoor">
			<option value="indoor-sewing">Sewing</option>
			<option value="indoor-painting">Painting</option>
			<option value="indoor-baking">Baking</option>
		</optgroup>
		<optgroup label="Outdoor">
			<option value="outdoor-climbing">Climbing</option>
			<option value="outdoor-hiking">Hiking</option>
			<option value="outdoor-horseback">Horseback Riding</option>
		</optgroup>
	</select>
</div>
```



### Part Two: Ember Component

text

### Part Three: Abstracting for Reuse

coming soon!

### Conclusion

text

### References

* [https://developer.mozilla.org/en-US/docs/Web/API/HTMLSelectElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLSelectElement)
* [https://blog.prototypr.io/7-rules-of-using-radio-buttons-vs-drop-down-menus-fddf50d312d1](https://blog.prototypr.io/7-rules-of-using-radio-buttons-vs-drop-down-menus-fddf50d312d1) 

