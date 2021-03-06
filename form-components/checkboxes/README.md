# Checkboxes

## Introduction

Checkboxes are a useful input element when it is desirable to allow users to select more than one option from a short list of options. Checkboxes can have three states: checked, not checked, and indeterminate.

### User Expectations

Users expect the following to be true:

* it should be possible to navigate via keyboard 
* animations should not be linked to functionality; if the user has disabled animations via system preferences, the checkbox should still be usable
* there should be a clear indicator of focus
* clicking on the label for the checkbox should also activate the checkbox itself \(this is done through properly [associating the label](../../general-considerations/considering-forms.md#labels) with the checkbox\)

## Part One: Considering Markup

Sometimes, a single checkbox is desirable. In these cases, a checkbox input only requires an associated label for the input:

```markup
<div class="form-group">
  <input type="checkbox" id="input_checkbox" name="terms-confirmation" />
  <label for="input_checkbox">I confirm that I have read the terms and conditions</label>
</div>
```

If the user should be able to select more than one option, a checkbox group should be used. To ensure that all of the checkboxes are associated with the single group, the `name` attribute value should be the same, and the checkbox group should be wrapped with the `<fieldset>` element:

```markup
<fieldset>
  <legend>What kind of jobs are you interested in (select all that apply)?</legend>
  <div class="form-checkbox">
    <input type="checkbox" id="checkbox_job-preferences-00" name="jobPreferences" />
    <label for="checkbox_job-preferences-00">Database Engineer</label>
  </div>
  <div class="form-checkbox">
    <input type="checkbox" id="checkbox_job-preferences-01" name="jobPreferences" />
    <label for="checkbox_job-preferences-01">CSS Engineer</label>
  </div>
  <div class="form-checkbox">
    <input type="checkbox" id="checkbox_job-preferences-02" name="jobPreferences" />
    <label for="checkbox_job-preferences-02">Accessibility Engineer</label>
  </div>
  <div class="form-checkbox">
    <input type="checkbox" id="checkbox_job-preferences-03" name="jobPreferences" />
    <label for="checkbox_job-preferences-03">Platform Engineer</label>
  </div>
</fieldset>
```

### Keyboard Support

| Key | Function |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left"><code>TAB</code>
      </th>
      <th style="text-align:left">
        <ul>
          <li>Moves keyboard focus among the checkboxes</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<table>
  <thead>
    <tr>
      <th style="text-align:left"><code>SPACE</code>
      </th>
      <th style="text-align:left">
        <ul>
          <li>Cycles the tri-state checkbox among unchecked, mixed, and checked states.</li>
          <li>When the tri-state checkbox is unchecked, all the controlled checkboxes
            are unchecked.</li>
          <li>When the tri-state checkbox is mixed, the controlled checkboxes return
            to the last combination of states they had when the tri-state checkbox
            was last mixed or to the default combination of states they had when the
            page loaded.</li>
          <li>When the tri-state checkbox is checked, all the controlled checkboxes
            are checked.</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

Ember has a checkbox input helper- [https://guides.emberjs.com/release/templates/input-helpers/\#toc\_checkboxes](https://guides.emberjs.com/release/templates/input-helpers/#toc_checkboxes) - but it should not be used in the place of common sense. Use this helper if it is sensible to do so.

\(More explicit guidance and additional scenarios coming soon\)

## Part Three: Abstracting for reuse

Coming soon!

## References

* [https://www.w3.org/TR/wai-aria-practices-1.1/\#checkbox](https://www.w3.org/TR/wai-aria-practices-1.1/#checkbox)
* [https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox)
* [https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/checkbox\_role](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/checkbox_role)
* [https://codepen.io/jensimmons/pen/KKPzxJa](https://codepen.io/jensimmons/pen/KKPzxJa)

{% hint style="info" %}
Feedback is welcome! Visit the [GitHub repository for this project](https://github.com/MelSumner/ember-component-patterns) to raise an issue.
{% endhint %}

