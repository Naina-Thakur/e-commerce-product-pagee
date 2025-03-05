<html>
<head>
    <title>Online Shopping Application</title>
    <link rel="stylesheet" href="shopping2.css">
    <style>
        body {
            display: flex;
            flex-direction: column;
            min-height: 100vh;
            margin: 0;
        }
        main {
            flex: 1;
        }
        .container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            padding: 20px;
        }
        .product-card {
            border: 1px solid #ddd;
            padding: 30px;
            border-radius: 5px;
            width: 400px;
            text-align: center;
            position: relative;
        }
        .rating {
            display: flex;
            justify-content: center;
            margin: 10px 0;
        }
        .rating span {
            font-size: 20px;
            color: gold;
        }
        .price {
            font-size: 18px;
            font-weight: bold;
        }
        .add-to-cart, .buy-now {
            display: block;
            margin: 10px auto;
            padding: 10px 20px;
            background-color: #28a745;
            color: #fff;
            text-decoration: none;
            border-radius: 5px;
        }
        .buy-options {
            display: none;
            margin: 10px 0;
        }
        .buy-options a {
            display: block;
            margin: 5px 0;
            padding: 10px 20px;
            background-color: #007bff;
            color: #fff;
            text-decoration: none;
            border-radius: 5px;
        }
        .whitelist-icon {
            position: absolute;
            top: 10px;
            right: 10px;
            font-size: 24px;
            cursor: pointer;
        }
        .whitelist-icon.active {
            color: red;
        }
        footer {
            text-align: center;
            padding: 10px;
            background-color: #f1f1f1;
        }
        .product-link {
            cursor: pointer;
            color: blue;
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <header>
        <center>
        <h1>Online Shopping</h1>
    </center>
    </header>
    <nav>
        <a href="#">Home</a><br>
        <a href="#">Products</a><br>
        <a href="#">About</a><br>
        <a href="#">Contact</a><br>
        <a href="#" id="view-wishlist">View Wishlist</a>
    </nav>
    <main class="container">
        <div class="main">
            <div class="product-card" data-id="1">
                <span class="whitelist-icon" onclick="toggleWhitelist(this)">☆</span>
                <img src="iPhone.webp" alt="iphone 15">
                <p class="price">$19.99</p>
                <p class="product-link" onclick="showDetails(this)">View Details</p>
                <div class="product-details" style="display:none;">
                    <p>Apple iPhone 15 Pro (128 GB Storage, Black Titanium)</p>
                    <div class="rating">
                        <span>★★★★☆</span>
                    </div>
                </div>
            </div>
            <div class="product-card" data-id="1">
                <span class="whitelist-icon" onclick="toggleWhitelist(this)">☆</span>
                <img src="hersheys.webp" alt="hersheys">
                <p class="price">$2.01</p>
                <p class="product-link" onclick="showDetails(this)">View Details</p>
                <div class="product-details" style="display:none;">
                    <p>Sweeten Every Moment with Hershey’s! Whether you’re drizzling, mixing, or baking, Hershey’s Syrup adds a burst of chocolatey goodness to your favorite treats.</p>
                    <div class="rating">
                        <span>★★★★☆</span>
                    </div>
                </div>
            </div>
            <div class="product-card" data-id="1">
                <span class="whitelist-icon" onclick="toggleWhitelist(this)">☆</span>
                <img src="clothes.webp" alt="clothes">
                <p class="price">$9.99</p>
                <p class="product-link" onclick="showDetails(this)">View Details</p>
                <div class="product-details" style="display:none;">
                    <p>Upgrade your wardrobe with the perfect blend of style and comfort!</p>
                    <div class="rating">
                        <span>★★★★☆</span>
                    </div>
                </div>
            </div>
            <div class="product-card" data-id="1">
                <span class="whitelist-icon" onclick="toggleWhitelist(this)">☆</span>
                <img src="beetroot.webp" alt="beetroot">
                <p class="price">$12.99</p>
                <p class="product-link" onclick="showDetails(this)">View Details</p>
                <div class="product-details" style="display:none;">
                    <p>Beetroot Skin Care Cream deeply nourishes, hydrates, and brightens your skin. Packed with antioxidants, vitamins, and essential nutrients, it helps combat dullness, reduce pigmentation, and promote a healthy, radiant glow.</p>
                    <div class="rating">
                        <span>★★★★☆</span>
                    </div>
                </div>
            </div>
            <div class="product-card" data-id="1">
                <span class="whitelist-icon" onclick="toggleWhitelist(this)">☆</span>
                <img src="puma.webp" alt="puma">
                <p class="price">$28.99</p>
                <p class="product-link" onclick="showDetails(this)">View Details</p>
                <div class="product-details" style="display:none;">
                    <p>PUMA WHITE UNISEX EQUATE SL LACE-UP SNEAKERS</p>
                    <div class="rating">
                        <span>★★★★☆</span>
                    </div>
                </div>
            </div>
            <div class="product-card" data-id="1">
                <span class="whitelist-icon" onclick="toggleWhitelist(this)">☆</span>
                <img src="fruit.webp" alt="fruit">
                <p class="price">$19.99</p>
                <p class="product-link" onclick="showDetails(this)">View Details</p>
                <div class="product-details" style="display:none;">
                    <p>🌿 Pure Goodness, Packed with Flavor! The Excellence Fruit Basket is a perfect blend of premium, handpicked fruits, curated for freshness, taste, and nutrition.</p>
                    <div class="rating">
                        <span>★★★★☆</span>
                    </div>
                </div>
            </div>
        </div>
    </main>
    <script>
        function toggleWhitelist(icon) {
            icon.classList.toggle('active');
            const productId = icon.closest('.product-card').dataset.id;
            const productTitle = icon.closest('.product-card').querySelector('p.product-link').innerText;
            
            if (icon.classList.contains('active')) {
                addToWhitelist(productId, productTitle);
            } else {
                removeFromWhitelist(productId);
            }
        }

        function addToWhitelist(productId, productTitle) {
            let whitelist = JSON.parse(localStorage.getItem('whitelist')) || [];
            whitelist.push({ id: productId, title: productTitle });
            localStorage.setItem('whitelist', JSON.stringify(whitelist));
        }

        function removeFromWhitelist(productId) {
            let whitelist = JSON.parse(localStorage.getItem('whitelist')) || [];
            whitelist = whitelist.filter(item => item.id !== productId);
            localStorage.setItem('whitelist', JSON.stringify(whitelist));
        }

        function showDetails(link) {
            const productCard = link.closest('.product-card');
            const details = productCard.querySelector('.product-details');
            details.style.display = details.style.display === 'block' ? 'none' : 'block';
        }

        document.getElementById('view-whitelist').addEventListener('click', function(event) {
            event.preventDefault();
            let whitelist = JSON.parse(localStorage.getItem('whitelist')) || [];
            if (whitelist.length === 0) {
                alert('Your whitelist is empty.');
            } else {
                alert('Whitelisted Products:\n' + whitelist.map(item => item.title).join('\n'));
            }
        });
    </script>
</body>
</html>
