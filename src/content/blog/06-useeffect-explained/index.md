---
title: "useEffect in React — Explained Like You're 5!"
description: "A simple guide to understanding React's useEffect hook with practical examples."
date: "2024-03-23"
tags:
  - react
  - tutorial
---

When you're learning React, you'll hear a lot about something called useEffect. And at first, it sounds scary.

But don't worry — we're going to explain it so simply, even your pet goldfish could understand it. 🐠

Let's go!

## 🔄 What is useEffect?

Imagine you're building a robot. Every time the robot sees something change, it does a job.

That robot is useEffect.

In React, useEffect lets you run side effects — things that happen outside the normal UI rendering, like:

- Fetching data from an API
- Setting up event listeners
- Updating the browser title
- Saving to localStorage
- Starting or stopping a timer

React's main job is to draw stuff on the screen. But what if you want to do something after it draws? That's where useEffect steps in.

## 🧪 Syntax — The Simple Version

```js
useEffect(() => {
  // do something here
}, [dependencies]);
```

- 🧠 The first part (() => {}) is a function — your robot's job.
- 📦 The second part ([dependencies]) is a list of things to watch.

When one of the things in the list changes, the robot wakes up and runs the function.

## 🚀 Example 1: Run Code on First Load

Let's say you want to show a message when your component loads.

```js
import React, { useEffect } from "react";

function Hello() {
  useEffect(() => {
    console.log("Hello! The component has loaded.");
  }, []);

  return <h1>Hello, world!</h1>;
}
```

The empty array [] means: "Only run this one time when I load."

## 🔄 Example 2: Watch a Value and React to Changes

```js
import React, { useState, useEffect } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log(`The count is now ${count}`);
  }, [count]); // 👀 watch count

  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increase</button>
    </div>
  );
}
```

## 🧹 Example 3: Clean Up After Yourself

```js
useEffect(() => {
  const interval = setInterval(() => {
    console.log("Tick");
  }, 1000);

  return () => {
    clearInterval(interval);
    console.log("Cleaned up!");
  };
}, []);
```

## ⚙️ Real-World Example: Fetching Data

```js
import React, { useState, useEffect } from "react";

function User() {
  const [user, setUser] = useState(null);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users/1")
      .then((res) => res.json())
      .then((data) => setUser(data));
  }, []);

  return user ? <h1>{user.name}</h1> : <p>Loading...</p>;
}
```

## 🧾 Summary: When to Use useEffect

| You want to... | useEffect is for you? |
|----------------|----------------------|
| Fetch data from an API | ✅ Yes |
| Update the page title | ✅ Yes |
| Listen to scroll or resize events | ✅ Yes |
| Clean up timers or subscriptions | ✅ Yes |
| Do something after every render | ✅ Yes (with no array) |
| Just render UI with no side effects | ❌ Not needed |

## 🧠 Pro Tips

- Forget the fancy words like "side effects" — just think of it as "do something after render."
- Always include a dependency array to avoid running too much or causing infinite loops.
- Cleanup functions help avoid memory leaks in big apps.

## 🎁 Bonus Analogy: The Pizza Delivery Robot

Imagine a robot that:
- Watches if your hunger level (state) changes
- If you're hungry, it orders a pizza
- When you're full, it stops ordering pizza

That's exactly what useEffect does with your variables and side jobs.

## 💬 Final Thoughts

useEffect is one of the most powerful (and most confusing) tools in React. But once you understand the simple idea — do something when things change — it becomes a superpower. 💪

You're no longer just building UI — you're building smart apps that can think, react, and clean up after themselves.