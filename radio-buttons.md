---
description: The radio button input.
---

# Radio Buttons

### Introduction

The radio button input is a simple component, but it is one that is very easy to do in a way that is detrimental to the performance of your application and to users with assistive technology. 

Consider something like Material Design: 

```markup
<div class="mdc-radio">
  <input
    class="mdc-radio__native-control"
    type="radio"
    id="city-chicago"
    name="city">
  <div class="mdc-radio__background">
    <div class="mdc-radio__outer-circle"></div>
    <div class="mdc-radio__inner-circle"></div>
  </div>
</div>
<label for="city-chicago">Chicago</label>
```

Just to make this one radio button, you need:

| HTML | CSS | JavaScript |
| :--- | :--- | :--- |
| 6 elements | 66 selectors | 2,374 lines \(unminified\) |
| 9 attributes | 141 properties | 30k minified |
| DOM depth of 3 | 10k minified |  |

And this is just one radio button- your app will likely need more than just one. So let us consider how we can achieve the appropriate markup in a much more efficient way. 

### Step One: Semantic HTML

Let us now consider using this markup, which can give us the same effect:

```text
<div class="radio">
  <input
    type="radio"
    id="city-chicago"
    name="city">
  <label for="city-chicago">Chicago</label>
</div>
```

This is all we need. 

If extra styling on the radio button is desired, _reach for pseudo elements in CSS_, rather than extra markup in the DOM. 

Of course, there are more options that will need to be build into this pattern in an Ember Component. 

### Step Two: Ember

First, consider the HTML attributes that might need to be added to this component \(in addition to the ones that were already indicated in the markup sample: 

* disabled, readonly, required - these boolean attributes work a little differently than may be expected, if one is not familiar with HTML.  For example:

Correct:

```text
<input type="radio" disabled />
```

Incorrect:

```text
<input type="radio" disabled="true" />
```



### References

1. [Excessive DOM Size](https://developers.google.com/web/tools/lighthouse/audits/dom-size)
2. Talk: [The Intersection of Performance and Accessibility](https://noti.st/ericwbailey/Yfyaxa)
3. 
