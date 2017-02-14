# SQL-Practice

Explorer Mode

How many users are there?
  SELECT COUNT( * ) FROM users;
  50

What are the 5 most expensive items?
  SELECT title, price FROM items ORDER BY price DESC LIMIT 5;
  Small Cotton Gloves|9984
  Small Wooden Computer|9859
  Awesome Granite Pants|9790
  Sleek Wooden Hat|9390
  Ergonomic Steel Car|9341

What's the cheapest book? (Does that change for "category is exactly 'book'" versus "category contains 'book'"?)
  1) SELECT title, category, price FROM items WHERE category='Books' ORDER BY price ASC LIMIT 1;
  2) SELECT title, category, price FROM items WHERE category LIKE '&book&' ORDER BY price ASC LIMIT 3;

  1) Ergonomic Granite Chair|Books|1496
  2) Ergonomic Granite Chair|Books|1496
  It did not change


Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?
 SELECT * FROM addresses WHERE street LIKE '%6439%';
 SELECT first_name, last_name, addresses.street, addresses.city, addresses.state FROM users LEFT JOIN addresses ON users.id=addresses.user_id WHERE user.id=40;

 Corrine Little lives there, yes she has 2 addresses.

Correct Virginie Mitchell's address to "New York, NY, 10108".
  SELECT * FROM users WHERE first_name LIKE '%virginie%';
  UPDATE addresses SET city = 'New York', zip = 10108 WHERE id = 41;

  There were two addresses for user_id 39 which in users table was Virginie Mitchell

How much would it cost to buy one of each tool?
  SELECT SUM(price) FROM items WHERE category LIKE '%tool%'tta;
  $46,477

How many total items did we sell?
  SELECT SUM(quantity) FROM orders;
  $2,125

How much was spent on books?
  SELECT SUM(orders.quantity*items.price) AS total FROM items INNER JOIN orders ON items.id=orders.item_id WHERE items.category LIKE '%book%';
  $1,081,352

Simulate buying an item by inserting a User for yourself and an Order for that User.
  INSERT INTO users (first_name, last_name, email) VALUES ('Kendrick', 'Lo', 'email@gmail.com')
  INSERT INTO orders (user_id, item_id, quantity, created_at) VALUES (51, 4, 11, CURRENT_TIMESTAMP);

Adventure Mode

What item was ordered most often? Grossed the most money?
What user spent the most?
What were the top 3 highest grossing categories?
