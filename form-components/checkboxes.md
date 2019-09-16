# Checkboxes

### Introduction

Checkboxes are a useful input element to use when it is desirable to allow users to select more than one option. 

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

### Part Two: Ember Component

text

### Part Three: Abstracting for reuse

text

### Conclusion

