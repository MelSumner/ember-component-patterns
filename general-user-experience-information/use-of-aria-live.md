# Use of aria-live

The `aria-live` attribute should be used with _**extreme**_ caution, as it can provide an incredibly poor user experience for users with assistive technology. 

Because the `aria-live` attribute can be used on any HTML element, and effects _all_ child elements of the element marked with the attribute, a thorough understanding of how this role works and when to use it is especially necessary for competent software engineers who build web-based solutions. 

The `aria-live` attribute can have a few different values \(`POLITENESS_SETTING`\): `off`, `polite`, and `assertive`. 

### Politeness Setting: Off

> Assistive technologies should not announce updates unless the assistive technology is currently focused on that region.

Regions which contain information that will receive updates but are not critical for users to know about immediately can be marked with `aria-live="off"`. Once that region has \(user-driven\) focus, the updates will be made known. 

### Politeness Setting: Polite

> Assistive technologies should announce updates at the next graceful opportunity \(e.g., end of the current sentence\).

Regions that contain warning notifications that users _may_ need to know can be marked with `aria-live="polite"`. 

### Politeness Setting: Assertive

> Assistive technologies should announce updates immediately.

Regions that contain urgent alerts or notifications \(such as error alerts\) that are imperative for users to know immediately should use `aria-live=assertive`. 

### Be aware of pitfalls

The aria-live attribute should not be used for dynamic content that is non-critical. Of course, what constitutes critical should be driven only by determining if the content is important to the specific purpose of the page. 

The purpose of the page should be clearly indicated by the `<title>` element in the page `<head>`. Another clue should be the `<h1>` of the page, which should also clearly indicate the purpose of that page. 

It is a common practice to asynchronously load other page content like sidebar widgets or tabular data. In both of these instances, the areas should be marked with `aria-live=off` so they can indicate the updated information only once the user focuses on those elements. 

