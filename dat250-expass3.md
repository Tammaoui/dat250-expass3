# DAT250 Assignment 3

Verify installation [x]

Exercise 1 [x]


Exercise 2 []



## Verify installation
I followed the tutorial as told in the assignment.
![bilde](https://user-images.githubusercontent.com/44643583/133894126-7ec9ee21-df91-4bf1-8417-4c2e64ecf48d.png)


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


### Delete a single object
`db.users.deleteOne({"email":"test@gmail.com"})`

### Bulk write

`db.users.bulkWrite([{insertOne: {"firstname": "Test", "lastname":"Test", "email":"Test3@gmail.com", "active":false} }, { deleteOne :{ "filter" : { "active" : false}}}])`



## Exercise 2
Add an additional operation developed by you and show its result given by its execution.

- Map: Process input data and create several small chunks of data.
- Reduce: Process data that comes from the mapper and store it in a new set of output.

Goal of the map-reduce operation is to output a collection of key, value pairs where the key is the id, and the value is how many orders the customer has. The value of this operation is to display how many orders each customer has had in the collection.

`var mapFunction1 = function() {emit(this._id, this.cust_id)}`

`var reduceFunction1 = function(keyId, customerIds) {return Array.sum(customerIds)}`

`db.orders.mapReduce(
   mapFunction1,
   reduceFunction1,
   { out: "map_orders_each_customer" }
)
`
To do this with aggregation:

`
db.orders.aggregate([
    {$group: {_id: "$_id", value: {$sum: $cust_id}}},
    {$out: "map_orders_each_customer"}
])
`

