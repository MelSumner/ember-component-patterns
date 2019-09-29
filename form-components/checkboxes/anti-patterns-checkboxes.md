# Anti-patterns: Checkboxes

### Anti-pattern \#1: heading as checkbox group label

The use of the header element with a wrapper div around a group of checkboxes may be a tempting approach at first sight. 

Consider this: 

```markup
<div class="checkbox-group">
  <h3>What are your preferred job titles?</h3>
  <div class="form-group__checkbox">
    <input id="c-00" type="checkbox" name="prefJob" value="ninja">
    <label for="c-00">Ninja</label>
  </div>
  <div class="form-group__checkbox">
  	<input id="c-01" type="checkbox" name="prefJob" value="unicorn">
   	<label for="c-01">Unicorn</label>
  </div>
  <div class="form-group__checkbox">
    <input id="c-02" type="checkbox" name="prefJob" value="rockstar">
   	<label for="c-02">Rockstar</label>
  </div>
</div>
```

At first glance, all might seem fine. However, as assistive technology such as a screen reader will not associate the title and the options correctly, this approach should be considered an anti-pattern and should be avoided. 

Instead, use the `<fieldset>` with a `<legend>` to successfully contain and associate the checkbox group. It should be remembered that the default styling for these elements can be overridden and should not be considered a blocker for their use. 

