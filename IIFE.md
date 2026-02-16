## Javascript - Immediately Invoked Function Expression

## IIFE (Immediately Invoked Function Expression)

An IIFE is a function that runs immediately after being defined.

```js
(function () {
  console.log("runs immediately");
})();
```

### Arrow version

```js
(() => {
  console.log("arrow IIFE");
})();
```

### Why used in backend?

* isolate variables
* run startup config once
* avoid global pollution

```js
const config = (() => {
  const PORT = 3000;
  const ENV = "dev";
  return { PORT, ENV };
})();

console.log(config.PORT);
```

---

Next Topic: Async / Await
