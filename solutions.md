How many users are there?

`SELECT COUNT(*) FROM users;`

What are the 5 most expensive items?

`SELECT * FROM items ORDER BY price DESC LIMIT 5;`

What's the cheapest book? (Does that change for "category is exactly 'book'" versus "category contains 'book'"?)

`SELECT * FROM items WHERE category LIKE "%Books%" ORDER BY price ASC LIMIT 1;`

Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?

`SELECT * FROM users INNER JOIN addresses ON addresses.user_id = users.id WHERE addresses.street = "6439 Zetta Hills";`
`SELECT * FROM addresses WHERE user_id = 40;`

Correct Virginie Mitchell's address to "New York, NY, 10108".

`SELECT * FROM addresses JOIN users ON users.id = addresses.user_id WHERE users.first_name = "Virginie" AND users.last_name = "Mitchell" AND addresses.state = "NY";`

`UPDATE addresses SET city = "New York", zip = 10108 WHERE street = "12263 Jake Crossing";`

How much would it cost to buy one of each tool?

`SELECT SUM(price) FROM items WHERE category LIKE "%Tools%"`

How many total items did we sell?

`SELECT SUM(quantity) FROM orders;`

How much was spent on books?

`SELECT SUM(price * quantity) FROM items INNER JOIN orders ON items.id = orders.item_id WHERE items.category LIKE "%Book%";` (1081352)

Simulate buying an item by inserting a User for yourself and an Order for that User.
`INSERT INTO users VALUES ( "Duncan", "Neal", "duncan.neal@xmail.com");`
`INSERT INTO orders (user_id, item_id, quantity, created_at) VALUES (378, 20, 90, 5, CURRENT_TIMESTAMP);`


What item was ordered most often? Grossed the most money?

`SELECT MAX( quantity ), item_id FROM orders`

`SELECT MAX(price * quantity), item_id FROM items INNER JOIN orders ON items.id = orders.item_id;`

What user spent the most?

What were the top 3 highest grossing categories?
