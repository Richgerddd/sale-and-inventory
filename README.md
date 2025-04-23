Mysql
CFD final red project
CREATE DATABASE venben_store;

USE venben_store;

CREATE TABLE products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    stock INT NOT NULL
);

CREATE TABLE sales (
    id INT AUTO_INCREMENT PRIMARY KEY,
    product_id INT,
    quantity INT,
    total_price DECIMAL(10, 2),
    FOREIGN KEY (product_id) REFERENCES products(id)
);

INSERT INTO products (name, price, stock) VALUES
('1KG Rice', 55.00, 25),
('Cooking Oil', 10.00, 30),
('Eggs', 10.00, 90),
('Bread', 65.00, 40),
('Canned Tuna', 35.00, 20),
('Canned Sardines', 25.00, 20),
('Canned Corned Beef', 76.00, 20),
('Chocolate Candy', 2.00, 20),
('Choco Mallows', 40.00, 20),
('Biscuit', 15.00, 15),
('Crackers', 10.00, 30),
('Potato Chips', 18.00, 50),
('Pancit Canton', 15.00, 50),
('Instant Cup Noodles', 22.00, 50),
('1L Coke Soft Drink', 60.00, 20);

SELECT * FROM products;

UPDATE products
SET stock = stock + 10
WHERE id = 1;

INSERT INTO sales (product_id, quantity, total_price)
VALUES (1, 2, 110.00);

UPDATE products
SET stock = stock - 2
WHERE id = 1;

SELECT * FROM sales;

ALTER TABLE sales
DROP FOREIGN KEY sales_ibfk_1;

ALTER TABLE sales
ADD CONSTRAINT sales_ibfk_1
FOREIGN KEY (product_id) REFERENCES products(id) ON DELETE CASCADE;

