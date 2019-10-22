---
title: How to create a pure CSS Off-Canvas Menu
date: 2019-01-02
published: true
tags: ['Quick Tips']
canonical_url: false
description: "Today I’m gonna show my way to create an easy off-canvas menu without any javascript, it uses (again), a checkbox, labels and some CSS stuff..."
cover_image: ./images/quick-tips-3-fix.gif
---

Today I’m gonna show my way to create an easy off-canvas menu without any javascript, it uses (again), a checkbox, labels and some CSS stuff.

## Step 1 - HTML

We will create this structure:

```html
<label for="chkMenu" class="menu__button"></label>
<input type="checkbox" id="chkMenu">
<label for="chkMenu" class="menu__helper"></label>
<nav class="nav__menu">
  <ul>
    <li>Home</li>
    <li>About Us</li>
    <li>Contact</li>
    <li>Support Me</li>
  </ul>
</nav>
```

The first label <strong>"menu button"</strong> it’s the normal button for the user open the menu, the <strong>chkMenu</strong> like I’ve done in other posts, I use it to combine with <strong>:checked</strong> selector so we can show/hide the navigation menu and that <strong>"menu helper"</strong> it’s a "trick" to easily close the navigation menu when user clicks outside, the menu closes.

## Step 2 - Where the magic happens

Let’s add some CSS:

```css
body{
  background-color:#cecece;
}
.menu__button{
  position: fixed;
    z-index: 1000;
    margin: 1em;
    padding: 0;
    width: 2.5em;
    height: 2.25em;
    border: none;
    text-indent: 2.5em;
    font-size: 1.5em;
    color: transparent;
    background: transparent;
}
.menu__button:before{
  position: absolute;
    top: 0.5em;
    right: 0.5em;
    bottom: 0.5em;
    left: 0.5em;
    background: linear-gradient(#373a47 20%, transparent 20%, transparent 40%, #373a47 40%, #373a47 60%, transparent 60%, transparent 80%, #373a47 80%);
    content: '';
}
#chkMenu{
  display:none;
}
#chkMenu:checked ~ .nav__menu{
  display:block;
  left:0;
}
#chkMenu:checked ~ .menu__helper{
  display:block;
}
.nav__menu{
  position:fixed;
  left:-300px;
  top:0;
  width:300px;
  height:100%;
  background:#2c3e50;
  transition:all 0.5s ease;
  z-index:1002;
  padding-top:20px;
}
ul{
  list-style:none;
}
ul li{
  margin-bottom:10px;
  color:#fff;
  font-size:20px;
}
.menu__helper{
  z-index:1001;
  position:fixed;
  top:0;
  left:0;
  height:100%;
  width:100%;
  display:none;
}
```

Basically we are working with z-index and the :checked selector, the navigation menu it’s hidden with <strong>left:-300px</strong>, so when user click in the button, it activate the checkbox and we combine it with the menu and the <strong>menu helper</strong>, applying <strong>left:0</strong> so the menu will open :)

The <strong>menu helper</strong> works the same way of the <strong>menu button</strong>, so if the menu is on state "opened" and the user clicks on <strong>menu helper</strong>, it will toggle off the checkbox and close our navigation menu. Don’t forget to use the z-index inside <strong>menu helper</strong>lower than the <strong>navigation menu</strong> because it needs to be under the nav menu.

The trick here it’s combine <strong>CSS selectors</strong>, <strong>positions</strong> and <strong>z-index</strong>.

You could see the example working, [right here](https://codepen.io/haykou/pen/mjbYrj).