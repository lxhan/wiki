## Event loop

- A loop that pick events from the event queue and pushes their callbacks to the call stack.

---

![event loop 1](/img/event_loop_1.jpg)

---

![event loop 2](/img/event_loop_2.jpg)

---

![event loop 3](/img/event_loop_3.jpg)

---


- If call stack and loop queue are both empty node will exit.
- Besides `V8` and `libuv` Node has these external dependencies: 
  - `http-parser`
  - `c-ares`
  - `OpenSSL`
  - `zlib`
- Node can run with Chakra engine
- IIFE - Immediately Invoked Function Expression
- `require.resolve('module-name')` - check for existence of a local module
