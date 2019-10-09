# Anti-patterns: Tooltips

### Anti-pattern \#1: data attribute + CSS only

One tempting tooltip uses the `data-` attribute and the CSS `content` property. 

Here's what the markup would look like:

```markup
<button data-tooltip="I’m the tooltip text.">I’m a button with a tooltip</button>
```

Here's what the CSS would look like: 

```css
[data-tooltip] {
  cursor: pointer;
  position: relative;
  z-index: 2;
}

[data-tooltip]:before,
[data-tooltip]:after {
  filter: progid: DXImageTransform.Microsoft.Alpha(Opacity=0);
  opacity: 0;
  pointer-events: none;
  visibility: hidden;
}

[data-tooltip]:before {
  background-color: #000;
  background-color: hsla(0, 0%, 20%, 0.9);
  border-radius: 3px;
  bottom: 150%;
  color: #fff;
  content: attr(data-tooltip);
  font-size: 14px;
  left: 50%;
  line-height: 1.2;
  margin-bottom: 5px;
  margin-left: -80px;
  padding: 7px;
  position: absolute;
  text-align: center;
  width: 160px;
}

[data-tooltip]:after {
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 5px solid #000;
  border-top: 5px solid hsla(0, 0%, 20%, 0.9);
  bottom: 150%;
  content: " ";
  font-size: 0;
  left: 50%;
  line-height: 0;
  margin-left: -5px;
  position: absolute;
  width: 0;
}


[data-tooltip]:hover:before,
[data-tooltip]:hover:after {
  filter: progid: DXImageTransform.Microsoft.Alpha(Opacity=100);
  opacity: 1;
  visibility: visible;
}
```

This is the produced tooltip: 

![A button with a tooltip](../../.gitbook/assets/image%20%285%29.png)

#### Why It Is An Anti-Pattern

This is an anti-pattern because assistive technology has no way of reading the content of the tooltip. Child elements of button elements are ignored in the accessibility tree. 

If the tooltip content is in a data attribute \(such as `data-tooltip`\), then JavaScript must be used.

