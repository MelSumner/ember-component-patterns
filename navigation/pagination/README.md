# Pagination

## Introduction

Pagination is a useful pattern for allowing the user to view a subset of sorted data when it is unsuitable to display all of the data on a single screen.

### User expectations

The user expects the following things from a pagination component:

* it should be possible to navigate by keyboard
* it should be obvious to a screen reader that it is pagination navigation
* the currently active element should be very obvious
* it should be possible to navigate with "previous" and "next" indicators

## Part One: Considering Markup

A pagination component should resemble this when rendered in the browser:

```markup
<nav aria-label="pagination navigation">
    <ul>
      <li><a href="/page-2">Previous</a></li>
      <li><a href="/page-1">1</a></li>
      <li><a href="/page-2" aria-current="page">2</a></li>
      <li><a href="/page-3">3</a></li>
      <li><a href="/page-4">4</a></li>
      <li><a href="/page-5">5</a></li>
      <li><a href="/page-3">Next</a></li>

    </ul>
</nav>
```

## Part Two: Creating the Ember Component

best practices TBD. In the meantime, review addons available in [https://emberobserver.com/categories/pagination](https://emberobserver.com/categories/pagination) to see if any meet the above requirements and would be suitable for use in your application.

## Part Three: Abstracting for Reuse

Coming Soon!

## References

{% hint style="info" %}
Feedback is welcome! Visit the [GitHub repository for this project](https://github.com/MelSumner/ember-component-patterns) to raise an issue.
{% endhint %}

