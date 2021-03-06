---
layout: post
title: JavaScript Promise
author: kamal
tags: javascript
---

Update 1: Thanks to [fadzlan](https://github.com/fadzlan) for [fixing](https://github.com/devkini/devkini.github.io/pull/1) the second example.

This is an answer to a question in FB group:-

>Confuse with callback and promises. In $.ajax, the success callback is async by default, why do we need to use promise? Can someone good in JS explain?

Promise let you program in async while maintaining the synchronize structure of your code. Take this code:-

<!--more-->

```javascript
var res;
db_connect(host, function(conn) {
  res = conn.query("SELECT * FROM ...");
});
console.log(res); // probably still null
```

Using promise:-

```javascript
var res;
db.connect(host).then(function(conn) {
  res = conn.query("select * from ...");
  return res;
}).then(function(res){
  console.log(res); // already available
});
```

The first code is a common mistake to someone new in async programming because while the code is async, the structure is not, you assume it to run from top to bottom. Using promise, the program definitely run from top to bottom as you read it.

> But promises like a callback? that `then()` is a callback of `db.connect`, but why promises is not a callback? What's the difference ?

Ok, let rephrase it. Promise is a different (or maybe better) way of using callback. So doesn't mean that when you use promise, you're not using callback anymore. You can't remove callback since it's the core of the language, that's how javascript work. But you can use it in different way.

For more in-depth write up on promise, I'd suggest to read [this article][1] (a very long one, /me haven't finished it yet ;))

[1]:http://robotlolita.me/2015/11/15/how-do-promises-work.html
