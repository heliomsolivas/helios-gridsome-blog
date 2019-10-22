---
title: CSS3 Transform Checkmark
date: 2019-01-01
published: true
tags: ['Quick Tips']
canonical_url: false
cover_image: ./images/quick-tips-2-fix.gif
description: "Hi everyone, today I’m gonna show a little tip / trick to create an easy checkmark. Most of times I have to do a custom checkbox, and I always use an image or a bootstrap icon (or something like that), so a discovered this way..."
---
# Easy CSS checkmark / tick

Hi everyone, today I’m gonna show a little tip / trick to create an easy checkmark. Most of times I have to do a custom checkbox, and I always use an image or a bootstrap icon (or something like that), so a discovered this way, and if you don’t need old browsers support, you can use easily.

First we had to create this structure:

```html
<label for="check">Click here to check the box</label>
    <input type="checkbox" id="check" name="check">
    <span class="select__radio">L<span>
```

I’ve created a label to check/uncheck the checkbox and set the input to hide. So basically I will create a span with a "L" word that will be the "check", if you rotate the "L" you can see something like a "check". You can do it using some CSS3 Transform:

```css
input[type="checkbox"]{
  display:none;
}
label{
  cursor:pointer;
}
.select__radio{
  height:40px;
  width:40px;
  background-color:#ccc;
  border-radius:50%;
  display:block;
  font-size:0;
}
input[type="checkbox"]:checked ~ .select__radio{
  background-color:#ffa800;
  transform: scaleX(-1) rotate(-35deg);
  color:#000;
  font-size:18px;
  text-align:center;
  line-height:40px;
  font-weight:bold;
  text-transform:uppercase;
  font-family:Arial;
}
```

The trick is use the transform: rotate + scale and set the font-size from 0 to any value when the input is checked.

You could see the example working, [right here](https://codepen.io/haykou/pen/yEwvXR).