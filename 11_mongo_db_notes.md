# MongoDB & Mongoose Deep Notes

---

## 1️⃣ What is MongoDB?

MongoDB is a NoSQL database that stores data in BSON (Binary JSON) format.

Unlike SQL databases:
- No tables
- No rows
- No strict schema

Instead:
- Collections (like tables)
- Documents (like rows)
- Flexible structure

Example document:

{
  _id: ObjectId("6538ab2c..."),
  name: "Zohaib",
  age: 22,
  skills: ["Node.js", "Flutter"]
}

---

## 2️⃣ Why MongoDB in Backend?

- Flexible schema
- Easy JSON integration with Node.js
- Scalable
- Good for modern web apps

MongoDB works very naturally with JavaScript because data format is JSON-like.

---

## 3️⃣ What is Mongoose?

Mongoose is an ODM (Object Data Modeling) library for MongoDB.

It provides:
- Schema definition
- Validation
- Middleware (hooks)
- Cleaner query syntax
- Structure over flexible database

MongoDB is schema-less  
Mongoose adds schema control

---

## 4️⃣ Schema vs Model

### Schema
Defines structure of document.

Example:

const noteSchema = new mongoose.Schema({
  title: String,
  description: String
})

Schema defines:
- Fields
- Data types
- Rules

---

### Model

const Note = mongoose.model("Note", noteSchema)

Model is a wrapper around collection.
It allows interaction with MongoDB.

Model = Interface to database.

---

## 5️⃣ Default Fields

MongoDB automatically adds:

- _id (Primary key)
- __v (Version key from Mongoose)

_id is ObjectId:
- 12 byte value
- Globally unique
- Includes timestamp internally

---

## 6️⃣ CRUD Operations in Mongoose

### Create
await Note.create({...})

### Read
await Note.find()
await Note.findById(id)

### Update
await Note.findByIdAndUpdate(id, updateData, { new: true })

### Delete
await Note.findByIdAndDelete(id)

---

## 7️⃣ Query Filtering

Example:

await Note.find({ title: "Test" })

MongoDB uses JSON-style queries.

Operators:
$gt  (greater than)
$lt  (less than)
$in  (inside array)
$regex (pattern matching)

Example:

await Note.find({ age: { $gt: 18 } })

---

## 8️⃣ Data Types in Mongoose

Common types:

String  
Number  
Boolean  
Date  
Array  
ObjectId  

Example with references:

user: {
  type: mongoose.Schema.Types.ObjectId,
  ref: "User"
}

---

## 9️⃣ Middleware (Hooks)

Mongoose allows pre and post hooks.

Example:

noteSchema.pre("save", function(next) {
  console.log("Before saving")
  next()
})

Useful for:
- Hashing password
- Logging
- Data manipulation

---

## 🔟 Important Concepts to Remember

- MongoDB stores raw data
- Mongoose adds structure and rules
- _id is automatically generated
- Always handle errors in async queries
- Never trust client data blindly

---

## 🚀 Backend Architecture Insight

Request → Controller → Mongoose Model → MongoDB  
MongoDB → Mongoose → Controller → Response

Mongoose acts as a bridge between Node.js and MongoDB.
