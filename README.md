---
description: >-
  This guide intends to be aligned with the idioms and syntax of the Octane
  edition of Ember.
---

# Ember Component Patterns

{% hint style="warning" %}
If you are reading this paragraph, then this guide has not yet been officially released. The first version of this guide is intended to be released with Ember 3.14, as they will employ syntax and idioms that are aligned with the [Octane edition](https://emberjs.com/editions/) of Ember.js. 
{% endhint %}

The goal of this guide is to cultivate a set of patterns that are practical and can reasonably be used by any Ember developer in their application. It is intended to be made publicly available with the release of Ember Octane.

The component patterns here will, at least initially, be completely without any CSS styling. This is to help clearly delineate form and function. "First, make it useful; then make it beautiful" as the saying goes. When necessary to demonstrate the validity of the approach, however, a sub-section on styling may be added to the pattern if it helps to demonstrate what might otherwise be thought of as impossible.  

As this project matures, the anti-patterns will be explored by adding more prose and explains to demonstrate why other options were not chosen, providing both a well-lit path and a knowledge base for the shadows.

What one can obtain from this collection of patterns depends on the reader; however a few potential types of readers, and possible goals, have been kept in mind. Some examples:  

### Developers

* write more technically accurate code 
* worry a little bit less about writing code that is not accessible
* have easy-to-reference base requirements for common component patterns
* have confidence in the code you produce

### Designers

* understand what components really need to have from a functional perspective
* ensure that designs will include the necessary functionality and accessibility
* focus on design within clear technical constraints

### BAs & TPMs

* reference to help you more accurately know base requirements for the new feature\(s\) you want to add to your project
* confidently plan out projects more accurately by reducing "unknown unknowns"

