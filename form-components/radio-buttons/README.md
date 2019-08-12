---
description: The radio button input. To be used with Ember 3.13+
---

# Radio Buttons

### Introduction

Although the radio button input is a simple component, it is one that is very easily constructed in a way that is detrimental to not only an application's performance but also the experience for users with assistive technology. This guide will examine successful patterns for development, and where possible, illuminate pitfalls that authors should avoid in order to successfully deliver a performant and accessible component. 

It should not be assumed that a component pattern that appears polished is technically sound. For example, consider the radio button offered by Material Design: 

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

Just to make this **one** radio button in Material Design, the following would be needed:

| HTML | CSS | JavaScript |
| :--- | :--- | :--- |
| 6 elements | 66 selectors | 2,374 lines \(unminified\) |
| 9 attributes | 141 properties | 30k minified |
| DOM depth of 3 | 10k minified |  |

Since any app will likely need more than just one radio button, and the above is far too obtuse for use in modern applications, considerations should be made for how the appropriate markup can be achieved in a much more efficient way. 

For additional patterns to avoid, see the [anti-patterns page](antipatterns-radio-buttons.md). 

### Part One: Considering Markup

Now consider this markup which uses semantic HTML to obtain the same effect:

```markup
<div class="radio-button">
  <input
    type="radio"
    id="city-chicago"
    name="city">
  <label for="city-chicago">Chicago</label>
</div>
```

This is all that is needed. 

If extra styling on the radio button is desired, the [pseudo elements in CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements), rather than extra markup in the DOM, should be used. To see examples of how this could be done, visit the [Styling: Radio Buttons page](styling-radio-buttons.md). 

Of course, there are more options that will need to be build into this pattern, so consideration for those should be planned for next, as it is preferred to plan out the component before building it.

#### Considering Attributes & Properties

First, consider the HTML attributes that might need to be added to this component \(in addition to the ones that were already indicated in the markup sample\). It should be observed that the boolean attributes in HTML work a little differently than they do in JS. For these attributes, they must be omitted all together to indicate a `false` value. If `true`, the attribute name is only present. Consider these examples for a disabled radio button:

Correct:

```markup
<input type="radio" disabled />
```

Incorrect:

```markup
<input type="radio" disabled="true" />
```

Additionally, consideration for the difference between `disabled` and `readonly` is important- when a form is submitted, information marked as `readonly` **will** be sent to the server upon submit, whereas information marked `disabled` **will not**. 

#### Radio Group

A radio button is, by nature, not going to be used alone \(in those instances, a checkbox is the correct choice\). It is reasonable, then, to consider how all the parts would work together in the whole. Here is an example that could be used to give a user an opportunity to indicate contact method preference:

```markup
<fieldset>
  <legend>Preferred Location</legend>
  <div class="radio-button">
    <input
      type="radio"
      id="city-austin"
      name="location-preference"
      value="austin">
    <label for="city-austin">Austin</label>
  </div>
  <div class="radio-button">
    <input
      type="radio"
      id="city-boston"
      name="location-preference"
      value="boston">
    <label for="city-boston">Boston</label>
  </div>
  <div class="radio-button">
    <input
      type="radio"
      id="city-portland"
      name="location-preference"
      value="portland">
    <label for="city-portland">Portland</label>
  </div>  
</fieldset>
```

The power of CSS makes it possible to use completely semantic markup and maintaining a separation of concerns where design is concerned- this means we do not need to use markup for styling. 

\(TODO: insert some examples of how this markup could be styled differently to achieve different visual designs\)

{% hint style="info" %}
Note: it is common to have an option pre-selected for users. An agreeable default selection can lower the amount of time the user spends filling out a form, which is always a bonus! To increase user happiness, a plan should be devised to revisit details \(such as default selection\) once an appropriate amount of data has been gathered. Observe which option users tend to choose the most and make that the default option, for extra delight! 
{% endhint %}

Now that well-crafted \(by which I mean semantic, performant, and accessible\) markup exists, it can be converted into an Ember Component. 

### Part Two: Creating the Ember Component

Generate the component:

```bash
$ ember generate component radio-group
```

In the generated template/component file, add this markup:

```markup
<fieldset>
  <legend>{{@title}}</legend>
  {{#each @cityNames as |cityName| }}
    <div class="radio-button">
      <input
        type="radio"
        id="city-{{cityName}}"
        name={{@name}}
        value={{cityName}}
        >
      <label for="city-{{cityName}}">{{cityName}}</label>
    </div>
  {{/each}}
</fieldset>
```

//TODO conditionals

//TODO models for components? not routes. What are we doing in Octane? Guides only show routes... 

The component can then be added to the template:

```markup
<RadioGroup 
  @title="Preferred Location"
  @cityNames={{this.model}}
  @name="location-preference"
/>
```

#### Additional Considerations

If it is desirable to allow some attributes to be changed when the component is placed into the template, the specific placement of `...attributes` will allow the author to indicate which attributes can be changed and which cannot. To learn more about this, visit [https://octane-guides-preview.emberjs.com/release/upgrading/editions/\#toc\_attributes](https://octane-guides-preview.emberjs.com/release/upgrading/editions/#toc_attributes). 

### References

1. [Excessive DOM Size](https://developers.google.com/web/tools/lighthouse/audits/dom-size) \(Audit reference, performance\)
2. [MDN Reference: Radio Buttons](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio)
3. Talk: [The Intersection of Performance and Accessibility](https://noti.st/ericwbailey/Yfyaxa)
4. [HTML Standard: Boolean Attributes](https://html.spec.whatwg.org/multipage/common-microsyntaxes.html#boolean-attributes)
5. [Pseudo Elements in CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)
6. [Styling: Radio Buttons](styling-radio-buttons.md)

