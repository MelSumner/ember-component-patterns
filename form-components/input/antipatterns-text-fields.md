---
description: >-
  Anti-patterns produce outcomes that are ineffective because they are not
  complete solutions, and as such are counterproductive. Developers are advised
  to be aware of anti-patterns and avoid their use.
---

# Anti-patterns: Text Fields

### Anti-pattern \#1: Placeholder as a label substitute

It is common for developers who are fully sighted to forget that many different kinds of people use the internet- including people with no vision. It is vital that all input fields have associated label elements. 

Anti-pattern example to **avoid**: 

```markup
<div class="form-group">
  <input type="text" name="firstName" placeholder="Zoey" />
</div>
```

### Anti-pattern \#2: Input fields that automatically do...anything. 

#### Automatically submitting an input/form

To avoid surprising the user \(in a not good way\), input fields should only submit information when the "submit" button has been pressed/clicked on by the user. 

#### Automatically update information in other places

Any page updates should come only as a result of an explicit interaction from the user, and any information on the page that will receive this updated data should be marked with aria-live. See the [aria-live guide](../../general-considerations/use-of-aria-live.md) for information on how to use this attribute. 

