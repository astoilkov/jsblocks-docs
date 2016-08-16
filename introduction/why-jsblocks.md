# Why use jsblocks?

<br />

## MV-ish

Model-View-Controller, Model-View-Collection, Model-View-ViewModel, Model-View-Whatever, Hierarchical Model-View-Controller or nothing at all - jsblocks has you covered.
A Model-View-Collection layer stands on top of the main DOM syncing core. This MVC layer is extremely powerful and enables easy creation of complex applications.
The MVC layer is also modular, so you could remove it if you don't need the extra functionality, making your code base lighter.

## Debugging experience

The debugging experience is a major factor that is often overlooked.
It brings an easier learning curve and faster development cycles.
This is why jsblocks concentrates a lot of effort in building a great debugging experience.
Let's take a look at an example of what jsblocks offers.

![debugging experience](/img/debugging.gif)

## Server-side rendering

Client-side frameworks suffer major drawbacks like:
 * Lack of SEO optimization because content is rendered on the client and search engines do not execute JavaScript
 * Slow performance because entire app logic is executed and rendered on the user machine on every page load
 * Laggy experience represented by the content changing between the page first loads and the time DOM is ready

There is a way to address all this issues by executing the entire client-side logic on the server.
This approach enables the content to be sent fully rendered from the server eliminating mentioned problems.
Also, jsblocks makes performance improvements so performance will no longer heavily depend on the user machine.

And it's super easy to setup:

```javascript
var blocks = require('blocks');
var server = blocks.server();
```

For detailed documentation on server-side rendering you could head up [here](../introduction/server-side-rendering.md).

## Fast

Performance is important. For a framework that manages your whole site, it's even more important.
And for data-heavy operations, it is absolutely essential. This is why jsblocks has an architecture designed with
performance in mind. We beat the competition and also provide server-side rendering.
We are fast now but we have even bigger plans for the future.

## Modular

jsblocks is made out of modules. Each module is independent and could be optionally removed from the framework.
You can decide your needs and preferences and optionally remove any unneeded modules.
Get your own custom jsblocks build containing only the modules you need [here](http://jsblocks.com/download#custom-build).

## Built-in utility library

Since a major part of our application logic is moved to the client, we need tools to handle complex data manipulations.
These tools should be intuitive and fast. The jsvalue module that is part of jsblocks achieves extremely high
performance by using advanced, dynamic code generation to create the fastest methods on the fly.

Let's look at an example that shows the power of the utility library:

```javascript
// returns true because the second condition is true
blocks
    .range(1, 100)
    .map(function (value) {
        return value * 2;
    })
    .filter(function (value) {
        return value % 2 == 0 && value < 50;
    })
    .contains(0)
    .or()
    .contains(22);
```

## Feature rich

 * Two-way data binding using observables that could be extended to bring any level of customization needed
 * Build in queries to work with the DOM while never actually touching it
 * Intuitive CSS3 Transitions & Animations and advanced, cross browser compatible JavaScript animations
 * Model-View-Controller architecture for building complex applications
 * Routing mechanism for single-page applications
 * Easy to setup connections to a service that automatically observes and changes via observables
 * Lazy loading of resources

## Forward thinking

We have a lot of things planned for the future, and the readers who are interested enough to read to the bottom
are a perfect audience.
 * Platform not just a framework - frameworks like Angular, Ember, React handle only the client-side of things.
 However we build complete solutions and there should be an easy(while optional) way to work with databases and services.
 * Virtual DOM - jsblocks architecture is build on top of a Virtual DOM and we want to share it with you.
 The final goal is cleaner way to work with the DOM while having better performance than directly touching the DOM.
 * jsvalue(utility library) as a separate library - the built-in utility library will be soon available as a separate project
 * Templating engine - it's also exciting to know that we are working on other interesting projects that aim to ease
 developers lives
