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

```markup
<div class="form-group">
  <label for="typeaheadInput-001" id="label-001" class="combobox-label">
    Choice or Search Label Text
  </label>
  <div class="combobox-wrapper">
    <div role="combobox" aria-expanded="false" aria-owns="listbox-001" aria-haspopup="listbox" id="combobox-001">
      <input aria-autocomplete="list" aria-controls="listbox-001" id="typeaheadInput-001" type="text" />
    </div>
    <ul aria-labelledby="label-001" role="listbox" id="listbox-001" class="listbox hidden">
        <li class="listbox-result" role="option" id="option-001">Watermelon</li>
        <-- This will likely be a long list -->
    </ul>
  </div>
</div>
```

#### Keyboard Interactions

| Key | Action |
| :--- | :--- |
| arrow keys         | cycle through the auto-suggestions and input field |
| `ESC` | close the listbox \(if open\) |
| `ENTER` | select the currently focused auto-suggestion item and close the listbox |
| `TAB` | select the currently focused auto-suggestion, close the menu, and move focus to the next focusable element |

The keyboard interactions are important here, because there is definitely the risk of introducing serious keyboard navigation flaws -- the focus could escape the listbox and continue down the page, or conversely, the focus could get trapped inside of the listbox and never allow the user to escape out of the list. 

### Part Two: Ember Component

#### Generate the component

```text
ember generate component typeahead -gc
```

Three files will be created:

* app/components/typeahead.js
* app/components/typeahead.hbs
* tests/integration/components/typeahead-test.js

A few styles will need to be added, but the method to do so will depend on the overall CSS approach for the application. 

#### Add template code

In the `typeahead.hbs` file, the template code can be added: 

```markup
<div class="form-group">
  <label for={{this.inputId}}
       id={{this.labelId}}
       class="combobox-label">
    {{@typeaheadLabelText}}
  </label>
  <div class="combobox-wrapper">
    <div role="combobox"
        aria-expanded="false"
        aria-owns={{this.listboxId}}
        aria-haspopup="listbox"
        id={{this.comboboxId}}>
      <input type="text"
            aria-autocomplete="list"
            aria-controls={{this.listboxId}}
            id={{this.inputId}}>
    </div>
    <ul aria-labelledby={{this.labelId}}
        role="listbox"
        id={{this.listboxId}}
        class="listbox hidden">
      {{#each this.listboxOptions as |option index| }}
        <li class="listbox-result" role="option" id="{{this.listboxId}}-{{index}}">{{option}}</li>
      {{/each}}
    </ul>
  </div>
</div>
```

//TODO abstract/add show/hide

#### Component JS

From the template code above, it is clear that there are multiple associations happening for accessibility reasons. Using the same approach as for other form components, unique IDs can be generated: 

```javascript
import Component from '@glimmer/component';
import { guidFor } from '@ember/object/internals';

export default class TypeaheadComponent extends Component {
  inputId = 'typeaheadInput-' + guidFor(this); 
  comboboxId = 'combobox-' + guidFor(this);
  listboxId = 'listbox-' + guidFor(this);
  labelId = 'label-' + guidFor(this);

  listboxOptions = [ 
  // options here
  ];
}
```

//TODO the results list is returning the same ID so need to increment instead of just returning the guid. 

//TODO add keyboard support

#### Using the Component

The component is now ready to be used in the page or form template file:

```markup
<Typeahead @typeaheadLabelText="Choice or Search Label Text" />
```



### Part Three: Abstracting for Reuse

coming soon!

### References

* WAI-ARIA Authoring Practices 1.1 - Combo Box - [https://www.w3.org/TR/wai-aria-practices/\#combobox](https://www.w3.org/TR/wai-aria-practices/#combobox)

