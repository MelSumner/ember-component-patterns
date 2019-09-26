# Breadcrumbs

### Introduction

Breadcrumbs are a useful features for large websites that have the proper logical hierarchy  of content -- single-level websites do not need them \(and should not use them\). 

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

Coming Soon! Until then, review the Ember addon [Ember Breadcrumbs](https://github.com/chrisfarber/ember-breadcrumbs) to determine if it will suit your needs. 

### References

* * [Accessible Breadcrumbs](https://scottaohara.github.io/a11y_breadcrumbs/) by Scott O'Hara
* WAI-ARIA [Accessible Breadcrumbs](https://w3c.github.io/aria-practices/examples/breadcrumb/index.html)

{% hint style="info" %}
Feedback is welcome! Visit the [GitHub repository for this project](https://github.com/MelSumner/ember-component-patterns) to raise an issue.
{% endhint %}

