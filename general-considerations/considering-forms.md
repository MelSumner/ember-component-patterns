---
description: >-
  This page contains some general knowledge that may be helpful to review before
  looking at the form component guides.
---

# Considering Forms

### Labels

All form inputs are required to have an associated `<label>` element. The `<label>` element should not be used in any other context. 

To associate a form input and a label, the value of the `for` attribute in the &lt;label&gt; element should match the value of the input's `id` attribute. See this truncated example: 

```markup
<label for="IDREF">Label Text</label>
<input id="IDREF" />
```

It should then be considered how to generate such a thing, since IDs must be unique. There are two approaches for Ember applications: 

#### UUID

One approach is to create a [`uuid`](https://en.wikipedia.org/wiki/Universally_unique_identifier) as a variable within the component, and increment the value as needed. If this approach is used, care must be taken to ensure that the values generated are valid values as per the HTML specification: 

* _**must**_ begin with a letter \(\[A-Za-z\]\) 
* may be followed by any number of letters, digits \(\[0-9\]\), hyphens \("-"\), underscores \("\_"\), colons \(":"\), and periods \("."\)

#### GUIDFOR

Ember has [`guidFor`](https://api.emberjs.com/ember/release/functions/@ember%2Fobject%2Finternals/guidFor) which returns a unique ID for the object. If the object does not yet have a guid, one will be assigned to it, and it can be called on any object, including DOM element objects. 

{% hint style="info" %}
While it is also valid to wrap the input in a `<label>` element and avoid using the `for` attribute entirely, this approach is not advised because it limits the designs that can be used. When considering how the code is written, it is essential to consider flexibility for styling as an integral part of the approach. Set your future up for success!
{% endhint %}



