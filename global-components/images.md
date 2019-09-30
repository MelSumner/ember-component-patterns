# Images

General guidelines for images Images can be used to enhance a website's visual presentation. 

#### ALT attributes

All `<img>` elements must have an `alt` attribute. 

If the image is purely decorative, leave the alt attribute empty and add role="presentation", like this: 

```markup
<img alt="" role="presentation" src="salad.jpg" />
```

If the image is informational, the alt attribute value should be a descriptive alternative for that image, like this: 

```markup
<img alt="a fluffy brown cat lays curled up by a window that overlooks a park" src="cat.jpg" />
```

Perhaps it is most useful to advise that alt text content should be revised until it gives an adequate description without viewing the image itself. This is a place where content editors can be quite useful, and it is recommended to employ them regularly to review this type of content. 

Typically, alt text should be kept under 125 characters, as some screen-readers cut off the alt text at this point. Do not permit "keyword stuffing" in alt tag content. 

Do not include words such as "picture of", "image of", or "logo for", but rather describe the image. Screen readers will announce that it is an image already, so including that text is redundant, and a bit irritating. 

