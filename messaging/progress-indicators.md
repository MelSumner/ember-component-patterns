# Progress Indicators

In general, this is what should happen:

* have a container that's empty on page load, with `aria-live="..."` or a relevant \(implicit or explicit\) live region role.
* once the page is loaded, the content can be updated dynamically, and this change will trigger an announcement by assistive technology\(AT\).

{% hint style="info" %}
The alerts announcing **after** page load, once content is actually injected into the container, is how loading indicators generally should behave. However, some browser/AT combos fire an explicit announcement _on page load_ is a bug/inconsistency. 
{% endhint %}

