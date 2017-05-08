---
layout: post
title: "An Introduction To Angular Directives"
date: 2017-03-22
---

<p>One of the most confusing parts of learning Angular is the seemingly-huge number of new terms and concepts that you have to learn and use. Chances are good that you've never dealt with controllers, directives, or factories before, and suddenly they're essential to your app working correctly. In the next few articles on this blog, we're going to be discussing some basic concepts in Angular, and this article is on directives.</p>

<p>The easiest way to think about directives is that they allow you to extend your HTML and add some increased functionality. In fact, directives are generally attached directly to your HTML elements. (See what I did there? "directly"? Bada bing!)</p>

<p>An easy example of a directive is when you bootstrap, or start, your Angular application. Your index.html file might start out like this:</p>

```
<!DOCTYPE html>
<html ng-app="myApp">
```

<p>ng-app is a directive which tells Angular to wake up and pay attention because you're using it to build an application.</p>

<p>In addition to ng-app, there are several other directives that you'll use on a regular basis. Some examples:</p>

<table>
  <tr><th>Directive</th><th>Description</th></tr>
  <tr><td>ng-model</td><td>Allows you to bind data in your HTML. Useful for getting values from inputs.</td></tr>
  <tr><td>ng-repeat</td><td>Creates a loop that sends data to the view. Useful for lists and tables</td></tr>
  <tr><td>ng-class</td><td>Allows you to assign a class to some HTML. Similar to JQuery's addClass()</td></tr>
  </table>

<h2>Custom Directives</h2>

<p>In addition to using the built-in directives available in Angular, you can also create your own custom directives. Here's a quick example:</p>

```
var app = angular.module("myCoolApp", []);
app.directive("myAwesomeDirective", function() {
  return {
    template: < h1>This headline was brought to you by a directive!</h1>
  };<br>
});
```

<p>Then, in your HTML, you can call this directive by creating an element with the same name: < my-awesome-directive>< /my-awesome-directive>.</p>
