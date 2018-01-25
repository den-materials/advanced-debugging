# Debugging Techniques

## Why is this important?
How many of us have written code that doesn't quite work the way we hope or want it to? Psssst, everyone does all day every day. The hardest and most time consuming part of our job is trying to figure out why code doesn't work the way we want it to. The better you are at debugging, the better you are at your job, the more you get paid :-)

## Lesson Objectives

*By the end of this lesson, you will be able to:*

- open up the Node Inspector tool
- explore the files in your node project within the Inspector tool
- run your application and pause the execution at a breakpoint
- explain the difference between regular dev tools and node inspector
- explore the data in your code while your application is paused
- navigate through your application step by step
- explain how data is passed into an EJS file to construct HTML

## Open Node Inspector

Clone the candies app again, [here's the repo](https://github.com/den-materials/express-views-lesson.git), then checkout the `solution` branch. *Make sure you change into the solution code directory!* Try running your app to make sure it works right out of the box.

### Fire up Node Inspector
[Here's](https://medium.com/@paul_irish/debugging-node-js-nightlies-with-chrome-devtools-7c4a1b95ae27) a good guide to using Node Inspector, I'm sure there's others. 

Kill your node server. Make sure you're using at least Node 6.3. Run a `node -v` to find out. Now run:

```
node --inspect --inspect-brk app.js
```

Wait for it to fire up, then open two tabs in Chrome: `localhost:3000/candies` and `about:inspect`.  You should see the app in localhost, and in the other, click "Open dedicated DevTools for Node". You should see something similar to the regular Chrome Dev Tools. Make sure you're in the "Sources" tab, click "file://" and expand those directories to see the files relevant to your Node server.

<!-- Pass to devs -->
