<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>SKINCAREWITHTANISHA</title>
  <style>
    body { font-family: Arial, sans-serif; margin:0; padding:0; background:#fdfdfd; }
    header { background:#ffb6c1; padding:20px; text-align:center; }
    header h1 { margin:0; color:#fff; }
    nav { background:#333; padding:10px; text-align:center; }
    nav a { color:#fff; margin:0 15px; text-decoration:none; }
    .products { display:flex; justify-content:center; flex-wrap:wrap; padding:20px; }
    .product { border:1px solid #ccc; margin:10px; padding:15px; width:200px; text-align:center; }
    .product img { width:100%; height:auto; }
    .cart { background:#ffe4e1; padding:20px; text-align:center; }
    button { background:#ff69b4; color:#fff; border:none; padding:10px; cursor:pointer; margin-top:10px; }
  </style>
</head>
<body>
  <header>
    <h1>SKINCAREWITHTANISHA</h1>
    <p>Natural Products for Healthy Skin</p>
  </header>

  <nav>
    <a href="#products">Products</a>
    <a href="#cart">Cart</a>
    <a href="#contact">Contact</a>
  </nav>

  <section class="products" id="products">
    <div class="product">
      <img src="https://via.placeholder.com/200" alt="Face Cream">
      <h3>Herbal Face Cream</h3>
      <p>₹299</p>
      <button onclick="addToCart('Herbal Face Cream',299)">Add to Cart</button>
    </div>
    <div class="product">
      <img src="https://via.placeholder.com/200" alt="Aloe Gel">
      <h3>Aloe Vera Gel</h3>
      <p>₹199</p>
      <button onclick="addToCart('Aloe Vera Gel',199)">Add to Cart</button>
    </div>
    <div class="product">
      <img src="https://via.placeholder.com/200" alt="Scrub">
      <h3>Natural Scrub</h3>
      <p>₹249</p>
      <button onclick="addToCart('Natural Scrub',249)">Add to Cart</button>
    </div>
  </section>

  <section class="cart" id="cart">
    <h2>Your Cart</h2>
    <ul id="cartItems"></ul>
    <p id="total">Total: ₹0</p>
    <button onclick="checkout()">Checkout</button>
    <br><br>
    <!-- WhatsApp Order Button -->
    <a id="whatsappLink" href="#" target="_blank">
      <button style="background:green;">Order via WhatsApp</button>
    </a>
  </section>

  <section id="contact" style="text-align:center; padding:30px;">
    <h2>Contact Us</h2>
    <p>WhatsApp: +91-9876543210</p>
    <p>Email: glowcare@example.com</p>
  </section>

  <script>
    let cart = [];
    function addToCart(product, price) {
      cart.push({product, price});
      displayCart();
    }
    function displayCart() {
      let cartItems = document.getElementById("cartItems");
      cartItems.innerHTML = "";
      let total = 0;
      cart.forEach(item => {
        cartItems.innerHTML += `<li>${item.product} - ₹${item.price}</li>`;
        total += item.price;
      });
      document.getElementById("total").innerText = "Total: ₹" + total;
    }
    function checkout() {
      alert("Thank you for shopping! Please contact us on WhatsApp/Email to complete payment.");
    }
    function updateWhatsAppLink() {
      let message = "Hello, I want to order: ";
      cart.forEach(item => {
        message += `${item.product} (₹${item.price}), `;
      });
      let total = cart.reduce((sum, item) => sum + item.price, 0);
      message += `Total: ₹${total}`;
      document.getElementById("whatsappLink").href = 
        "https://wa.me/919876543210?text=" + encodeURIComponent(message);
    }
    setInterval(updateWhatsAppLink, 1000);
  </script>

  <footer style="background:#333; color:#fff; text-align:center; padding:15px; margin-top:20px;">
    <p>&copy; 2026 SKINCAREWITHTANISHA. All rights reserved.</p>
  </footer>
</body>
</html>
