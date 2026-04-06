<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>Nocturna Atelier | Gothic Paintings Emporium</title>
    <!-- Google Fonts: Gothic Display + Modern Sans -->
    <link href="https://fonts.googleapis.com/css2?family=UnifrakturMaguntia&family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700&display=swap" rel="stylesheet">
    <!-- Font Awesome 6 (free icons) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <!-- EmailJS SDK -->
    <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0b0a0e;
            color: #e9e4f0;
            font-family: 'Inter', sans-serif;
            line-height: 1.5;
            scroll-behavior: smooth;
        }

        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #1a1722;
        }
        ::-webkit-scrollbar-thumb {
            background: #4a3a5c;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #7c5e9e;
        }

        h1, h2, h3, .gothic-title, .hero-title, .section-heading, .product-card h3, .cart-item-title {
            font-family: 'UnifrakturMaguntia', 'Times New Roman', cursive;
            letter-spacing: 2px;
            font-weight: normal;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 24px;
        }

        .site-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            padding: 24px 0;
            border-bottom: 1px solid #2a2533;
            margin-bottom: 32px;
        }
        .logo-area h1 {
            font-size: 2.6rem;
            background: linear-gradient(135deg, #f0e6d0, #b89f7a);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 3px;
            text-shadow: 0 0 4px rgba(0,0,0,0.5);
        }
        .logo-area p {
            font-size: 0.8rem;
            color: #aa9fbb;
            letter-spacing: 1px;
        }
        .cart-icon {
            position: relative;
            cursor: pointer;
            font-size: 1.8rem;
            background: #1e1a29;
            padding: 12px 18px;
            border-radius: 60px;
            transition: all 0.2s ease;
            border: 1px solid #3f3352;
        }
        .cart-icon:hover {
            background: #2f2840;
            transform: scale(1.02);
            border-color: #b8860b;
        }
        .cart-count {
            position: absolute;
            top: -6px;
            right: -6px;
            background: #b42b4b;
            color: white;
            font-size: 0.7rem;
            font-weight: bold;
            min-width: 22px;
            height: 22px;
            border-radius: 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 0 6px;
            font-family: 'Inter', sans-serif;
            box-shadow: 0 0 4px rgba(0,0,0,0.6);
        }

        .hero {
            background: radial-gradient(circle at 30% 10%, #1b1424, #030104);
            border-radius: 2rem;
            padding: 4rem 2rem;
            margin: 20px 0 60px 0;
            text-align: center;
            border: 1px solid #352e44;
            box-shadow: 0 20px 35px -12px black;
        }
        .hero-title {
            font-size: 3.8rem;
            color: #f0e2c5;
            text-shadow: 0 4px 12px #00000055;
            margin-bottom: 1rem;
        }
        .hero-sub {
            font-size: 1.2rem;
            max-width: 700px;
            margin: 0 auto 2rem auto;
            color: #cbc3dc;
        }
        .btn-primary {
            background: #2c1f38;
            border: 1px solid #9b7bb5;
            color: #f2e9ff;
            padding: 12px 28px;
            font-weight: 600;
            border-radius: 40px;
            font-size: 1rem;
            cursor: pointer;
            transition: 0.25s;
            display: inline-block;
            text-decoration: none;
        }
        .btn-primary:hover {
            background: #5a3e72;
            border-color: #d4af37;
            letter-spacing: 1px;
            box-shadow: 0 0 12px rgba(180, 130, 200, 0.4);
        }

        .section-heading {
            font-size: 2.4rem;
            margin: 40px 0 24px 0;
            border-left: 5px solid #b8860b;
            padding-left: 20px;
            letter-spacing: 2px;
        }
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 32px;
            margin-bottom: 70px;
        }
        .product-card {
            background: #131017;
            border-radius: 28px;
            overflow: hidden;
            transition: all 0.3s ease;
            border: 1px solid #2e273c;
            backdrop-filter: blur(2px);
            box-shadow: 0 12px 20px -12px rgba(0,0,0,0.6);
        }
        .product-card:hover {
            transform: translateY(-8px);
            border-color: #aa7bc7;
            box-shadow: 0 20px 28px -12px #2e1c3e;
        }

        .product-img-container {
            position: relative;
            width: 100%;
            overflow: hidden;
            border-radius: 28px 28px 0 0;
            background: #07060a;
        }
        .product-img {
            width: 100%;
            height: 320px;
            object-fit: cover;
            display: block;
            transition: transform 0.5s cubic-bezier(0.2, 0.9, 0.4, 1.1);
            will-change: transform;
        }
        .product-card:hover .product-img {
            transform: scale(1.08);
        }

        .sold-overlay {
            position: absolute;
            inset: 0;
            background: rgba(0, 0, 0, 0.75);
            backdrop-filter: blur(2px);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 5;
            pointer-events: none;
        }
        .sold-overlay span {
            font-family: 'UnifrakturMaguntia', cursive;
            font-size: 2.2rem;
            font-weight: bold;
            color: #e4c48a;
            text-transform: uppercase;
            letter-spacing: 6px;
            background: rgba(20, 12, 28, 0.7);
            padding: 0.5rem 1.5rem;
            border-radius: 60px;
            border: 1px solid #b8860b;
            transform: rotate(-5deg);
            box-shadow: 0 0 15px rgba(0,0,0,0.6);
            text-shadow: 0 2px 5px black;
            backdrop-filter: blur(3px);
        }
        .sold-overlay::before {
            content: "⚰️";
            position: absolute;
            top: 12px;
            left: 18px;
            font-size: 1.6rem;
            opacity: 0.7;
            filter: drop-shadow(0 2px 2px black);
        }
        .sold-overlay::after {
            content: "⚰️";
            position: absolute;
            bottom: 12px;
            right: 18px;
            font-size: 1.6rem;
            opacity: 0.7;
            filter: drop-shadow(0 2px 2px black);
        }

        .product-info {
            padding: 20px 20px 24px;
        }
        .product-card h3 {
            font-size: 1.8rem;
            margin-bottom: 8px;
            color: #eeddcc;
        }
        .product-price {
            font-size: 1.5rem;
            font-weight: 700;
            color: #d4af37;
            margin: 12px 0;
            letter-spacing: 1px;
        }
        .add-to-cart {
            background: #2a2336;
            border: none;
            width: 100%;
            padding: 12px;
            font-weight: 600;
            font-size: 1rem;
            border-radius: 60px;
            color: #f0e9ff;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            font-family: 'Inter', sans-serif;
        }
        .add-to-cart i {
            font-size: 1.1rem;
        }
        .add-to-cart:hover:not(:disabled) {
            background: #694a8a;
            color: white;
            letter-spacing: 0.5px;
        }
        .add-to-cart:disabled {
            background: #2a2336;
            opacity: 0.55;
            cursor: not-allowed;
            filter: grayscale(0.1);
            border: 1px solid #5a4a6e;
            color: #b9accf;
        }

        .about-section {
            background: #0f0d14;
            border-radius: 2rem;
            padding: 3rem 2rem;
            margin: 40px 0 60px;
            border: 1px solid #352e44;
            box-shadow: 0 12px 25px -12px black;
        }
        .about-section h2 {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
            color: #eeddcc;
            border-left: 5px solid #b8860b;
            padding-left: 20px;
        }
        .about-text {
            display: flex;
            flex-direction: column;
            gap: 1.2rem;
            font-size: 1.05rem;
            color: #d9d0e8;
            max-width: 85%;
            margin: 0 auto;
            text-align: center;
        }
        .about-text p {
            line-height: 1.6;
        }
        .signature {
            font-family: 'UnifrakturMaguntia', cursive;
            font-size: 1.5rem;
            margin-top: 1rem;
            color: #b89f7a;
        }

        .contact-section {
            background: #0f0d14;
            border-radius: 2rem;
            padding: 3rem 2rem;
            margin: 40px 0 60px;
            border: 1px solid #352e44;
            box-shadow: 0 12px 25px -12px black;
        }
        .contact-section h2 {
            font-size: 2.5rem;
            margin-bottom: 2rem;
            color: #eeddcc;
            border-left: 5px solid #b8860b;
            padding-left: 20px;
        }
        .contact-wrapper {
            display: flex;
            flex-wrap: wrap;
            gap: 3rem;
            justify-content: space-between;
        }
        .contact-info {
            flex: 1;
            min-width: 200px;
        }
        .contact-info p {
            margin: 1rem 0;
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1rem;
        }
        .contact-info i {
            width: 32px;
            color: #b8860b;
            font-size: 1.3rem;
        }
        .contact-form {
            flex: 2;
            min-width: 260px;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }
        .contact-form input, .contact-form textarea {
            background: #1e1a29;
            border: 1px solid #3f3352;
            padding: 12px 18px;
            border-radius: 30px;
            color: #f0e9ff;
            font-family: 'Inter', sans-serif;
            font-size: 0.95rem;
            outline: none;
            transition: 0.2s;
        }
        .contact-form input:focus, .contact-form textarea:focus {
            border-color: #b8860b;
            box-shadow: 0 0 8px rgba(184, 134, 11, 0.3);
        }
        .contact-form textarea {
            min-height: 100px;
            resize: vertical;
            border-radius: 20px;
        }
        .contact-form button {
            background: #2c1f38;
            border: 1px solid #9b7bb5;
            padding: 12px;
            border-radius: 40px;
            font-weight: 600;
            cursor: pointer;
            color: #f2e9ff;
            transition: 0.2s;
            width: fit-content;
            min-width: 160px;
        }
        .contact-form button:hover {
            background: #5a3e72;
            border-color: #d4af37;
            letter-spacing: 1px;
        }
        .contact-form button:disabled {
            opacity: 0.7;
            cursor: not-allowed;
        }
        @media (max-width: 760px) {
            .about-text {
                max-width: 100%;
            }
            .contact-wrapper {
                flex-direction: column;
            }
        }

        footer {
            margin-top: 80px;
            border-top: 1px solid #292138;
            padding: 40px 0 32px;
            text-align: center;
            color: #948dab;
            font-size: 0.85rem;
        }
        footer i {
            color: #b97f52;
            margin: 0 4px;
        }

        .cart-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.85);
            backdrop-filter: blur(4px);
            z-index: 1000;
            visibility: hidden;
            opacity: 0;
            transition: 0.25s ease;
        }
        .cart-overlay.open {
            visibility: visible;
            opacity: 1;
        }
        .cart-sidebar {
            position: fixed;
            top: 0;
            right: -100%;
            width: 420px;
            max-width: 90vw;
            height: 100%;
            background: #0d0b12;
            border-left: 2px solid #3e2c52;
            box-shadow: -8px 0 35px rgba(0, 0, 0, 0.8);
            z-index: 1001;
            transition: right 0.3s cubic-bezier(0.2, 0.9, 0.4, 1.1);
            display: flex;
            flex-direction: column;
            font-family: 'Inter', sans-serif;
        }
        .cart-sidebar.open {
            right: 0;
        }
        .cart-header {
            padding: 24px 20px;
            border-bottom: 1px solid #2c243b;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .cart-header h2 {
            font-family: 'UnifrakturMaguntia', cursive;
            font-size: 1.8rem;
            color: #e9dccc;
        }
        .close-cart {
            background: none;
            border: none;
            font-size: 1.8rem;
            color: #b79fcf;
            cursor: pointer;
            transition: 0.2s;
        }
        .close-cart:hover {
            color: #ffb347;
            transform: rotate(90deg);
        }
        .cart-items-list {
            flex: 1;
            overflow-y: auto;
            padding: 16px;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        .cart-item {
            display: flex;
            gap: 14px;
            background: #15121e;
            border-radius: 20px;
            padding: 12px;
            border: 1px solid #312a41;
        }
        .cart-item-img {
            width: 70px;
            height: 70px;
            object-fit: cover;
            border-radius: 14px;
            background: #1f1b2b;
        }
        .cart-item-details {
            flex: 1;
        }
        .cart-item-title {
            font-size: 1.2rem;
            margin-bottom: 4px;
        }
        .cart-item-price {
            color: #dbba6c;
            font-weight: 600;
        }
        .cart-item-actions {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-top: 8px;
        }
        .cart-item-actions button {
            background: #2b2338;
            border: none;
            color: #e2d6ff;
            width: 28px;
            height: 28px;
            border-radius: 30px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.15s;
        }
        .cart-item-actions button:hover {
            background: #6d4b8c;
        }
        .cart-item-qty {
            font-weight: 600;
            min-width: 20px;
            text-align: center;
        }
        .remove-item-btn {
            background: none !important;
            color: #c97e7e !important;
            font-size: 1rem;
        }
        .cart-footer {
            padding: 20px;
            border-top: 1px solid #312842;
        }
        .cart-total {
            display: flex;
            justify-content: space-between;
            font-size: 1.4rem;
            font-weight: bold;
            margin-bottom: 20px;
        }
        .checkout-btn {
            background: #a2596b;
            width: 100%;
            padding: 14px;
            border: none;
            color: white;
            font-weight: bold;
            border-radius: 40px;
            font-size: 1rem;
            cursor: pointer;
            transition: 0.2s;
        }
        .checkout-btn:hover {
            background: #c97c6c;
            letter-spacing: 1px;
        }
        .empty-cart-msg {
            text-align: center;
            padding: 40px;
            color: #b1a5cb;
        }

        @media (max-width: 680px) {
            .hero-title {
                font-size: 2.5rem;
            }
            .container {
                padding: 0 18px;
            }
            .site-header {
                flex-direction: column;
                gap: 16px;
            }
            .cart-sidebar {
                width: 100%;
            }
        }
        button {
            cursor: pointer;
        }
    </style>
</head>
<body>

<div class="container">
    <header class="site-header">
        <div class="logo-area">
            <h1>Nocturna Atelier</h1>
            <p>✦ Strange masterpieces & dark romanticism ✦</p>
        </div>
        <div class="cart-icon" id="cartIcon">
            <i class="fas fa-shopping-cart"></i>
            <span class="cart-count" id="cartCount">0</span>
        </div>
    </header>

    <section class="hero">
        <div class="hero-title">Whispers of the Abyss</div>
        <div class="hero-sub">Original acrylic paintings & other witchy art — each piece carries the soul of shadow and light.</div>
        <button class="btn-primary" id="exploreBtn"><i class="fas fa-feather-alt"></i> Explore collection</button>
    </section>

    <h2 class="section-heading">✦ Cursed Gallery ✦</h2>
    <div id="productsContainer" class="products-grid"></div>

    <section class="about-section">
        <h2>✦ About the Atelier ✦</h2>
        <div class="about-text">
            <p>Nocturna Atelier was born from the whisper of midnight muses and the pull of the macabre. Each painting is an invocation — acrylics, charcoal, and raw emotion blended to evoke dreams, shadows, and the uncanny vally. Artist <strong>Jae Sheppard</strong> crafts every piece as a talisman for those who find beauty in darkness.</p>
            <p>Our gallery is a sanctuary for collectors who seek the uncanny, the romantic grotesque, and the poetic grotesque. All works are original, signed, and eventually we hope to soon ship worldwide in sustainable, ritual‑like packaging.</p>
            <div class="signature">— Memento Mori, Memento Vivere —</div>
        </div>
    </section>

    <!-- FIXED CONTACT SECTION: proper HTML fields -->
    <section class="contact-section">
        <h2>✦ Conjure a Message ✦</h2>
        <div class="contact-wrapper">
            <div class="contact-info">
                <p><i class="fas fa-envelope"></i> darkshadownexus666@gmail.com</p>
                <p><i class="fab fa-instagram"></i> @nocturna__atelier</p>
                <p><i class="fab fa-twitter"></i> @nocturna_art</p>
                <p><i class="fas fa-map-marker-alt"></i> Cobourg, ON. (by appointment)</p>
                <p><i class="fas fa-hourglass-half"></i> Responses within 3 moons</p>
            </div>
            <form class="contact-form" id="gothicContactForm">
                <input type="text" name="user_name" placeholder="Your name / shadow sigil" required>
                <input type="email" name="user_email" placeholder="Raven mail (email)" required>
                <textarea name="message" placeholder="Your message... (commission inquiries, dark blessings, or curses)" required></textarea>
                <button type="submit"><i class="fas fa-feather"></i> Send raven</button>
            </form>
        </div>
    </section>

    <footer>
        <p><i class="fas fa-skull"></i> Nocturna Atelier — Where darkness becomes art <i class="fas fa-ghost"></i></p>
        <p style="margin-top: 10px;">© 2026 | all shadows reserved | gothic paintings for the eternal collector | Artist Jae Sheppard</p>
    </footer>
</div>

<!-- CART OVERLAY + SIDEBAR -->
<div id="cartOverlay" class="cart-overlay"></div>
<div id="cartSidebar" class="cart-sidebar">
    <div class="cart-header">
        <h2><i class="fas fa-shopping-basket"></i> Raven Cart</h2>
        <button class="close-cart" id="closeCartBtn"><i class="fas fa-times"></i></button>
    </div>
    <div id="cartItemsList" class="cart-items-list">
        <div class="empty-cart-msg">🕯️ Your collection is empty ... add some dark beauty 🕸️</div>
    </div>
    <div class="cart-footer">
        <div class="cart-total">
            <span>Total Due:</span>
            <span id="cartTotalPrice">$0.00</span>
        </div>
        <button class="checkout-btn" id="checkoutBtn"><i class="fas fa-crown"></i> Claim Masterpiece</button>
    </div>
</div>

<script>
    // ----- CONFIG -----
    const IMAGE_PATH = "./images/";
    const CURRENCY = "CAD";

    const formatPrice = (amount) => {
        return new Intl.NumberFormat("en-CA", {
            style: "currency",
            currency: CURRENCY
        }).format(amount);
    };

    // ----- Painting Data (all unsold for now) -----
    const paintings = [
        { id: 1, name: "The Mug", price: 80, image: IMAGE_PATH + "TheMug.jpg", alt: "mystic forest painting", sold: false },
        { id: 2, name: "Paranoia Paradolia", price: 125, image: IMAGE_PATH + "parapara.jpg", alt: "dark floral with eyes and mouth", sold: false },
        { id: 3, name: "The Consumption", price: 90, image: IMAGE_PATH + "love.jpg", alt: "purple heart with mouth and eye", sold: false },
        { id: 4, name: "Mushy Madness", price: 199, image: IMAGE_PATH + "spookymush.jpg", alt: "mushrooms covered in eyes", sold: false },
        { id: 5, name: "Beauty is Pain", price: 250, image: IMAGE_PATH + "flowpow.jpg", alt: "spooky flowers covered in eyes", sold: false }
    ];

    let cart = [];

    const productsContainer = document.getElementById('productsContainer');
    const cartCountSpan = document.getElementById('cartCount');
    const cartSidebar = document.getElementById('cartSidebar');
    const cartOverlay = document.getElementById('cartOverlay');
    const cartItemsContainer = document.getElementById('cartItemsList');
    const cartTotalSpan = document.getElementById('cartTotalPrice');

    function syncCartWithSoldStatus() {
        let changed = false;
        const newCart = cart.filter(cartItem => {
            const painting = paintings.find(p => p.id === cartItem.id);
            if (!painting || painting.sold) {
                changed = true;
                return false;
            }
            return true;
        });
        if (changed) {
            cart = newCart;
            saveCartToLocal();
            updateCartUI();
        }
    }

    function updateCartUI() {
        const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
        cartCountSpan.innerText = totalItems;
        const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
        cartTotalSpan.innerText = formatPrice(total);
        renderCartSidebar();
    }

    function renderCartSidebar() {
        if (cart.length === 0) {
            cartItemsContainer.innerHTML = `<div class="empty-cart-msg">🕯️ Your collection is empty...</div>`;
            return;
        }
        cartItemsContainer.innerHTML = cart.map(item => `
            <div class="cart-item" data-id="${item.id}">
                <img class="cart-item-img" src="${item.image}" alt="${item.name}">
                <div class="cart-item-details">
                    <div class="cart-item-title">${item.name}</div>
                    <div class="cart-item-price">${formatPrice(item.price)}</div>
                    <div class="cart-item-actions">
                        <button class="decrement-qty" data-id="${item.id}">−</button>
                        <span class="cart-item-qty">${item.quantity}</span>
                        <button class="increment-qty" data-id="${item.id}">+</button>
                        <button class="remove-item-btn" data-id="${item.id}">🗑</button>
                    </div>
                </div>
            </div>
        `).join("");
    }

    cartItemsContainer.addEventListener('click', (e) => {
        const btn = e.target.closest('button');
        if (!btn) return;
        const id = parseInt(btn.dataset.id);
        if (btn.classList.contains('increment-qty')) updateQuantity(id, 1);
        if (btn.classList.contains('decrement-qty')) updateQuantity(id, -1);
        if (btn.classList.contains('remove-item-btn')) removeItemFromCart(id);
    });

    function updateQuantity(id, delta) {
        const item = cart.find(i => i.id === id);
        if (!item) return;
        item.quantity += delta;
        if (item.quantity <= 0) {
            cart = cart.filter(i => i.id !== id);
        }
        saveCartToLocal();
        updateCartUI();
    }

    function removeItemFromCart(id) {
        cart = cart.filter(i => i.id !== id);
        saveCartToLocal();
        updateCartUI();
    }

    function addToCart(product) {
        if (product.sold) {
            alert("⛧ This masterpiece has already been claimed (SOLD). ⛧");
            return false;
        }
        const existing = cart.find(i => i.id === product.id);
        if (existing) existing.quantity++;
        else cart.push({ ...product, quantity: 1 });
        saveCartToLocal();
        updateCartUI();
        const icon = document.getElementById('cartIcon');
        icon.style.transform = 'scale(1.1)';
        setTimeout(() => icon.style.transform = '', 200);
        return true;
    }

    function saveCartToLocal() {
        localStorage.setItem('gothicCart', JSON.stringify(cart));
    }

    function loadCartFromLocal() {
        const saved = localStorage.getItem('gothicCart');
        try {
            const parsed = JSON.parse(saved);
            if (Array.isArray(parsed)) cart = parsed;
        } catch {}
        syncCartWithSoldStatus();
    }

    function renderProducts() {
        productsContainer.innerHTML = paintings.map(p => {
            const soldOverlayHtml = p.sold ? `<div class="sold-overlay"><span>SOLD</span></div>` : '';
            const buttonHtml = p.sold 
                ? `<button class="add-to-cart" data-id="${p.id}" disabled><i class="fas fa-skull"></i> Sold Out</button>`
                : `<button class="add-to-cart" data-id="${p.id}"><i class="fas fa-crown"></i> Add to collection</button>`;
            return `
                <div class="product-card">
                    <div class="product-img-container">
                        <img class="product-img" src="${p.image}" alt="${p.alt}" loading="lazy">
                        ${soldOverlayHtml}
                    </div>
                    <div class="product-info">
                        <h3>${p.name}</h3>
                        <div class="product-price">${formatPrice(p.price)}</div>
                        ${buttonHtml}
                    </div>
                </div>
            `;
        }).join("");
        document.querySelectorAll('.add-to-cart:not(:disabled)').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const id = parseInt(btn.dataset.id);
                const product = paintings.find(p => p.id === id);
                if (product && !product.sold) addToCart(product);
                else if (product && product.sold) alert("⛧ This cursed piece is already sold. ⛧");
            });
        });
    }

    function openCart() {
        cartSidebar.classList.add('open');
        cartOverlay.classList.add('open');
        document.body.style.overflow = 'hidden';
    }
    function closeCart() {
        cartSidebar.classList.remove('open');
        cartOverlay.classList.remove('open');
        document.body.style.overflow = '';
    }

    // ----- EMAILJS INITIALIZATION -----
    (function() {
        emailjs.init("zxSozeOlDCzX8BNDZ");
    })();

    // ----- FIXED CONTACT FORM HANDLER (no nesting, proper async) -----
    const contactForm = document.getElementById('gothicContactForm');
    if (contactForm) {
        contactForm.addEventListener('submit', function(e) {
            e.preventDefault();
            const submitBtn = contactForm.querySelector('button[type="submit"]');
            const originalText = submitBtn.innerHTML;
            submitBtn.innerHTML = '<i class="fas fa-spinner fa-pulse"></i> Sending...';
            submitBtn.disabled = true;

            // Replace with your actual EmailJS credentials after creating account
            emailjs.sendForm('service_xih26ak', 'template_qkiur9h', this)
                .then(() => {
                    alert("🕸️ Raven delivered successfully! We'll respond within 3 dark moons. 🕸️");
                    contactForm.reset();
                })
                .catch((error) => {
                    console.error("EmailJS error:", error);
                    alert("⚠️ The raven was lost in the void. Please try again later or email us directly.");
                })
                .finally(() => {
                    submitBtn.innerHTML = originalText;
                    submitBtn.disabled = false;
                });
        });
    }

    document.getElementById('cartIcon').addEventListener('click', openCart);
    document.getElementById('closeCartBtn').addEventListener('click', closeCart);
    cartOverlay.addEventListener('click', closeCart);

    document.getElementById('checkoutBtn').addEventListener('click', () => {
        if (cart.length === 0) {
            alert("🖤 Your cart is empty. Add some dark treasures first.");
            return;
        }
        const total = cart.reduce((s, i) => s + i.price * i.quantity, 0);
        alert(`🦇 Total: ${formatPrice(total)}\n(⚰️ Ritual checkout would integrate Stripe/payment gateway.)`);
    });

    const exploreBtn = document.getElementById('exploreBtn');
    if (exploreBtn) {
        exploreBtn.addEventListener('click', () => {
            const galleryHeading = document.querySelector('.section-heading');
            if (galleryHeading) galleryHeading.scrollIntoView({ behavior: 'smooth', block: 'start' });
        });
    }

    document.addEventListener('keydown', (e) => {
        if (e.key === 'Escape') closeCart();
    });

    function init() {
        loadCartFromLocal();
        renderProducts();
        updateCartUI();
    }
    init();
</script>
</body>
</html>
