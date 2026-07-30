SQL Injection Vulnerability Demonstration

This web app contains a SQL injection vulnerability in its student search feature. The search input is inserted directly into a SQL query using an f-string (f"SELECT * FROM students WHERE name = '{name}'"), without any sanitization or parameterization. This allows an attacker to manipulate the query's logic by entering specially crafted input.

For example, entering ' OR '1'='1 as the search term changes the query into SELECT * FROM students WHERE name = '' OR '1'='1'. Since '1'='1' is always true, the database returns every record in the table instead of matching a specific name — exposing all student data without proper authorization.

Fix: Use parameterized queries instead of string formatting, e.g. conn.execute("SELECT * FROM students WHERE name = ?", (name,)). This ensures user input is always treated as data, never as executable SQL CODE
