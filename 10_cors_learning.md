# CORS & Backend Networking – Deep Notes

---

## 1. What is CORS?

CORS stands for **Cross-Origin Resource Sharing**.

It is a browser security mechanism that restricts frontend applications from making requests to a backend running on a different origin.

An "origin" consists of:

* Protocol (http / https)
* Domain (localhost / example.com)
* Port (3000 / 5173)

If any of these differ → it becomes a cross-origin request.

---

## 2. Why Does CORS Error Happen?

Example:

Frontend running on:

```
http://localhost:5173
```

Backend running on:

```
http://localhost:3000
```

Browser blocks request because ports are different.

Error example:

```
Access to fetch has been blocked by CORS policy
```

Important:
CORS is enforced by the browser — not by Node.js.

---

## 3. How to Fix CORS in Express

Install CORS package:

```bash
npm install cors
```

Enable globally:

```js
const cors = require("cors");
app.use(cors());
```

Or allow specific origin:

```js
app.use(cors({
  origin: "http://localhost:5173"
}));
```

---

## 4. Preflight Request (Advanced)

For certain requests (PUT, DELETE, custom headers),
Browser sends an OPTIONS request first.

This is called a "preflight request".

Server must respond properly, otherwise request fails.

---

## 5. Binding Server to Network (Important Debugging Lesson)

If backend is started like this:

```js
app.listen(3000);
```

It may only bind to localhost.

To allow mobile device access on same WiFi:

```js
app.listen(3000, "0.0.0.0", () => {
  console.log("Server running");
});
```

This allows external network devices to connect.

---

## 6. Common Real Debugging Issues Learned

* Connection refused due to server not running
* Wrong IP address used
* Firewall blocking port
* Server not bound to 0.0.0.0
* CORS not enabled

---

## 7. Difference: CORS vs Network Error

CORS Error:

* Happens in browser
* Server actually receives request
* Browser blocks response

Network Error:

* Server not reachable
* Wrong IP or port
* Firewall issue

---

## 8. Engineering Insight

Understanding networking basics makes debugging easier.

Instead of guessing, check:

1. Is server running?
2. Is IP correct?
3. Is port correct?
4. Is CORS enabled?
5. Is firewall blocking?

---

## 9. Interview Revision Questions

* What is an origin?
* Why does CORS exist?
* What is a preflight request?
* Why bind server to 0.0.0.0?

---

End of Topic 2: CORS & Backend Networking
