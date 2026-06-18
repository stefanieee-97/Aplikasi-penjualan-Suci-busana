<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Suci Busana - Tunik & Gamis</title>
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: #f8f4f0;
            color: #3e2c1b;
            padding-bottom: 80px;
        }

        /* Header */
        .header {
            background: #5e3c2b;
            color: #f5ede4;
            padding: 20px 16px 14px;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 10;
        }

        .header h1 {
            font-size: 28px;
            letter-spacing: 2px;
            font-weight: 600;
        }

        .header h1 i {
            margin-right: 8px;
            color: #e8c9b0;
        }

        .header p {
            font-size: 14px;
            opacity: 0.8;
            margin-top: 4px;
            letter-spacing: 1px;
        }

        /* Kategori */
        .category-tabs {
            display: flex;
            justify-content: center;
            gap: 12px;
            padding: 16px 12px 8px;
            background: #f8f4f0;
            flex-wrap: wrap;
        }

        .category-tabs button {
            background: #ede4db;
            border: none;
            padding: 10px 24px;
            border-radius: 30px;
            font-weight: 600;
            font-size: 15px;
            color: #3e2c1b;
            cursor: pointer;
            transition: 0.25s;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .category-tabs button i {
            font-size: 16px;
        }

        .category-tabs button.active {
            background: #5e3c2b;
            color: #f5ede4;
            box-shadow: 0 4px 10px rgba(94, 60, 43, 0.3);
        }

        .category-tabs button:hover {
            transform: translateY(-2px);
        }

        /* Produk Grid */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 16px 16px 0;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 24px 16px;
            margin-top: 8px;
        }

        .product-card {
            background: white;
            border-radius: 18px;
            overflow: hidden;
            box-shadow: 0 6px 18px rgba(0, 0, 0, 0.06);
            transition: 0.3s ease;
            display: flex;
            flex-direction: column;
            border: 1px solid #ede4db;
        }

        .product-card:hover {
            transform: translateY(-6px);
            box-shadow: 0 14px 28px rgba(94, 60, 43, 0.12);
        }

        .product-image {
            width: 100%;
            height: 220px;
            background: #e8ddd2;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 48px;
            color: #5e3c2b;
            background: linear-gradient(145deg, #ede4db, #dfd2c4);
        }

        .product-image i {
            filter: drop-shadow(2px 4px 6px rgba(0,0,0,0.1));
        }

        .product-info {
            padding: 16px 14px 18px;
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        .product-name {
            font-weight: 700;
            font-size: 17px;
            color: #2d1f14;
            margin-bottom: 4px;
        }

        .product-category {
            font-size: 13px;
            color: #8a6e5a;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .product-price {
            font-weight: 700;
            font-size: 19px;
            color: #5e3c2b;
            margin: 6px 0 12px;
        }

        .product-price small {
            font-weight: 400;
            font-size: 13px;
            color: #8a6e5a;
            margin-left: 4px;
        }

        .btn-order {
            background: #5e3c2b;
            color: white;
            border: none;
            padding: 10px 0;
            border-radius: 40px;
            font-weight: 600;
            font-size: 15px;
            cursor: pointer;
            transition: 0.2s;
            margin-top: auto;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .btn-order i {
            font-size: 14px;
        }

        .btn-order:hover {
            background: #4a2f21;
            transform: scale(1.02);
        }

        /* Keranjang Belanja (mini) */
        .cart-badge {
            position: fixed;
            bottom: 24px;
            right: 24px;
            background: #5e3c2b;
            color: white;
            padding: 14px 22px;
            border-radius: 60px;
            box-shadow: 0 8px 24px rgba(94, 60, 43, 0.4);
            display: flex;
            align-items: center;
            gap: 14px;
            cursor: pointer;
            transition: 0.25s;
            z-index: 20;
            border: none;
            font-size: 16px;
            font-weight: 600;
        }

        .cart-badge i {
            font-size: 22px;
        }

        .cart-badge:hover {
            transform: scale(1.05);
            background: #4a2f21;
        }

        .cart-count {
            background: #e8c9b0;
            color: #3e2c1b;
            border-radius: 40px;
            padding: 2px 12px;
            font-weight: 700;
            font-size: 16px;
        }

        /* Modal Keranjang */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(3px);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 100;
            opacity: 0;
            visibility: hidden;
            transition: 0.3s;
        }

        .modal-overlay.open {
            opacity: 1;
            visibility: visible;
        }

        .modal-content {
            background: #fcf9f6;
            border-radius: 32px;
            max-width: 480px;
            width: 92%;
            padding: 28px 24px 30px;
            box-shadow: 0 30px 60px rgba(0,0,0,0.3);
            transform: scale(0.9);
            transition: 0.25s;
            max-height: 80vh;
            overflow-y: auto;
        }

        .modal-overlay.open .modal-content {
            transform: scale(1);
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid #ede4db;
            padding-bottom: 16px;
            margin-bottom: 18px;
        }

        .modal-header h2 {
            font-size: 24px;
            color: #3e2c1b;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .modal-close {
            background: none;
            border: none;
            font-size: 28px;
            cursor: pointer;
            color: #8a6e5a;
            transition: 0.2s;
            padding: 0 6px;
        }

        .modal-close:hover {
            color: #3e2c1b;
            transform: rotate(90deg);
        }

        .cart-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 12px 0;
            border-bottom: 1px solid #ede4db;
        }

        .cart-item-info {
            display: flex;
            flex-direction: column;
        }

        .cart-item-name {
            font-weight: 600;
            font-size: 16px;
        }

        .cart-item-price {
            font-size: 14px;
            color: #5e3c2b;
        }

        .cart-item-qty {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .cart-item-qty button {
            background: #ede4db;
            border: none;
            width: 30px;
            height: 30px;
            border-radius: 40px;
            font-size: 18px;
            font-weight: 700;
            cursor: pointer;
            transition: 0.15s;
            color: #3e2c1b;
        }

        .cart-item-qty button:hover {
            background: #d6c6b8;
        }

        .cart-item-qty span {
            font-weight: 600;
            min-width: 24px;
            text-align: center;
        }

        .cart-total {
            margin-top: 20px;
            font-size: 20px;
            font-weight: 700;
            text-align: right;
            color: #3e2c1b;
            border-top: 2px solid #ede4db;
            padding-top: 16px;
        }

        .btn-checkout {
            background: #5e3c2b;
            color: white;
            border: none;
            padding: 14px;
            border-radius: 60px;
            width: 100%;
            font-weight: 700;
            font-size: 18px;
            margin-top: 16px;
            cursor: pointer;
            transition: 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .btn-checkout:hover {
            background: #4a2f21;
        }

        .empty-cart {
            text-align: center;
            color: #8a6e5a;
            padding: 30px 0;
            font-size: 16px;
        }

        .empty-cart i {
            font-size: 48px;
            margin-bottom: 12px;
            opacity: 0.5;
        }

        /* Responsive */
        @media (max-width: 600px) {
            .product-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 16px;
            }
            .product-image {
                height: 160px;
                font-size: 36px;
            }
            .header h1 {
                font-size: 22px;
            }
            .category-tabs button {
                padding: 8px 16px;
                font-size: 13px;
            }
            .cart-badge {
                padding: 10px 18px;
                font-size: 14px;
                bottom: 16px;
                right: 16px;
            }
        }
    </style>
</head>
<body>

    <!-- HEADER -->
    <header class="header">
        <h1><i class="fas fa-tshirt"></i> Suci Busana</h1>
        <p>Tunik & Gamis Elegan • Busana Muslimah</p>
    </header>

    <!-- Kategori -->
    <div class="category-tabs" id="categoryTabs">
        <button class="active" data-category="all"><i class="fas fa-th"></i> Semua</button>
        <button data-category="tunik"><i class="fas fa-blouse"></i> Tunik</button>
        <button data-category="gamis"><i class="fas fa-dress"></i> Gamis</button>
    </div>

    <!-- Daftar Produk -->
    <div class="container">
        <div class="product-grid" id="productGrid"></div>
    </div>

    <!-- Keranjang (Floating) -->
    <button class="cart-badge" id="cartBadge">
        <i class="fas fa-shopping-bag"></i>
        <span>Keranjang</span>
        <span class="cart-count" id="cartCount">0</span>
    </button>

    <!-- Modal Keranjang -->
    <div class="modal-overlay" id="cartModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2><i class="fas fa-shopping-bag"></i> Keranjang</h2>
                <button class="modal-close" id="closeCart">&times;</button>
            </div>
            <div id="cartItemsContainer">
                <!-- diisi JS -->
            </div>
            <div class="cart-total" id="cartTotal">Total: Rp 0</div>
            <button class="btn-checkout" id="checkoutBtn">
                <i class="fas fa-check-circle"></i> Pesan Sekarang
            </button>
        </div>
    </div>

    <script>
        // ================= DATA PRODUK =================
        const products = [
            // TUNIK
            { id: 1, name: 'Tunik Floral Ankara', category: 'tunik', price: 185000, icon: 'fa-tshirt' },
            { id: 2, name: 'Tunik Batik Modern', category: 'tunik', price: 210000, icon: 'fa-palette' },
            { id: 3, name: 'Tunik Linen Premium', category: 'tunik', price: 239000, icon: 'fa-leaf' },
            { id: 4, name: 'Tunik Polos Katun', category: 'tunik', price: 165000, icon: 'fa-cloud' },
            { id: 5, name: 'Tunik A-line', category: 'tunik', price: 199000, icon: 'fa-arrow-right' },
            // GAMIS
            { id: 6, name: 'Gamis Dubai Elegan', category: 'gamis', price: 325000, icon: 'fa-star' },
            { id: 7, name: 'Gamis Pashmina Ceruty', category: 'gamis', price: 289000, icon: 'fa-moon' },
            { id: 8, name: 'Gamis Brokat Mewah', category: 'gamis', price: 410000, icon: 'fa-crown' },
            { id: 9, name: 'Gamis Maxi Syar\'i', category: 'gamis', price: 269000, icon: 'fa-umbrella' },
            { id: 10, name: 'Gamis Casual Flanel', category: 'gamis', price: 235000, icon: 'fa-heart' },
        ];

        // ================= STATE =================
        let cart = []; // [{ id, quantity }]
        let currentCategory = 'all';

        // ================= DOM REFS =================
        const productGrid = document.getElementById('productGrid');
        const categoryTabs = document.getElementById('categoryTabs');
        const cartBadge = document.getElementById('cartBadge');
        const cartCount = document.getElementById('cartCount');
        const cartModal = document.getElementById('cartModal');
        const closeCart = document.getElementById('closeCart');
        const cartItemsContainer = document.getElementById('cartItemsContainer');
        const cartTotal = document.getElementById('cartTotal');
        const checkoutBtn = document.getElementById('checkoutBtn');

        // ================= RENDER PRODUK =================
        function renderProducts(category = 'all') {
            const filtered = category === 'all' ? products : products.filter(p => p.category === category);
            if (filtered.length === 0) {
                productGrid.innerHTML = `<p style="grid-column:1/-1; text-align:center; padding:40px; color:#8a6e5a;">
                    <i class="fas fa-box-open" style="display:block; font-size:32px; margin-bottom:10px;"></i>
                    Belum ada produk di kategori ini.
                </p>`;
                return;
            }

            productGrid.innerHTML = filtered.map(product => {
                // cek apakah produk ada di cart
                const cartItem = cart.find(item => item.id === product.id);
                const qty = cartItem ? cartItem.quantity : 0;
                return `
                    <div class="product-card" data-id="${product.id}">
                        <div class="product-image">
                            <i class="fas ${product.icon}"></i>
                        </div>
                        <div class="product-info">
                            <div class="product-name">${product.name}</div>
                            <div class="product-category">
                                <i class="fas ${product.category === 'tunik' ? 'fa-blouse' : 'fa-dress'}"></i>
                                ${product.category === 'tunik' ? 'Tunik' : 'Gamis'}
                            </div>
                            <div class="product-price">
                                Rp ${product.price.toLocaleString('id-ID')}
                                <small>/ pcs</small>
                            </div>
                            <button class="btn-order add-to-cart" data-id="${product.id}" data-name="${product.name}" data-price="${product.price}">
                                <i class="fas fa-cart-plus"></i> Tambah
                                ${qty > 0 ? `<span style="background:#e8c9b0; color:#3e2c1b; border-radius:20px; padding:0 10px; font-size:13px; margin-left:4px;">${qty}</span>` : ''}
                            </button>
                        </div>
                    </div>
                `;
            }).join('');

            // Attach event listener ke tombol "Tambah"
            document.querySelectorAll('.add-to-cart').forEach(btn => {
                btn.addEventListener('click', function(e) {
                    e.stopPropagation();
                    const id = parseInt(this.dataset.id);
                    const name = this.dataset.name;
                    const price = parseInt(this.dataset.price);
                    addToCart(id, name, price);
                });
            });
        }

        // ================= KATEGORI =================
        categoryTabs.addEventListener('click', function(e) {
            const btn = e.target.closest('button');
            if (!btn) return;
            const category = btn.dataset.category;
            if (!category) return;

            // update aktif
            document.querySelectorAll('.category-tabs button').forEach(b => b.classList.remove('active'));
            btn.classList.add('active');

            currentCategory = category;
            renderProducts(category);
        });

        // ================= KERANJANG =================
        function addToCart(id, name, price) {
            const existing = cart.find(item => item.id === id);
            if (existing) {
                existing.quantity += 1;
            } else {
                cart.push({ id, name, price, quantity: 1 });
            }
            updateCartUI();
            renderProducts(currentCategory); // refresh badge quantity di tombol
            // animasi kecil
            cartBadge.style.transform = 'scale(1.15)';
            setTimeout(() => cartBadge.style.transform = 'scale(1)', 150);
        }

        function removeFromCart(id) {
            const index = cart.findIndex(item => item.id === id);
            if (index !== -1) {
                if (cart[index].quantity > 1) {
                    cart[index].quantity -= 1;
                } else {
                    cart.splice(index, 1);
                }
            }
            updateCartUI();
            renderProducts(currentCategory);
        }

        function updateCartUI() {
            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            cartCount.textContent = totalItems;

            // Render isi keranjang di modal
            if (cart.length === 0) {
                cartItemsContainer.innerHTML = `
                    <div class="empty-cart">
                        <i class="fas fa-shopping-bag"></i>
                        <p>Keranjang kosong, yuk belanja!</p>
                    </div>
                `;
                cartTotal.textContent = 'Total: Rp 0';
                return;
            }

            let html = '';
            let total = 0;
            cart.forEach(item => {
                const subtotal = item.price * item.quantity;
                total += subtotal;
                html += `
                    <div class="cart-item">
                        <div class="cart-item-info">
                            <span class="cart-item-name">${item.name}</span>
                            <span class="cart-item-price">Rp ${item.price.toLocaleString('id-ID')}</span>
                        </div>
                        <div class="cart-item-qty">
                            <button class="qty-decrease" data-id="${item.id}">−</button>
                            <span>${item.quantity}</span>
                            <button class="qty-increase" data-id="${item.id}">+</button>
                        </div>
                    </div>
                `;
            });

            cartItemsContainer.innerHTML = html;
            cartTotal.textContent = `Total: Rp ${total.toLocaleString('id-ID')}`;

            // Event listener untuk tombol + dan - di modal
            document.querySelectorAll('.qty-increase').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = parseInt(this.dataset.id);
                    const product = products.find(p => p.id === id);
                    if (product) addToCart(id, product.name, product.price);
                });
            });
            document.querySelectorAll('.qty-decrease').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = parseInt(this.dataset.id);
                    removeFromCart(id);
                });
            });
        }

        // ================= MODAL =================
        function openCartModal() {
            cartModal.classList.add('open');
            updateCartUI(); // refresh isi
        }

        function closeCartModal() {
            cartModal.classList.remove('open');
        }

        cartBadge.addEventListener('click', openCartModal);
        closeCart.addEventListener('click', closeCartModal);
        cartModal.addEventListener('click', function(e) {
            if (e.target === this) closeCartModal();
        });

        // ================= CHECKOUT =================
        checkoutBtn.addEventListener('click', function() {
            if (cart.length === 0) {
                alert('Keranjang masih kosong. Yuk tambahkan produk!');
                return;
            }

            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            const totalPrice = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const itemNames = cart.map(item => `${item.name} (${item.quantity}x)`).join(', ');

            const confirmation = confirm(
                `🛍️ Suci Busana\n\n` +
                `Pesanan: ${itemNames}\n` +
                `Total: Rp ${totalPrice.toLocaleString('id-ID')}\n\n` +
                `Klik OK untuk melanjutkan ke WhatsApp.`
            );

            if (confirmation) {
                const phone = '6281234567890'; // ganti dengan nomor WhatsApp toko
                const message = `Halo Suci Busana, saya ingin memesan:\n${itemNames}\nTotal: Rp ${totalPrice.toLocaleString('id-ID')}`;
                const url = `https://wa.me/${phone}?text=${encodeURIComponent(message)}`;
                window.open(url, '_blank');
                // Kosongkan keranjang setelah checkout
                cart = [];
                updateCartUI();
                renderProducts(currentCategory);
                closeCartModal();
            }
        });

        // ================= INIT =================
        renderProducts('all');
        updateCartUI();
    </script>
</body>
</html>
