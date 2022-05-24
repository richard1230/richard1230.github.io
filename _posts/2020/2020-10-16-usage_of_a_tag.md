---
title: Usage of 'a' Tag
date: 16-10-2020
categories: 
- HTML and CSS
tags:
- front end
---

### 1. href

#### (1) Linking to relative URLs
```html
<a href= "//google.com">Go To Google</a>
```
	Q: Why use '//google.com' instead of 'https://www.google.com' and 'http://www.google.com?'
    A: Because '//' can automatically recognize if the website using the 'https' or 'http' protocol.

#### (2) Jump to one point of the same html page
```html
  <p>1</p>
  <p>2</p>
  <p>3</p>
  <p>4</p>
  <p>5</p>
  <p id="xxx">6</p>
  <p>7</p>
  <p>8</p>
  <p>9</p>
  <a href= "#xxx">Go To 6</a>
```
	You can locate one point in the same html page by using a id tag in the href.

#### (3) Linking to  email or telephone
```html
<a href="mailto:librayuyue@163.com">Send Email to Me</a>
<a href="tel:2032123212" target="_self">Send Message to Me</a>
```

### 2. target
	(1) "_self" is a default value of target, it will open the new page based on current page.
    (2) "_blank" usually a ne tab
    (3) "_parent" the parent browsing context of the current one. If no parent, behaves as _self.
    (4) "_top" the topmost browsing context(the "highest" context that's an ancestor of the current one.) if no ancestors, behaves as _self.

### 3. download
	MDN Quote: "Prompts the user to save the linekd URL instead of nabigating to it. Can be used with or without a value."


### 4. rel = noopener
	Not important



## The Usage of 'img' Tag
```html
  <img id=xxx src="dog.png" alt="one dog">
```
	(1) The 'src' attribute is required. It contains the path to the image you want to embed.
    (2) 'alt' attribute holds a text description of the image. When the image failed to load, the alt text will be displayed.
    (3) 'max-width: 100%;' it sets the maximum width of an element. It prevents the used value of the width property from becoming larger than the value specified by max-width.


## The Usage of 'table' Tag
```html
<table>
    <thead>
      <tr>
        <th>English</th>
        <th>Translate</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Hyper</td>
        <td>超级</td>
      </tr>
      <tr>
        <td>Target</td>
        <td>目标</td>
      </tr>
      <tr>
        <td>Reference</td>
        <td>引用 </td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <td>空</td>
        <td>空</td>
      </tr>
    </tfoot>
  </table>
```
	'table' contains 'thead', 'tbody' and 'tfoot'. These three tags can change the order but the browser will consistently display them in the default order.

## Other Thoughts
### *The Use of javascript:; （pseudo code）*
```html
 <p><a href="javascript: alert(1);">javascript pseudo protocols.</a></p>
 <p><a href="javascript:;">click</a></p>
```
	When click the second link, the page will not refreshed and there is no new record in the network tab. But the click effect is still work.

### *The difference between 'input' and 'button'*
	you can not put any other thing inside the input tag, while you can put something like 'strong','em' or even 'img' tag inside a button tag.







