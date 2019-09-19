# Checkboxes

### Introduction

Checkboxes are a useful input element to use when it is desirable to allow users to select more than one option. Checkboxes can have three states: checked, not checked, and indeterminate. 

### Part One: Markup

Sometimes, a single checkbox is desirable. In these cases, a checkbox input only requires an associated label input: 

```text
<div class="form-group">
  <input type="checkbox" id="input_checkbox" name="terms-confirmation" />
  <label for="input_checkbox">I confirm that I have read the terms and conditions</label>
</div>
```

If the user should be able to select more than one option, a checkbox group should be used. To ensure that all of the checkboxes are associated with the single group, the `name` attribute value should be the same: 

```text
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

#### Keyboard Support

<table>
  <thead>
    <tr>
      <th style="text-align:left">Key</th>
      <th style="text-align:left">Function</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>TAB</code>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Moves keyboard focus among the checkboxes</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>SPACE</code>
      </td>
      <td style="text-align:left">
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
      </td>
    </tr>
  </tbody>
</table>### Part Two: Ember Component

Ember has a checkbox input helper-  [https://guides.emberjs.com/release/templates/input-helpers/\#toc\_checkboxes](https://guides.emberjs.com/release/templates/input-helpers/#toc_checkboxes) - but it should not be used in the place of common sense. 



### Part Three: Abstracting for reuse

text

### References

* [https://www.w3.org/TR/wai-aria-practices-1.1/\#checkbox](https://www.w3.org/TR/wai-aria-practices-1.1/#checkbox)
* [https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox)
* [https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/checkbox\_role](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/checkbox_role)
* [https://codepen.io/jensimmons/pen/KKPzxJa](https://codepen.io/jensimmons/pen/KKPzxJa)

### Conclusion

