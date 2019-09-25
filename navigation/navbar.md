---
description: Current WIP
---

# Navbar

### Introduction

Using the `<nav>` element can make groups of links easier to locate and skip past by users of assistive technology such as screen readers. 

### Part One: Considering Markup

Mark up for a navbar is surprisingly simple: 

```markup
<nav>
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about">About Us</a></li>
        <li><a href="/contact">Contact Us</a></li>
    </ul>
</nav>
```

If there will be more than one `<nav>` element on a page, then each `<nav>` element should be given an `aria-label` attribute with a unique value. 

The primary navbar should be consistent across the entire site- meaning, the links presented in the navbar should not change when the user visits different pages. 

#### Keyboard Support

| Key | Function |
| :--- | :--- |
| `ESC` | If there is a drop down, pressing the `ESC` key should close it |
| `TAB` | Traverse through the active links |

### Part Two: Creating the Ember Component

#### Generate the component: 

```text
ember generate component navbar -gc
```

Three files will be created:

* app/components/navbar.js
* app/components/navbar.hbs
* tests/integration/components/navbar-test.js

#### Template

Convert the HTML markup: 

```markup
(template here)
```

#### Component

In the navbar.js file, some functionality will need to be defined: 

```text
component.js
```

#### Component Invocation

To use the component in a page or view template, add: 

```text
<Navbar />
```

### Part Three: Abstracting for Reuse

Coming Soon! 

### References: 

* "[Don't use ARIA Menu Roles for Site Nav](http://adrianroselli.com/2017/10/dont-use-aria-menu-roles-for-site-nav.html)" by Adrian Roselli
* Related technique: [Using ARIA landmarks to identify regions of a page](http://www.w3.org/TR/WCAG20-TECHS/ARIA11.html)
* Related technique: [Using semantic elements to markup structure](http://www.w3.org/TR/2012/NOTE-WCAG20-TECHS-20120103/G115)
* 
{% hint style="info" %}
Feedback is welcome! Visit the [GitHub repository for this project](https://github.com/MelSumner/ember-component-patterns) to raise an issue.
{% endhint %}



