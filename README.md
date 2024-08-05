# Task-1
LANDING PAGE ON SHOP OF LUXURY WATCHES
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Luxury Watches</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <div class="container">
            <h1>Luxury Watches</h1>
            <nav>
                <ul>
                    <li><a href="#home">Home</a></li>
                    <li><a href="#products">Products</a></li>
                    <li><a href="#cart">Cart</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>
    <section id="home">
        <div class="container">
            <h2>Welcome to Luxury Watches</h2>
            <p>Your destination for the finest luxury watches.</p>
        </div>
    </section>
    <section id="products" class="container">
        <h2>Our Products</h2>
        <div class="product" data-id="1">
            <img src="assets/watch1.jpg" alt="Luxury Watch 1">
            <h3>Luxury Watch 1</h3>
            <p>$5000</p>
            <button onclick="addToCart(1)">Add to Cart</button>
        </div>
        <div class="product" data-id="2">
            <img src="assets/watch2.jpg" alt="Luxury Watch 2">
            <h3>Luxury Watch 2</h3>
            <p>$6000</p>
            <button onclick="addToCart(2)">Add to Cart</button>
        </div>
        <!-- Add more products as needed -->
    </section>
    <section id="cart" class="container">
        <h2>Your Cart</h2>
        <div id="cart-items">
            <!-- Cart items will be dynamically added here -->
        </div>
        <button onclick="checkout()">Checkout</button>
    </section>
    <section id="contact" class="container">
        <h2>Contact Us</h2>
        <form id="contact-form">
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required>
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>
            <label for="message">Message:</label>
            <textarea id="message" name="message" required></textarea>
            <button type="submit">Send</button>
        </form>
    </section>
    <footer>
        <div class="container">
            <p>&copy; 2024 Luxury Watches. All rights reserved.</p>
        </div>
    </footer>
    <script src="scripts.js"></script>
</body>
</html>
body {
    font-family: 'Arial', sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

.container {
    width: 80%;
    margin: auto;
    overflow: hidden;
}

header {
    background-color: #333;
    color: white;
    padding: 10px 0;
    text-align: center;
}

nav ul {
    list-style: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 0 10px;
}

nav ul li a {
    color: white;
    text-decoration: none;
    font-weight: bold;
}

section {
    padding: 20px 0;
    margin: 20px 0;
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.product {
    display: inline-block;
    width: 45%;
    margin: 2.5%;
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 10px;
    text-align: center;
    padding
let cart = [];

function addToCart(productId) {
    const product = document.querySelector(`.product[data-id="${productId}"]`);
    const productName = product.querySelector('h3').innerText;
    const productPrice = product.querySelector('p').innerText;
    const cartItem = { id: productId, name: productName, price: productPrice };
    cart.push(cartItem);
    updateCartDisplay();
}

function updateCartDisplay() {
    const cartItems = document.getElementById('cart-items');
    cartItems.innerHTML = '';
    cart.forEach((item, index) => {
        const cartItem = document.createElement('div');
        cartItem.classList.add('cart-item');
        cartItem.innerHTML = `
            <p>${item.name} - ${item.price}</p>
            <button onclick="removeFromCart(${index})">Remove</button>
        `;
        cartItems.appendChild(cartItem);
    });
}

function removeFromCart(index) {
    cart.splice(index, 1);
    updateCartDisplay();
}

function checkout() {
    alert('Thank you for your purchase!');
    cart = [];
    updateCartDisplay();
}
