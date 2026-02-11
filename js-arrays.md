# JavaScript Arrays — Backend Cheat Sheet

> Focus: Data transform, validation, aggregation (API / DB work)

---

## ⭐ reduce() — MOST IMPORTANT (Aggregation / Object building)

Array ko ek single result mein convert karta hai

### Sum

```js
const total = orders.reduce((acc,o)=> acc + o.price , 0);
```

### Count

```js
const active = users.reduce((acc,u)=> u.active ? acc+1 : acc , 0);
```

### Object (indexing)

```js
const map = users.reduce((box,u)=>{
  box[u.id] = u.name;
  return box;
},{});
```

### Grouping

```js
const grouped = logs.reduce((box,l)=>{
  if(!box[l.user]) box[l.user] = [];
  box[l.user].push(l.action);
  return box;
},{});
```

### Sum per user

```js
const totals = payments.reduce((box,p)=>{
  box[p.user] = (box[p.user] || 0) + p.amount;
  return box;
},{});
```

Backend use:

* analytics
* reports
* caching
* indexing DB results

---

## map() — Response shaping

DB → API response format

```js
users.map(u => ({
  id: u.id,
  name: u.name
}));
```

Backend:
Remove sensitive fields (password, tokens)

---

## filter() — Remove unwanted data

```js
users.filter(u => u.active);
```

Backend:
soft delete, permissions, search

---

## find() — Single record

```js
users.find(u => u.id === id);
```

Backend:
GET /users/:id

---

## some() — Any match (authorization)

```js
roles.some(r => r === "admin");
```

Backend:
check permission

---

## every() — All valid (validation)

```js
fields.every(f => f !== "");
```

Backend:
input validation

---

## forEach() — Side effects

```js
users.forEach(u => log(u.email));
```

Backend:
logging / notifications

---

## slice() — Pagination

```js
items.slice(offset, offset + limit);
```

Backend:
page & limit APIs

---

## includes() — Existence check

```js
allowedRoles.includes(user.role);
```

Backend:
access control

---

# Mental Model

filter → kam karo
map → shape badlo
reduce → result banao
find → ek nikaalo
some → koi ek?
every → sab?

---

# Golden Rule

Backend arrays ≠ DSA
Backend arrays = DATA TRANSFORMATION
