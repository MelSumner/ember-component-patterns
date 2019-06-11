# Modals

The \#1 issue for any modal is lack of focus trapping. No matter what approach authors decide to take, authors must ensure that focus is contained to the modal when the modal is open. This means that when the user navigates with a keyboard \(TAB key, for example\) or a mouse, they are not able to navigate to any content outside of the modal window.

### Requirements

All modals must support the following: 

* A modal must only appear after the user has taken a specific action to trigger it. 
* A modal must not appear automatically. For example: 
  * Unacceptable: the user visits a page and a modal immediately pops up, or appears after a set interval. 
  * Acceptable: the user submits a form, and a modal pops up to invite them to review their submission before proceeding. 
* A machine-readable title. This means that a title should be present for assistive technology \(AT\) such as screen-readers to use, whether visible or not \(tip: it benefits _all_ users to have a visible title\). 
* Keyboard navigation support  
* Focus management: All modals must keep focus in the modal window until the user interacts with the modal to dismiss it.

### Keyboard Support

<table>
  <thead>
    <tr>
      <th style="text-align:left">Keystroke</th>
      <th style="text-align:left">What It Should Do</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>TAB</code>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Moves the focus to the next interactive element inside of the modal.</li>
          <li>If focus is on the last interactive element inside of the modal,
            <br />move the focus to the first interactive element inside of the modal.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>SHIFT + TAB</code>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Moves the focus to the previous interactive element inside of the modal.</li>
          <li>If the focus is on the first interactive element inside of the modal,
            <br
            />move the focus to the last interactive element inside of the modal.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>ESC</code>
      </td>
      <td style="text-align:left">
        <ul>
          <li>close the modal window and return the user to the previously focused element.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>### Focus-Trapping Approaches

There are some common approaches used to provide focus-trapping in modals:

1. keep track of the first interactive element and the last interactive element. Only allow focus to move to the appropriate one \(`TAB` vs `SHIFT + TAB`\)
2. use the inert browser polyfill.

### Sample Markup

Here is some sample markup for a modal \(before it is active\):

```markup
<div aria-labelledby="modal-heading" role="dialog" tabindex="-1">
  <div data-modal-document="" role="document">
    <h2 id="modal-heading">
      Modal Title
    </h2>
    <button aria-label="Close" type="button">
     <span data-modal-x=""></span>
    </button>
    <!-- Modal content goes here -->
  </div>
</div>
```

### Ember Addons

Check [https://emberobserver.com/](https://emberobserver.com/) for a list of all published modal addons.

**ember-modal-dialog** - [https://github.com/yapplabs/ember-modal-dialog](https://github.com/yapplabs/ember-modal-dialog) is one of the most popular modal dialogs for Ember apps. However, users should be aware of [a11y issues](https://github.com/yapplabs/ember-modal-dialog/issues/236) before using this addon. 

**e-a11y-modal** - This addon is intended to provide a simple, accessible, button-triggered modal. For the user with a screen reader, either the modal will exist, or the rest of the page will exist, but never both at the same time.



### References

* [http://w3c.github.io/aria-practices/examples/dialog-modal/dialog.html](http://w3c.github.io/aria-practices/examples/dialog-modal/dialog.html)

