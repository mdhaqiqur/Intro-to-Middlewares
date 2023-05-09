# Intro-to-Middlewares
const express = require('express');
const bodyParser = require('body-parser');

const app = express();
app.use(bodyParser.urlencoded({ extended: false }));

app.get('/add-product', (req, res) => {
  const form = `
    <form method="POST" action="/add-product">
      <label for="name">Product Name:</label>
      <input type="text" name="name" id="name"><br>
      <label for="price">Price:</label>
      <input type="number" name="price" id="price"><br>
      <button type="submit">Add Product</button>
    </form>
  `;
  res.send(form);
});

app.post('/add-product', (req, res) => {
  const { name, price } = req.body;
  console.log(`Product Name: ${name}, Price: ${price}`);
  res.redirect('/');
});

app.listen(3000, () => {
  console.log('Server listening on port 3000');
});
