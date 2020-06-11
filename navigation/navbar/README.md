# Navbar

## Introduction

Using the `<nav>` element can make groups of links easier to locate and skip past by users of assistive technology such as screen readers.

## Part One: Considering Markup

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

{% hint style="info" %}
Why put a list element inside of the `<nav>` element?   
  
The `<nav>` element informs screen reader users that they are in a part of the page that relates to navigation and provides a "landmark" for them to be able to navigate to with a shortcut. The list inside the `<nav>` informs screen reader users that there is a "list of N items" where N is the number of `<li>`elements inside the ol/ul, and this helps screen reader users judge the size of the navigation block and from there to decide on their strategy for navigating through it, over it, or something else.
{% endhint %}

//TODO adding toggle for mobile nav support

### Keyboard Support

| Key | Function |
| :--- | :--- |
| `TAB` | Traverse through the active links |
| `ESC` | should close any open sub-navigation lists |

## Part Two: Creating the Ember Component

### Generate the component:

```text
ember generate component navbar -gc
```

Three files will be created:

* app/components/navbar.js
* app/components/navbar.hbs
* tests/integration/components/navbar-test.js

### Template

Convert the HTML markup:

```markup
<nav>
  <ul class="navbar-list">
    {{#each this.navLinks as |link| }}
      <li><a href={{link.href}}>{{link.name}}</a></li>
    {{/each}}
  </ul>
</nav>
```

### Component

In the `navbar.js` file, some functionality will need to be defined. For this example, routes "alpha" and "bravo" represent sample routes:

```javascript
import Component from '@glimmer/component';

export default class NavbarComponent extends Component {
  navLinks = [{
    "href": '/alpha',
    "name": 'Alpha'
  }, {
    "href": '/bravo',
    "name": 'Bravo'
  }];
}
```

//TODO add actions associated with toggle

### Component Invocation

To use the component in a page or view template, add:

```text
<Navbar />
```

## Part Three: Abstracting for Reuse

Coming Soon!

## References:

* "[Don't use ARIA Menu Roles for Site Nav](http://adrianroselli.com/2017/10/dont-use-aria-menu-roles-for-site-nav.html)" by Adrian Roselli
* Related technique: [Using ARIA landmarks to identify regions of a page](http://www.w3.org/TR/WCAG20-TECHS/ARIA11.html)
* Related technique: [Using semantic elements to markup structure](http://www.w3.org/TR/2012/NOTE-WCAG20-TECHS-20120103/G115)
* 
{% hint style="info" %}
Feedback is welcome! Visit the [GitHub repository for this project](https://github.com/MelSumner/ember-component-patterns) to raise an issue.
{% endhint %}

