###1) Why would you consider a Scripting Language as JavaScript as your Backend Platform.
Node.js is a JavaScript runtime that uses the V8 engine developed by Google for use in Chrome. V8 compiles and executes JavaScript at lightning speeds mainly due to the fact that V8 compiles JavaScript into native machine code. In addition to lightning fast JavaScript execution, the real magic behind Node.js is the event loop. The event loop is a single thread that performs all I/O operations asynchronously. Traditionally, I/O operations either run synchronously (blocking) or asynchronously by spawning off parallel threads to perform the work. This old approach consumes a lot of memory and is notoriously difficult to program. In contrast, when a Node application needs to perform an I/O operation, it sends an asynchronous task to the event loop, along with a callback function, and then continues to execute the rest of its program. When the async operation completes, the event loop returns to the task to execute its callback.

**In other words, reading and writing to network connections, reading/writing to the filesystem, and reading/writing to the database–all very common tasks in web apps–execute very, very fast in Node. Node allows you to build fast, scalable network applications capable of handling a huge number of simultaneous connections with high throughput**

Sources: http://blog.modulus.io/top-10-reasons-to-use-node

###2) Explain Pros & Cons in using Node.js + Express to implement your Backend compared to a strategy using for example Java/JAX-RS/Tomcat  
###3) Node.js uses a Single Threaded Non-blocking strategy to handle asynchronous task. Explain strategies to implement a Node.js based server architecture that still could take advantage of a multi-core Server. 
###4) Explain, using relevant examples, concepts related to the testing a REST-API using Node/JavaScript + relevant packages  
###5) Explain, using relevant examples, the Express concept; middleware. 
###6) Explain, using relevant examples, how to implement sessions, and the legal implications of doing this. 
###7) Compare the express strategy toward (server side) templating with the one you used with Java on second semester.
###8) Explain, using a relevant examples, your strategy for implementing a REST-API with Node/Express and show how you can "test" all the four CRUD operations programmatically using for example the Request package.  
###9) Explain, using relevant examples, about testing JavaScript code, relevant packages (Mocha etc.) and how to test asynchronous code. 
###10) Explain, using relevant examples, different ways to mock out databases, HTTP-request etc. 