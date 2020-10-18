## What is Node.js

Node.js is a js runtime environment which use event driven, non blocking io model.
Node.js is single threaded, event driven environment.

### Pros

- Fast processing
- Event based model
- Best for streaming big amounts of data and io intensive operations

### Cons

- Since it is single threaded not suitable for heavy computations. 

## Event driven 

Programming paradigm in which the flow of the program is determined by events such as user actions, sensor outputs, or messages from other programs or threads.

In Node.js it is mainly publish-subscribe pattern.

## Event loop

- A loop that pick events from the event queue and pushes their callbacks to the call stack.

Event loop handles all async callbacks. All callbacks are queued in loop and will run when response is received. 

- If call stack and loop queue are both empty node will exit.
- Besides `V8` and `libuv` Node has these external dependencies: 
  - `http-parser`
  - `c-ares`
  - `OpenSSL`
  - `zlib`
- Node can run with Chakra engine
- IIFE - Immediately Invoked Function Expression
- `require.resolve('module-name')` - check for existence of a local module

---
![event loop 1](/img/event_loop_1.jpg)
---
![event loop 2](/img/event_loop_2.jpg)
---
![event loop 3](/img/event_loop_3.jpg)
---
