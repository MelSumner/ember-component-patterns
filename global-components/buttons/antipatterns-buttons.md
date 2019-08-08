# Antipatterns: Buttons

### Anti-pattern \#1: The div as a button

Really, this should be called "the `<div>` or `<span>` as a button."

Code example: 

```markup
<div class="button">button text</div>
```

This should be considered unacceptable for the following reasons: 

* there is no way for a machine to determine that it is a button
* a div is not an interactive element 
* non-interactive elements should not have interactions associated with them
* there is no way to keyboard navigate to this element
* there is no way to interact with this element using a keyboard

### Anti-pattern \#2: The "Almost" button

Code example: 

```markup
<div class="button" role="button">button text</div>
```

This sample is marked with the role of button, which provides a machine-readable way for it to be identified as a button. However, it should still be considered unacceptable for the following reasons: 

* a div is not an interactive element 
* non-interactive elements should not have interactions associated with them
* there is no way to keyboard navigate to this element
* there is no way to interact with this element using a keyboard


