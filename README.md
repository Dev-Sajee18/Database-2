# Database-2
**1. Create a Database called customers.**

```
test> use customers
switched to db customers

```

**2. Create a collection called customerdetails.**

```
customers> db.createCollection("customerdetails")
{ ok: 1 }

```
**3. Insert all documents into the collection named   customerdetails.**

```
db.customerdetails.insertMany([{ "name": "John", "age": "25", "gender": "Male", "city": "New York" }, { "name": "Emily", "age": "22", "gender": "Female", "city": "London" }, { "name": "Daniel", "age": "28", "gender": "Male", "city": "Sydney" }, { "name": "Sophia", "age": "24", "gender": "Female", "city": "Paris" }, { "name": "William", "age": "26", "gender": "Male", "city": "Chicago" }, { "name": "Olivia", "age": "23", "gender": "Female", "city": "Los Angeles" }, { "name": "Benjamin", "age": "27", "gender": "Male", "city": "Toronto" }, { "name": "Mila", "age": "29", "gender": "Female", "city": "Berlin" }, { "name": "James", "age": "30", "gender": "Male", "city": "Tokyo" }])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("654d3b69737d42578ab3fcb4"),
    '1': ObjectId("654d3b69737d42578ab3fcb5"),
    '2': ObjectId("654d3b69737d42578ab3fcb6"),
    '3': ObjectId("654d3b69737d42578ab3fcb7"),
    '4': ObjectId("654d3b69737d42578ab3fcb8"),
    '5': ObjectId("654d3b69737d42578ab3fcb9"),
    '6': ObjectId("654d3b69737d42578ab3fcba"),
    '7': ObjectId("654d3b69737d42578ab3fcbb"),
    '8': ObjectId("654d3b69737d42578ab3fcbc")
  }
}

```

**4. Retrieve all documents from the collection and sort the results by the “age” field in ascending order.**

```
db.customerdetails.find().sort({"age":1}).pretty()
[
  {
    _id: ObjectId("654d3b69737d42578ab3fcb5"),
    name: 'Emily',
    age: '22',
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcb9"),
    name: 'Olivia',
    age: '23',
    gender: 'Female',
    city: 'Los Angeles'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcb7"),
    name: 'Sophia',
    age: '24',
    gender: 'Female',
    city: 'Paris'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcb4"),
    name: 'John',
    age: '25',
    gender: 'Male',
    city: 'New York'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcb8"),
    name: 'William',
    age: '26',
    gender: 'Male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcba"),
    name: 'Benjamin',
    age: '27',
    gender: 'Male',
    city: 'Toronto'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcb6"),
    name: 'Daniel',
    age: '28',
    gender: 'Male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcbb"),
    name: 'Mila',
    age: '29',
    gender: 'Female',
    city: 'Berlin'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcbc"),
    name: 'James',
    age: '30',
    gender: 'Male',
    city: 'Tokyo'
  }
]

```


**5. Count the number of females. **

```
customers> db.customerdetails.countDocuments({ "gender":"Female" })
4

```
**6. Insert one document into the customerdetails collection.**

```
customers> db.customerdetails.insertOne({ "name": "santhu","age":"21","gender" :"male","city":"toronto" })
{
  acknowledged: true,
  insertedId: ObjectId("654d43b9737d42578ab3fcbe")
}
```

**7. Update city=SriLanka to John.**

```
db.customerdetails.update({"name":"John"},{ $set: { city: "srilanka" }})
DeprecationWarning: Collection.update() is deprecated. Use updateOne, updateMany, or bulkWrite.
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
```

**8. Remove the customer from Tokyo.**

```

customers> db.customerdetails.remove({"city":"Tokyo"})
{ acknowledged: true, deletedCount: 1 }

```

**9.  Find customers not from Los Angeles.**

```
db.customerdetails.find({ "city": { $ne: "Los Angeles" } })
[
  {
    _id: ObjectId("654d3b69737d42578ab3fcb4"),
    name: 'John',
    age: '25',
    gender: 'Male',
    city: 'srilanka'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcb5"),
    name: 'Emily',
    age: '22',
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcb6"),
    name: 'Daniel',
    age: '28',
    gender: 'Male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcb7"),
    name: 'Sophia',
    age: '24',
    gender: 'Female',
    city: 'Paris'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcb8"),
    name: 'William',
    age: '26',
    gender: 'Male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcba"),
    name: 'Benjamin',
    age: '27',
    gender: 'Male',
    city: 'Toronto'
  },
  {
    _id: ObjectId("654d3b69737d42578ab3fcbb"),
    name: 'Mila',
    age: '29',
    gender: 'Female',
    city: 'Berlin'
  },
  {
    _id: ObjectId("654d43b9737d42578ab3fcbe"),
    name: 'santhu',
    age: '21',
    gender: 'male',
    city: 'toronto'
  }
]
```

**10.Find the customers who are older than age 25.**

```
customers> db.customerdetails.find({ "age": {$gt:("25")} })
[
  {
    _id: ObjectId("654ca6a8f41d0bb8c74d2fb3"),
    name: 'Daniel',
    age: '28',
    gender: 'Male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("654ca6a8f41d0bb8c74d2fb5"),
    name: 'William',
    age: '26',
    gender: 'Male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("654ca6a8f41d0bb8c74d2fb7"),
    name: 'Benjamin',
    age: '27',
    gender: 'Male',
    city: 'Toronto'
  },
  {
    _id: ObjectId("654ca6a8f41d0bb8c74d2fb8"),
    name: 'Mila',
    age: '29',
    gender: 'Female',
    city: 'Berlin'
  }
]
```
**11.Retrieve the males who are less than 25.**

```
Explain
customers> db.customerdetails.find({ "age": {$lt:("25")},"gender":"Male" })
[
  {
    _id: ObjectId("654cb000f41d0bb8c74d2fba"),
    name: 'Sajee',
    age: '24',
    gender: 'Male',
    city: 'Toronto'
  }
]

```

**12.Update Francis age to 35, if Francis is not available upsert. **

```
customers> db.customerdetails.update({"name":"Francis"},{ $set: {"age":"35"}},{ upsert: true })
DeprecationWarning: Collection.update() is deprecated. Use updateOne, updateMany, or bulkWrite.
{
  acknowledged: true,
  insertedId: ObjectId("654ceed0937b2d69715cfcba"),
  matchedCount: 0,
  modifiedCount: 0,
  upsertedCount: 1
}
```

**13.Retrieve males who are younger than 30 and older than25.**

```
customers> db.customerdetails.find({ "age": {$lt:("30"),$gt:("25")},"gender":"Male" })
[
  {
    _id: ObjectId("654ca6a8f41d0bb8c74d2fb3"),
    name: 'Daniel',
    age: '28',
    gender: 'Male',
    city: 'Sydney'
  },
  {
    _id: ObjectId("654ca6a8f41d0bb8c74d2fb5"),
    name: 'William',
    age: '26',
    gender: 'Male',
    city: 'Chicago'
  },
  {
    _id: ObjectId("654ca6a8f41d0bb8c74d2fb7"),
    name: 'Benjamin',
    age: '27',
    gender: 'Male',
    city: 'Toronto'
  }
]

```

**14.Find a customer who is lesser than or equal to 23.**

```

customers> db.customerdetails.find({ "age": {$lte:("23")} })
[
  {
    _id: ObjectId("654ca6a8f41d0bb8c74d2fb2"),
    name: 'Emily',
    age: '22',
    gender: 'Female',
    city: 'London'
  },
  {
    _id: ObjectId("654ca6a8f41d0bb8c74d2fb6"),
    name: 'Olivia',
    age: '23',
    gender: 'Female',
    city: 'Los Angeles'
  }
]

```










