---
description: >-
  Tooltips should provide extra information to the user, and shown only when the
  item has focus. They should not contain interactive elements.
---

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

The standard tooltip will appear when the user hovers over the element, or tabs to the interactive element and brings it into focus. Moving the mouse away from the element should both close the tooltip. 

For this example, a tooltip will be attached to a button element: 

```markup
<div class="tooltip">
  <a href="#tooltip" class="tooltip-trigger" aria-describedby="tooltipText">
    I have a tooltip
  </a>
  <div id="tooltipText" class="visually-hidden tooltip-content" role="tooltip" tabindex="-1">
    Tooltips provide additional context or additional help text for the user.
  </div>
</div>
```

A little CSS will help this work- note that your exact dimensions may vary.

```css
.visually-hidden {
  clip: rect(1px 1px 1px 1px);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}

.tooltip {
  position: relative;
  display: inline-block;
}

.tooltip-content {
  background-color: #fff;
  border: 1px solid black;
  left: 0;
  opacity: 0;
  padding: 0.25em;
  top: 20px;
}

.tooltip-trigger:hover + .tooltip-content,
.tooltip-trigger:focus + .tooltip-content,
.tooltip-content:hover,
.tooltip-content:focus {
  clip: auto;
  height: auto;
  opacity: 1;
  overflow: visible;
  white-space: normal;
  width: 200px;
}
```

![The basic rendered tooltip is displayed when the button has hover or focus](../../.gitbook/assets/image%20%2811%29.png)

This is a very basic pattern; there is more to consider if additional positioning is desired. 

### Part Two: Ember Component \(for reuse\)

To turn this into an Ember Component that we can reuse throughout our app, we'll generate a component with a class file, and then add the template markup to the `.hbs` file and some auto-generated `id` attributes to the component's `.js` file, so that elements are associated appropriately for assistive technology.

#### generate tooltip component 

```bash
ember generate component tooltip -gc
```

#### tooltip.hbs

```markup
<div class="tooltip">
  <a href="#{{this.tooltipId}}" class="tooltip-trigger" aria-describedby={{this.tooltipTextId}}>{{@textWithTooltip}}</a>
  <div id="{{this.tooltipTextId}}" class="visually-hidden tooltip-content" role="tooltip" tabindex="-1">
    {{@tooltipText}}
  </div>
</div>
```

#### tooltip.js

```javascript
import Component from '@glimmer/component';
import { guidFor } from '@ember/object/internals';

export default class TooltipComponent extends Component {
  tooltipId = 'tooltip-' + guidFor(this); 
  tooltipTextId = 'tooltipText-' + guidFor(this);
}
```

Then, we can use the component in our template:

```markup
<Tooltip 
  @textWithTooltip="I have a tooltip" 
  @tooltipText="Tooltips can provide additional context for the user." 
/>
```

This will help you implement a simple tooltip in your app. If additional functionality is needed, it is likely that a different kind of tooltip, known colloquially as a toggletip, may be desired.

