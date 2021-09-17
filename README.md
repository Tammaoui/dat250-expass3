#DAT250 Assignment 3
Exercise 1 [X]
Exercise 2 []
Exercise 3 []


## Exercise 1

CRUD:
Create [X]
Read [X]
Update [X]
Delete [X]
Bulk write [X]

### Make the email property unique

`db.users.createIndex( { "email" : 1 }, { unique : true })`

### Create some objects

`db.users.insertOne({"firstname":"Ayoub", "lastname":"Tammaoui", "age":23,"active":true, "email":"Tammaoui.1998@gmail.com"})`

`db.users.insertOne({"firstname": "Emma", "lastname":"Perez", "age":23, "active":false, "email":"test@gmail.com"})`

### Read some objects

`db.users.find({"email":"Tammaoui.1998@gmail.com"})`

`db.users.find({"email":"test@gmail.com"})`



### Update one objects

`db.users.updateOne({"email":"test@gmail.com"},{ $set: { "active": false }})`

Confirm that the status is now false. This was set to true to begin with.

`   `

### Delete a single object
`db.users.deleteOne({"email":"test@gmail.com"})`

### Bulk write

`db.users.bulkWrite([{insertOne: {"firstname": "Test", "lastname":"Test", "email":"Test3@gmail.com", "active":false} }, { deleteOne :{ "filter" : { "active" : false}}}])`
`
