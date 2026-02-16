## JS - Fetch API

## 1. Fetch API (then / catch)

Fetch is used to make HTTP requests (API calls). It returns a Promise.

Basic flow:

```
fetch → Promise → then → then → catch
```

---

### Example 1: Simple GET request

```js
fetch("https://jsonplaceholder.typicode.com/users")
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.log(err));
```

---

### Example 2: Handle response status

```js
fetch("https://jsonplaceholder.typicode.com/users/1")
  .then(res => {
    if(!res.ok) throw new Error("Request failed");
    return res.json();
  })
  .then(data => console.log(data))
  .catch(err => console.log("Error:",err.message));
```

---

### Example 3: POST request

```js
fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ title: "Hello" })
})
.then(res => res.json())
.then(data => console.log(data))
.catch(err => console.log(err));
```

---

### Example 4: Chain multiple thens

```js
fetch("https://jsonplaceholder.typicode.com/users/1")
  .then(res => res.json())
  .then(user => user.id)
  .then(id => console.log("User id:", id))
  .catch(err => console.log(err));
```

---

### Example 5: Equivalent async/await

```js
async function loadUser(){
  try{
    const res = await fetch("https://jsonplaceholder.typicode.com/users/1");
    const data = await res.json();
    console.log(data);
  }catch(err){
    console.log(err);
  }
}
loadUser();

