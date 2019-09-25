---
description: AKA Combobox.
---

# Typeahead

### Introduction

The typeahead or combobox component is usually similar to a textbox where users can type ahead to select an option, or sometimes even type arbitrary text as a new item to add to the list. 

It is a combination of a single line input field with a popup, typically a listbox. 

Because this field is editable and is typically used for autocomplete behavior \(to help the user find things more quickly\), the `aria-autocomplete` attribute should be used. 

There are four forms of autocomplete that are acceptable: 

1. **no autocomplete**: the suggested values that appear are the same, no matter what the user has typed in the textbox.  
2. **list autocomplete with manual selection**: the suggested values that appear contain values that complete or otherwise logically correspond with the characters that the user has typed into the textbox. However, the characters that the user has typed will be the value of the textbox unless the user manually selects a value displayed in the popup. 
3. **list autocomplete with automatic selection**: the suggested values that appear, contain values that complete \(or otherwise logically correspond with\) the characters that the user has typed into the textbox, and the first suggestion is automatically highlighted as selected. The automatically selected suggestion becomes the value of the textbox when the combobox loses focus, unless the user manually chooses a different suggestion.  
4. **list with inline autocomplete**: after the user types a certain number of characters, suggestions display inline after the input cursor in the textbox \(known as a completion string\). The suggested completion string should update as the user types additional characters. 



### Part One: Markup

#### Keyboard Interactions

| Key | Action |
| :--- | :--- |
| UP arrow / DOWN arrow  | cycle through the auto-suggestions and input field |
| `ESC` | close the listbox \(if open\) |
| `ENTER` | select the currently focused auto-suggestion item and close the listbox |
| `TAB` | select the currently focused auto-suggestion, close the menu, and move focus to the next focusable element |

text

### Part Two: Ember Component

text

### Part Three: Abstracting for Reuse

coming soon!

### References

* 
