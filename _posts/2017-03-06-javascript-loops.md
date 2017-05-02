---
layout: post
title: "Understanding Javascript Loops: For, While, and Do-While"
date: 2017-03-06
---

<p>Loops are a very efficient method in Javascript for running a command over and over on a set of data.
  But there are a few different types of loops, and when you're new to Javascript it can be difficult to
  keep them straight. In this article, we'll be taking an in-depth look at three different Javascript
  loops: the <strong>for loop</strong>, the <strong>while loop</strong>, and the <strong>do while loop</strong>.</p>

<h2>Data Set and Our Problem</h2>

<p>To show how loops can help us solve problems efficiently in Javascript, let's say that an elementary school
teacher has asked us to help her create a seating chart for her students. Miss Alice has 26 students, and she
wants a random seating chart for her classroom.</p>

<p>Let's create an array of her students:</p>

```javascript
var students = ["Ava", "Barry", "Charlie", "David", "Elizabeth", "Frank", "Grant", "Holly", "Ian",
"Jimmy", "Keri", "Lucy", "Mindy", "Nancy", "Ophelia", "Peter", "Quentin", "Russell", "Sally", "Theresa", "Umberto", "Veronica", "Walter", "Xavier", "Yvette", "Zeke"];
```

<h2>Starting Off Easy With The For Loop</h2>

<p>Now that we have the students in a data set that we can use, let's start off easy by printing out
a list of Miss Alice's students for her. We'll do it using a for loop.</p>

```javascript
for (var i = 0; i < students.length; i ++){
  console.log(students[i]);
}
```

<p>If we were to run this code, we would get the following list:</p>

```
  Ava
  Barry
  Charlie
  David
  Elizabeth
  Frank
  Grant
  Holly
  Ian
  Jimmy
  Keri
  Lucy
  Mindy
  Nancy
  Ophelia
  Peter
  Quentin
  Russell
  Sally
  Theresa
  Umberto
  Veronica
  Walter
  Xavier
  Yvette
  Zeke
  ```

<p>Let's break down what happened with the for loop. The first part of the loop for (var i = 0;) begins the loop, creates a variable named i and
  sets it equal to 0. It's common to use i as your variable and set it equal to 0, but it's important to know that you can choose any name for your variable and set it equal to any number (as we'll soon see!).</p>

<p>All that i is doing here is acting as a counter. The second part of the loop i < students.length; i ++ tells the for loop how long to run. i ++
  means "add 1 to i each time you loop", and i < students.length means run as long as i is less than the length of the students array.</p>

<p>The first time the for loop runs, the loop creates the variable i, sets it equal to 0, checks to make sure it satisfies the second part of the statement i < students.length, adds 1 to i, and then finally executes the code in your loop. (In this example, that's the console.log statement.) It continues that pattern until i does not satisfy the criteria in the second part the statement, at which point the loop stops.</p>


<h2>Now, About That Seating Chart</h2>

<p>So far all we've done for Miss Alice is print out a list of her students. Which, presumably, she already had. So let's get to work on the random seating chart.</p>

<p>Here's some code, that based on what we've learned so far, should make a random seating chart:</p>


```javascript
var students = ["Ava", "Barry", "Charlie", "David", "Elizabeth", "Frank", "Grant", "Holly", "Ian",
"Jimmy", "Keri", "Lucy", "Mindy", "Nancy", "Ophelia", "Peter", "Quentin", "Russell", "Sally", "Theresa", "Umberto", "Veronica", "Walter", "Xavier", "Yvette", "Zeke"];

var seatingChart = [];

for (var i = 0; i < students.length; i++) {
  var random = Math.floor(Math.random() * students.length);
  seatingChart.push(students.splice(random, 1));
  }

console.log(seatingChart);
  ```

<p>What I've done in this code is create a new, empty array called seatingChart
  that will eventually hold our random list. Then, in the for loop, I have a variable random
  which is going to be assigned a random number between 0 and the current length of the students array. (Because random
  is inside the for loop, it will be assigned a new random value each time the loop runs.)</p>

<p>Next I'm going to find the student at the random position in the students array,
remove it from students and add it to seatingChart.
(If you aren't familiar with Math.floor(), Math.random(),
.push(), or .splice(), that's ok. It's enough for now
to know what the for loop is supposed to do.)</p>

<p>When we run this code, we should get a list of all 26 students in a random order. But what we actually get is something like this: </p>

```javascript
[ 'Peter',
  'David',
  'Nancy',
  'Walter',
  'Yvette',
  'Elizabeth',
  'Zeke',
  'Russell',
  'Grant',
  'Sally',
  'Barry',
  'Lucy',
  'Ophelia' ]
  ```

<p>That's only 13 students. What happened?</p>

<p>The problem lies in how we defined our for loop. We set it to run as long as i < students.length,
  and at the same time, we're removing the student's name from students (so that they don't get
  assigned to the seatingChart twice). So i is counting up
  at the same time that students.length is getting smaller. Eventually,
they meet in the middle, at 13, and the for loop stops.</p>

<p>So, how can we solve this problem and get Miss Alice her seating chart? There are a couple of solutions.</p>

<p>The first thing that we could do is simply create the for loop like this:</p>

```javascript
for (var i = 0; i < 26; i++) {
  var random = Math.floor(Math.random() * students.length);
  seatingChart.push(students.splice(random, 1));
}
```

<p>Using i < 26 ensures that our loop will run the correct number of times and assign every student to the seatingChart. However, that's not a very elegant solution. What if we didn't know the exact number of students in the class? A better option would be this:</p>

```javascript
for (var i = students.length; i > 0; i--) {
  &nbsp&nbsp var random = Math.floor(Math.random() * students.length);
  &nbsp&nbsp seatingChart.push(students.splice(random, 1));
}
```

<p>Here we are assigning i the value of students.length,
  then subtracting 1 each loop, and telling it to run as long as i > 0. Using this
  solution ensures that the loop will select every student from the original array no matter how many students there are.</p>

<h2>Using A While Loop</h2>

<p>That last solution we discussed is actually very similar to the while loop. Here's how the code would look in a while loop:</p>

```javascript
var students = ["Ava", "Barry", "Charlie", "David", "Elizabeth", "Frank", "Grant", "Holly", "Ian",
"Jimmy", "Keri", "Lucy", "Mindy", "Nancy", "Ophelia", "Peter", "Quentin", "Russell", "Sally", "Theresa", "Umberto", "Veronica", "Walter", "Xavier", "Yvette", "Zeke"];<br><br>

var i = students.length;
while (i > 0) {<br>
  var random = Math.floor(Math.random() * students.length);
    seatingChart.push(students.splice(random, 1)[0]);
    i --;
}
```

<p>The syntax of a while loop is a little bit different, but you can still see what's happening.
  We're setting i = students.length (outside of the loop this time), and
  then removing a student randomly from the array. Be sure to put in the line of code that increments
  or decrements i, or else your loop will run forever! (and crash your browser.)</p>

<p>A while loop runs as long as the statement in the parentheses is true. We set i = students.length
  and then decrement it by one each loop, so the loop will run as long as i > 0. Once i
  hits 0, the loop stops.</p>

<p>In case you're curious, if the statement in the while loop is false, the loop will never run.</p>

<h2>Finally, A Random Seating Chart</h2>

<p>At long last, we have a random seating chart for Miss Alice. We can do it using either the while loop or the last for loop solution that we talked about. If you'd like to play around with these loops and data, here's a JSBin.</p>

<a class="jsbin-embed" href="http://jsbin.com/savamixoqa/embed?js,console,output">JS Bin on jsbin.com</a><script src="http://static.jsbin.com/js/embed.min.js?3.41.5"></script>


<h2>What About The Do-While Loop?</h2>

<p>We don't need to use a do-while loop to make the seating chart, but here's an example of one
  for the sake of completeness. A do-while loop is very similar to a while loop, but it guarantees
  that your code will run at least one time.</p>

```
var i = 0;

do {
  console.log(i);
  i++;
  }
while (i < 10);
```

<p>This will log i to the console 10 times, but if we changed the code
  to say while (i > 10); thus making it a false statement, the code would still run one time.</p>
