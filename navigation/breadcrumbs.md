# Breadcrumbs

### Introduction

//TODO

Breadcrumbs are useful on large websites -- single-level websites should not use them. 

### Part One: Considering Markup

//TODO

```markup
<nav class="breadcrumb-nav" aria-label="Breadcrumb">
  <ol>
    <li>
      <a href="/">
        Index
      </a>
    </li>
    <li>
      <a href="/alpha">
        Alpha
      </a>
    </li>
    <li>
      <a href="/alpha/child" aria-current="page"> 
        This page
      </a>
    </li>
  </ol>
</nav>
```

The dividers between each list item should be created via CSS \(alone\), using pseudo elements. Using CSS to create a divider will allow for visual separator that will not be announced by a screen reader. 

### Part Two: Creating the Ember Component

//TODO

### Part Three: Abstracting for Reuse

Coming Soon! 

### References

* Addon: [Ember Breadcrumbs](https://github.com/chrisfarber/ember-breadcrumbs)
* [Accessible Breadcrumbs](https://scottaohara.github.io/a11y_breadcrumbs/) by Scott O'Hara

{% hint style="info" %}
Feedback is welcome! Visit the [GitHub repository for this project](https://github.com/MelSumner/ember-component-patterns) to raise an issue.
{% endhint %}

