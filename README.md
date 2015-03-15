#Front-end Job Interview Questions

This file contains a number of front-end interview questions that can be used when vetting potential candidates. It is by no means recommended to use every single question here on the same candidate (that would take hours). Choosing a few items from this list should help you vet the intended skills you require.

**Note:** Keep in mind that many of these questions are open-ended and could lead to interesting discussions that tell you more about the person's capabilities than a straight answer would.

## Table of Contents

  1. [General Questions](#general-questions)
  1. [HTML Questions](#html-questions)
  1. [CSS Questions](#css-questions)
  1. [JS Questions](#js-questions)
  1. [Network Questions](#network-questions)
  1. [Coding Questions](#coding-questions)
  1. [Fun Questions](#fun-questions)

## Getting Involved

  1. [Contributors](#contributors)
  1. [How to Contribute](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/CONTRIBUTING.md)
  1. [License](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/LICENSE.md)

#### General Questions:

* What did you learn yesterday/this week?
* What excites or interests you about coding?
* What is a recent technical challenge you experienced and how did you solve it?
* What UI, Security, Performance, SEO, Maintainability or Technology considerations do you make while building a web application or site?
* Talk about your preferred development environment.
* Which version control systems are you familiar with?
* Can you describe your workflow when you create a web page?
* If you have 5 different stylesheets, how would you best integrate them into the site?
* Can you describe the difference between progressive enhancement and graceful degradation?
* How would you optimize a website's assets/resources?
* How many resources will a browser download from a given domain at a time?
  * What are the exceptions?
* Name 3 ways to decrease page load (perceived or actual load time).
* If you jumped on a project and they used tabs and you used spaces, what would you do?
* Describe how you would create a simple slideshow page.
* What tools do you use to test your code's performance?
* If you could master one technology this year, what would it be?
* Explain the importance of standards and standards bodies.
* What is Flash of Unstyled Content? How do you avoid FOUC?
* Explain what ARIA and screenreaders are, and how to make a website accessible.
* Explain some of the pros and cons for CSS animations versus JavaScript animations.

#### HTML Questions:

* What does a `doctype` do?
* What's the difference between standards mode and quirks mode?
* What's the difference between HTML and XHTML?
* Are there any problems with serving pages as `application/xhtml+xml`?
* How do you serve a page with content in multiple languages?
* What kind of things must you be wary of when design or developing for multilingual sites?
* What are `data-` attributes good for?
* Consider HTML5 as an open web platform. What are the building blocks of HTML5?
* Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.
* Describe the difference between `<script>`, `<script async>` and `<script defer>`.
* Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?

#### CSS Questions:

* What is the difference between classes and ID's in CSS?

  `id 用#, class用. id是unique的class可以用在多个元素上面.`
* What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?

  每个浏览器有它自己的默认user agent style（比如link是蓝色的还带个下划线，table有一定的border和padding)。reset.css强制抹去所有的浏览器的默认style，以此来避免出现跨浏览器的错误。nomalize.css更加注重的是一个consistent，保留了一部分默认的东西，而不是一刀切。并且它还另外修改了一些浏览器的bug（html5里面的display setting）。normalize不会对调试工具起作用，更加模块化，normalize有documentation。最好的例子就是h1-h tag了，在normalize里面就是粗体。
  choose：如果是迅速的prototyping或者是testing，非html5的一个page，使用reset。否则使用normalize。
  
* Describe Floats and how they work.

  float:left/right/none/inherit
  float的元素不给它container加高度。
  如果不给clear float的话，container的height总是不会增加的。
  overflow：hidden；也可以用来清除浮动，这属性要用在container上面。
  clear: both要更加好一些。
  最开始float是用来flow the text around img，当给一个inline或者是block的元素加上float属性的时候，float会使得它像一个inline-block.

* Describe z-index and how stacking context is formed.

  z-index 仅在节点的 position 是 relative|absolute|fixed 才会起作用。
  z-index是用来控制vertical stacking order of elements that overlap. 
  比较好的用法就是 100，200，300 这样在他们之间也可以插入元素。

* What are the various clearing techniques and which is appropriate for what context?

  1.
  ```javascript
  empty div <div style=”clear:both”></div>
  ```
  2.overflow method
  3.使用:after伪元素！
  ```javascript
  .clearfix:after {
    content: “.”;
    visibility:hidden;
    display: block;
    height: 0;
    clear: both;
  }
  ```

* Explain CSS sprites, and how you would implement them on a page or site.

  css sprites 是用来减少http request的一个方法，对img resource的一个优化提高加载速度。
  方法是把各种image合并成为一个大的 按照x，y coordinates来使用。
  css-background-image 在定位的时候切换显示不同的小区块。

* What are your favourite image replacement techniques and which do you use when?
* How would you approach fixing browser-specific styling issues?

  css hacks, browser specific hacks.当然有时候呢一个近似准确的也可以达到。

* How do you serve your pages for feature-constrained browsers?
  * What techniques/processes do you use?

  progressive enhancement，graceful degradation.
  去caniuse.com看这个功能在哪些浏览器里面是支持的
  有些浏览器要加vendor prefix

* What are the different ways to visually hide content (and make it available only for screen readers)?

  1.
  ```javascript
  visibility: hidden; and/or display:none;
  ```
  这货一出，所有人都看不到了，所以不能使用

  2. `text-indent： -10000px；`这以使用，但是当元素是要跳转或者navigation的时候会有些bug 不好用

  3. css clip 普通观众 这个1px装不下所以就隐藏了，但是screen reader能够获取到。
  ```javascript
  position: absolute !important;
  clip: rect(1px 1px 1px 1px); /* IE6, IE7 */
  clip: rect(1px, 1px, 1px, 1px);
  ```
  4. Absolutely positioning content off-screen 这个好用
  ```javascript
    .hidden{
      position:absolute;
      left:-10000px;
      top:auto;
      width:1px;
      height:1px;
      overflow:hidden;
    }
  ```
* Have you ever used a grid system, and if so, what do you prefer?
* Have you used or implemented media queries or mobile specific layouts/CSS?
* Any familiarity with styling SVG?
* How do you optimize your webpages for print?
* What are some of the "gotchas" for writing efficient CSS?
* What are the advantages/disadvantages of using CSS preprocessors?
  * Describe what you like and dislike about the CSS preprocessors you have used.
* How would you implement a web design comp that uses non-standard fonts?
* Explain how a browser determines what elements match a CSS selector.
* Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.
* What does ```* { box-sizing: border-box; }``` do? What are its advantages?
* List as many values for the display property that you can remember.
* What's the difference between inline and inline-block?
* What's the difference between a relative, fixed, absolute and statically positioned element?
* The 'C' in CSS stands for Cascading.  How is priority determined in assigning styles (a few examples)?  How can you use this system to your advantage?
* What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
* Have you played around with the new CSS Flexbox or Grid specs?
* How is responsive design different from adaptive design?
* Have you ever worked with retina graphics? If so, when and what techniques did you use?
* Is there any reason you'd want to use `translate()` instead of *absolute positioning*, or vice-versa? And why?

#### JS Questions:

* Explain event delegation
* Explain how `this` works in JavaScript
* Explain how prototypal inheritance works
* How do you go about testing your JavaScript?
* What do you think of AMD vs CommonJS?
* Explain why the following doesn't work as an IIFE: `function foo(){ }();`.
  * What needs to be changed to properly make it an IIFE?
* What's the difference between a variable that is: `null`, `undefined` or `undeclared`?
  * How would you go about checking for any of these states?
* What is a closure, and how/why would you use one?
* What's a typical use case for anonymous functions?
* How do you organize your code? (module pattern, classical inheritance?)
* What's the difference between host objects and native objects?
* Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
* What's the difference between `.call` and `.apply`?
* Explain `Function.prototype.bind`.
* When would you use `document.write()`?
* What's the difference between feature detection, feature inference, and using the UA string?
* Explain AJAX in as much detail as possible.
* Explain how JSONP works (and how it's not really AJAX).
* Have you ever used JavaScript templating?
  * If so, what libraries have you used?
* Explain "hoisting".
* Describe event bubbling.
* What's the difference between an "attribute" and a "property"?
* Why is extending built in JavaScript objects not a good idea?
* Difference between document load event and document ready event?
* What is the difference between `==` and `===`?
* Explain the same-origin policy with regards to JavaScript.
* Make this work:
```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```
* Why is it called a Ternary expression, what does the word "Ternary" indicate?
* What is `"use strict";`? what are the advantages and disadvantages to using it?
* Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, `"buzz"` at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`
* Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?
* Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?
* Explain what a single page app is and how to make one SEO-friendly.
* What is the extent of your experience with Promises and/or their polyfills?

#### Network Questions:

* Traditionally, why has it been better to serve site assets from multiple domains?
* Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.
* What are the differences between Long-Polling, Websockets and Server-Sent Events?
* Explain the following request and response headers:
  * Diff. between Expires, Date, Age and If-Modified-...
  * Do Not Track
  * Cache-Control
  * Transfer-Encoding
  * ETag
  * X-Frame-Options
* Can you explain the difference between `GET` and `POST`?
* Can you explain the difference between `GET` and `HEAD`?

#### Coding Questions:

*Question: What is the value of `foo`?*
```javascript
var foo = 10 + '20';
```

*Question: How would you make this work?*
```javascript
add(2, 5); // 7
add(2)(5); // 7
```
Answer:
```javascript
//add(2,5)
function add(a,b){
  return a+b;
}
//add(2)(5)
function add(a){
  return function(b){
    return a+b;
  }
} 
```

*Question: What value is returned from the following statement?*
```javascript
"i'm a lasagna hog".split("").reverse().join("");
```

*Question: What is the value of `window.foo`?*
```javascript
( window.foo || ( window.foo = "bar" ) );
```

*Question: What is the outcome of the two alerts below?*
```javascript
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```

*Question: What is the value of `foo.length`?*
```javascript
var foo = [];
foo.push(1);
foo.push(2);
```

#### Fun Questions:

* What's a cool project that you've recently worked on?
* What are some things you like about the developer tools you use?
* Do you have any pet projects? What kind?
* What's your favorite feature of Internet Explorer?
* How do you like your coffee?


#### Contributors:

This document started in 2009 as a collaboration of [@paul_irish](http://twitter.com/paul_irish) [@bentruyman](http://twitter.com/bentruyman) [@cowboy](http://twitter.com/cowboy) [@ajpiano](http://twitter.com/ajpiano)  [@SlexAxton](http://twitter.com/slexaxton) [@boazsender](http://twitter.com/boazsender) [@miketaylr](http://twitter.com/miketaylr) [@vladikoff](http://twitter.com/vladikoff) [@gf3](http://twitter.com/gf3) [@jon_neal](http://twitter.com/jon_neal) [@sambreed](http://twitter.com/sambreed) and [@iansym](http://twitter.com/iansym).

It has since received contributions from [100 developers](https://github.com/h5bp/Front-end-Developer-Interview-Questions/graphs/contributors).
