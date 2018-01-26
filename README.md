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

## Node Inspector

Clone the candies app again, [here's the repo](https://github.com/den-materials/express-views-lesson.git), then checkout the `debugging` branch. *Make sure you change into the solution code directory!* Run the seed file and then try running your app to make sure it works right out of the box. The homepage is actually `localhost:3000/candies`.

### Fire up Node Inspector
[Here's](https://medium.com/@paul_irish/debugging-node-js-nightlies-with-chrome-devtools-7c4a1b95ae27) a good guide to using Node Inspector, I'm sure there's others. 

Kill your node server. Make sure you're using at least Node 6.3. Run a `node -v` to find out. Now run:

```
node --inspect --inspect-brk app.js
```

Wait for it to fire up, then open two tabs in Chrome: `localhost:3000/candies` and `about:inspect`.  You should see the app in localhost, and in the other, click "Open dedicated DevTools for Node". You should see something similar to the regular Chrome Dev Tools. Make sure you're in the "Sources" tab, click "file://" and expand those directories to see the files relevant to your Node server.

#### *Note* 

Documentation claims you can just run this:

```
node --inspect app.js
```

But, I experienced a little finickyness with Node Inspector loading all the files in my project properly. Adding the `--inspect-brk` pauses execution on the first line of the project, and I've had more success getting all the files in my project properly using this.

<!-- Pass to devs -->

## Breakpoints
Let's find a piece of code to run. How about the Get All Candies functionality? Let's find the code that executes that functionality...

Let's set a breakpoint on the first line of the `getAll` function. Click the line number of the first line, and you should see the blue breakpoint symbol. Also, note there's a list of all your breakpoints in the right pane. You can even toggle them on and off. Now that is power.

I want to test this code out. How do I do that? What do I expect to see? I can just hit that route in the browser window to test that functionality out.

When I try loading that page, it pauses execution at that breakpoint. Now I can:

1. Hover over variables to see what they equal
2. Explore variables and other codes in the console
3. Add a variable to the watch panel
4. Continue the code execution step by step, until the next breakpoint, step into functions, you name it.

Now, put a breakpoint inside the database query callback. Look at the arguments that Mongoose has returned to you. That's nice, isn't it? Lastly, throw a breakpoint right where the view file is loaded. You can literally see the data that's passed into the EJS file.

A couple more notes:
* setting breakpoints in different routes will not catch until you hit that route
* code in the app.js will only run at the very beginning when you launch node
* use breakpoints to get a deeper unders

### DIY
The seed file put in a company name for our seed data. Use the inspector tool to explore this functionality and add a company field to the `layout.ejs` file. 

<!-- pass over to devs to experiment for a second -->
tanding, or any understanding, of what order the lines of your code are executing in

<!-- hand off to devs -->

## Compare to Mongo CLI
As a pro debugger, you gotta keep all your resources in mind. It's like being your favorite detective.

![angela](http://static.tvtome.com/images/genie_images/news_hub/uploaded/thekaitlingnews138265621470/Angela.png)

When you click a candy name and edit it in the user interface, you *should* be able to verify it's stored correctly in at least two ways:

1. connect directly to your DB via the Mongo CLI
2. throw a breakpoint in the callback in your Node-Code
3. look really carefully at your DB with a magnifying glass

### DIY
Try clicking a candy name and editing it's name and color. Verify that the data is saved correctly to your database by using breakpoints and the node inspector, as well as using the Mongo CLI. Where can you find the candy ID? Do you see the same document ID in both Node Inspector and Mongo CLI? How are you DB queries different between the two?

Keep this in mind:
1. What do you expect to see?
2. What do you see? In Node Inspector? In Mongo CLI?

## Node Inspector vs the regular Dev Tools
You can open up Node Inspector and Chrome dev tools at the same time, and they'll show different things. Why?? 

### DIY
We have a bug to fix! BTW if you don't know who [Grace Hopper](https://www.youtube.com/watch?v=S6sh8CxwWx8) is, you should change that.

Try adding a new candy on the main index page (`/candies`). Doesn't work does it? Use Chrome dev tools and Node Inspector to figure out why the new candy is not saving properly. *Hint: You should see a file called `main.js` in your dev tools window.*

## Fancy Breakpoints
* Conditional breakpoints
* Black box scripts

## Resources
[Documentation](https://nodejs.org/en/docs/inspector/)

[Paul Irish's How To](https://medium.com/@paul_irish/debugging-node-js-nightlies-with-chrome-devtools-7c4a1b95ae27)









