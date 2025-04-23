# sale-and-inventory
final req cfd
-- 1. Create the database
CREATE DATABASE venben_store;

-- 2. Use the database
USE venben_store;

-- 3. Create the 'products' table
CREATE TABLE products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    stock INT NOT NULL
);

-- 4. Create the 'sales' table
CREATE TABLE sales (
    id INT AUTO_INCREMENT PRIMARY KEY,
    product_id INT,
    quantity INT,
    total_price DECIMAL(10, 2),
    FOREIGN KEY (product_id) REFERENCES products(id)
);

-- 5. Insert initial product data
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

-- 6. View all products
SELECT * FROM products;

-- 7. Update stock of a specific product (example: add 10 to product with id 1)
UPDATE products
SET stock = stock + 10
WHERE id = 1;

-- 8. Record a sale (example: sell 2 units of product with id 1)
INSERT INTO sales (product_id, quantity, total_price)
VALUES (1, 2, 110.00);

-- 9. Update stock after the sale
UPDATE products
SET stock = stock - 2
WHERE id = 1;

-- 10. View all sales transactions
SELECT * FROM sales;

-- 11. Setup cascade delete (optional)
-- If you want to delete a product and automatically remove related sales:
ALTER TABLE sales
DROP FOREIGN KEY sales_ibfk_1;

ALTER TABLE sales
ADD CONSTRAINT sales_ibfk_1
FOREIGN KEY (product_id) REFERENCES products(id) ON DELETE CASCADE;

-- 12. Exit MySQL (type in MySQL prompt, not script)
-- EXIT;

