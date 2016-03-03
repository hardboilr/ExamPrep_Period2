###1) Why would you consider a Scripting Language as JavaScript as your Backend Platform.
Node.js is a JavaScript runtime that uses the V8 engine developed by Google for use in Chrome. V8 compiles and executes JavaScript at lightning speeds mainly due to the fact that V8 compiles JavaScript into native machine code. In addition to lightning fast JavaScript execution, the real magic behind Node.js is the event loop. The event loop is a single thread that performs all I/O operations asynchronously. Traditionally, I/O operations either run synchronously (blocking) or asynchronously by spawning off parallel threads to perform the work. This old approach consumes a lot of memory and is notoriously difficult to program. In contrast, when a Node application needs to perform an I/O operation, it sends an asynchronous task to the event loop, along with a callback function, and then continues to execute the rest of its program. When the async operation completes, the event loop returns to the task to execute its callback.

**In other words, reading and writing to network connections, reading/writing to the filesystem, and reading/writing to the database–all very common tasks in web apps–execute very, very fast in Node. Node allows you to build fast, scalable network applications capable of handling a huge number of simultaneous connections with high throughput**

[Source](http://blog.modulus.io/top-10-reasons-to-use-node)

###2) Explain Pros & Cons in using Node.js + Express to implement your Backend compared to a strategy using for example Java/JAX-RS/Tomcat. 

####Java/JAX-RS/Tomcat 
- (+) True object oriented language -> increased readability and somewhat easier to maintain a large codebase.  
- (+) Easier to debug -> The compiler will, by default, give back more useful information about the error. 
- (+) Maturity -> larger workforce (short term?), proven and stable server technology.
- (-) Lots of configuration up front -> Tomcat is big and heavy and comes with a lot of features (that you might not ever use).
- (-) Threads are memory intensive and can be difficult to work with.

####JavaScript/Node.js/Express
- (+) Suited for apps -> A lot of IO, chat- web rest- servers, streaming servers, games 
- (+) One language -> <insert a lot of obvious reasons here>
- (+) Refer to 1)
- (+) Lightweight -> Barebones from the outset, but add functionality as you go with npm.  
- (+) Modern & Sexy -> get a lot of functionality for "free" using npm to get the latest and greatest from an active community.
- (+) Non blocking API -> easier to use than threads.  
- (-) Not suited for apps -> Heavy CPU intensive applications.
- (-) Chaotic code -> harder to read code, especially when being sloppy (see first pro from java)
- (-) Not a completely matured technology (from slides: Node.js Intro)
- (-) New packages pops up all the time (from slides: Node.js Intro)
- (-) Unhandled errors will shutdown the server (from slides: Node.js Intro)

###3) Node.js uses a Single Threaded Non-blocking strategy to handle asynchronous task. Explain strategies to implement a Node.js based server architecture that still could take advantage of a multi-core Server. 
>Even though Node uses a Single Threaded strategy, it is easy to scale it to multi-core machines. For CPU intensive task Node.js can fire up child processes, and for scaling up webservices the trick is to start multiple node instances on the fly.
>Node has built in support for this via the Clustering module and Express run multiple virtual hosts (i.e. run multiple domains under one IP) out of the box.

Utilize a load balancer to manage multiple Node.js processes. 

[Source](http://js2016.azurewebsites.net/node1/NodeIntro.html)

###4) Explain, using relevant examples, concepts related to testing a REST-API using Node/JavaScript + relevant packages.
**Mocha**: Mocha is a test framework running on Node.js and can be used to test synchronous and asynchronous functions. Mocha tests run serially, allowing for flexible and accurate reporting, while mapping uncaught exceptions to the correct test cases.  -> "describe" + "it".
**Chai**: Chai is a BDD / TDD assertion library for node and the browser that can be delightfully paired with any javascript testing framework. -> "should" + "expect" + "assert".
**request**: Request is designed to be the simplest way possible to make http calls. It supports HTTPS and follows redirects by default.

Testing **synchronous** functions: 1_Mocha_Chai_Testing/Sources/test/testCalculator.js [Github](insert link here)

Testing **asynchronous** functions: 2_ServersideTemplating/Sources/test/jokesApiTest.js [Github](insert link)

use the **done** callback for asynchronous functions.

[Mocha](https://mochajs.org/)
[Chai](http://chaijs.com/)
[request](https://www.npmjs.com/package/request)

###5) Explain, using relevant examples, the Express concept; middleware.
**Middleware** functions are functions that you bind to the express instance and works as a way to configure/add functionality to the server. Otherwise boring question.

1. Application level middleware: Mount to all requests or specific endpoints to define routes.
2. Router-level middleware: Router-level middleware works in the same way as application-level middleware, except it is bound to an instance of express.Router().
3. Error-handling middleware: Define error-handling middleware functions in the same way as other middleware functions, except with four arguments instead of three, specifically with the signature (err, req, res, next)):
4. Third-party middleware: Add functionality.

[Exress documentation on middleware](http://expressjs.com/en/guide/using-middleware.html)
 
###6) Explain, using relevant examples, how to implement sessions, and the legal implications of doing this. 

Enable session first:
```javascript
app.use(session({secret: 'secret_3162735', saveUninitialized: true, resave: true}));
```
Then get the session, doing this:
```javascript
var session = req.session;
```
and add objects to the session object, doing this:
```javascript
session.userName = req.body.userName;
``` 

A cookie consent has to be implemented on the site, if the cookie is used to track user behaviour. 

[EU cookie info](http://ec.europa.eu/ipg/basics/legal/cookies/index_en.htm)

###7) Compare the express strategy toward (server side) templating with the one you used with Java on second semester.
??

###8) Explain, using a relevant examples, your strategy for implementing a REST-API with Node/Express and show how you can "test" all the four CRUD operations programmatically using for example the Request package.  
Refer to question 4).

###9) Explain, using relevant examples, about testing JavaScript code, relevant packages (Mocha etc.) and how to test asynchronous code. 
Refer to question 4).

###10) Explain, using relevant examples, different ways to mock out databases, HTTP-request etc. 
Refer to question 4) for general info.
Nock can be used to test modules that perform HTTP requests in isolation.

See these two github examples: [5_Mocking_HTTP-requests]("github link") [6_Mocking_HTTP-requests]("github link")

[nock](https://www.npmjs.com/package/nock)

