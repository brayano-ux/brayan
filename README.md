

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ShopVerse - Votre Destination Shopping Premium</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <style>
        :root {
            --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            --secondary-gradient: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            --accent-color: #4ecdc4;
            --warning-color: #ff6b6b;
            --success-color: #2ecc71;
            --text-light: rgba(255, 255, 255, 0.9);
            --glass-bg: rgba(255, 255, 255, 0.1);
            --glass-border: rgba(255, 255, 255, 0.2);
            --shadow-soft: 0 8px 32px rgba(0, 0, 0, 0.1);
            --shadow-strong: 0 20px 60px rgba(0, 0, 0, 0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: var(--primary-gradient);
            min-height: 100vh;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* Header Premium */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: var(--glass-bg);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid var(--glass-border);
            z-index: 1000;
            padding: 1rem 2rem;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        header.scrolled {
            background: rgba(255, 255, 255, 0.15);
            box-shadow: var(--shadow-soft);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1400px;
            margin: 0 auto;
        }

        .logo {
            font-size: 2.2rem;
            font-weight: 800;
            background: var(--secondary-gradient);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 30px rgba(255, 107, 107, 0.5);
            letter-spacing: -0.02em;
        }

        .nav-links {
            display: flex;
            gap: 2.5rem;
            list-style: none;
            align-items: center;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            font-weight: 600;
            font-size: 0.95rem;
            transition: all 0.3s ease;
            position: relative;
            padding: 0.5rem 1rem;
            border-radius: 25px;
        }

        .nav-links a:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateY(-2px);
            text-shadow: 0 5px 15px rgba(255, 255, 255, 0.4);
        }

        .nav-search {
            display: flex;
            align-items: center;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 25px;
            padding: 0.5rem 1rem;
            border: 1px solid var(--glass-border);
            transition: all 0.3s ease;
        }

        .nav-search:focus-within {
            background: rgba(255, 255, 255, 0.15);
            transform: scale(1.05);
        }

        .nav-search input {
            background: none;
            border: none;
            color: white;
            outline: none;
            padding: 0.25rem 0.5rem;
            width: 400px;
            height: 30px;
            font-size: 0.9rem;
        }

        .nav-search input::placeholder {
            color: rgba(255, 255, 255, 0.6);
        }

        /* Hero Section Premium */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background:
                radial-gradient(circle at 20% 80%, rgba(255, 107, 107, 0.3) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(76, 205, 196, 0.3) 0%, transparent 50%),
                radial-gradient(circle at 40% 40%, rgba(118, 75, 162, 0.2) 0%, transparent 50%);
            animation: heroFloat 8s ease-in-out infinite;
        }

        @keyframes heroFloat {

            0%,
            100% {
                transform: translateY(0) rotate(0deg);
                opacity: 0.8;
            }

            50% {
                transform: translateY(-20px) rotate(2deg);
                opacity: 1;
            }
        }

        .hero-content {
            z-index: 2;
            color: white;
            max-width: 800px;
            padding: 0 2rem;
        }

        .hero h1 {
            font-size: clamp(2.5rem, 8vw, 5rem);
            margin-bottom: 1.5rem;
            background: linear-gradient(45deg, #fff, #f0f0f0, #4ecdc4);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: heroGlow 3s ease-in-out infinite alternate;
            font-weight: 800;
            letter-spacing: -0.03em;
        }

        @keyframes heroGlow {
            from {
                filter: drop-shadow(0 0 20px rgba(255, 255, 255, 0.5));
            }

            to {
                filter: drop-shadow(0 0 40px rgba(76, 205, 196, 0.8));
            }
        }

        .hero-subtitle {
            font-size: 1.3rem;
            margin-bottom: 2.5rem;
            opacity: 0.9;
            font-weight: 400;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        .hero-stats {
            display: flex;
            justify-content: center;
            gap: 3rem;
            margin: 2rem 0;
            flex-wrap: wrap;
        }

        .stat-item {
            text-align: center;
        }

        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            color: var(--accent-color);
            display: block;
        }

        .stat-label {
            font-size: 0.9rem;
            opacity: 0.8;
            margin-top: 0.5rem;
        }

        .hero-cta {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 3rem;
        }

        .cta-button {
            padding: 1.2rem 2.5rem;
            background: var(--secondary-gradient);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 700;
            font-size: 1.1rem;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            position: relative;
            overflow: hidden;
            border: 2px solid transparent;
        }

        .cta-button.secondary {
            background: transparent;
            border: 2px solid rgba(255, 255, 255, 0.3);
            backdrop-filter: blur(10px);
        }

        .cta-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: left 0.6s ease;
        }

        .cta-button:hover::before {
            left: 100%;
        }

        .cta-button:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.4);
        }

        /* Panier Premium */
        .cart-icon {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: var(--secondary-gradient);
            width: 70px;
            height: 70px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.8rem;
            cursor: pointer;
            z-index: 1001;
            box-shadow: var(--shadow-strong);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            animation: cartPulse 2s infinite;
        }

        @keyframes cartPulse {

            0%,
            100% {
                box-shadow: var(--shadow-strong), 0 0 0 0 rgba(255, 107, 107, 0.7);
            }

            50% {
                box-shadow: var(--shadow-strong), 0 0 0 10px rgba(255, 107, 107, 0);
            }
        }

        .cart-icon:hover {
            transform: scale(1.1) rotate(5deg);
            box-shadow: 0 25px 60px rgba(0, 0, 0, 0.4);
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background: var(--warning-color);
            color: white;
            border-radius: 50%;
            width: 28px;
            height: 28px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.85rem;
            font-weight: 700;
            box-shadow: 0 4px 12px rgba(255, 107, 107, 0.4);
            animation: countBounce 0.5s ease;
        }

        @keyframes countBounce {

            0%,
            100% {
                transform: scale(1);
            }

            50% {
                transform: scale(1.3);
            }
        }

        /* Sidebar Panier Premium */
        .cart-sidebar {
            position: fixed;
            top: 0;
            right: -450px;
            width: 450px;
            height: 100vh;
            background: var(--glass-bg);
            backdrop-filter: blur(30px);
            border-left: 1px solid var(--glass-border);
            z-index: 1002;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            overflow-y: auto;
            padding: 2rem;
        }

        .cart-sidebar.open {
            right: 0;
            box-shadow: -20px 0 60px rgba(0, 0, 0, 0.3);
        }

        /* Sections Produits Premium */
        .categories {
            padding: 6rem 2rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }

        .section-title {
            font-size: clamp(2.5rem, 6vw, 4rem);
            color: white;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, #fff, #e0e0e0, var(--accent-color));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: 800;
            letter-spacing: -0.02em;
        }

        .section-subtitle {
            font-size: 1.2rem;
            color: var(--text-light);
            max-width: 600px;
            margin: 0 auto;
        }

        .category-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2.5rem;
            margin-bottom: 5rem;
        }

        .category-card {
            background: var(--glass-bg);
            backdrop-filter: blur(25px);
            border-radius: 25px;
            padding: 2.5rem;
            text-align: center;
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid var(--glass-border);
            position: relative;
            overflow: hidden;
            cursor: pointer;
        }

        .category-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: conic-gradient(from 0deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            opacity: 0;
            transition: all 0.6s ease;
            animation: rotate 10s linear infinite;
        }

        @keyframes rotate {
            from {
                transform: rotate(0deg);
            }

            to {
                transform: rotate(360deg);
            }
        }

        .category-card:hover::before {
            opacity: 1;
        }

        .category-card:hover {
            transform: translateY(-15px) scale(1.03);
            box-shadow: var(--shadow-strong);
            border-color: rgba(255, 255, 255, 0.4);
        }

        .category-icon {
            font-size: 4.5rem;
            margin-bottom: 1.5rem;
            background: var(--secondary-gradient);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 15px rgba(255, 107, 107, 0.5));
            position: relative;
            z-index: 2;
        }

        .category-card h3 {
            color: white;
            font-size: 1.8rem;
            margin-bottom: 1rem;
            font-weight: 700;
            position: relative;
            z-index: 2;
        }

        .category-card p {
            color: var(--text-light);
            line-height: 1.7;
            margin-bottom: 2rem;
            font-size: 1.05rem;
            position: relative;
            z-index: 2;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 2.5rem;
        }

        .product-card {
            background: rgba(255, 255, 255, 0.08);
            border-radius: 20px;
            padding: 1.5rem;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid rgba(255, 255, 255, 0.1);
            cursor: pointer;
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(10px);
        }

        .product-card:hover {
            background: rgba(255, 255, 255, 0.15);
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.2);
        }

        .product-image {
            width: 100%;
            height: 180px;
            background: var(--primary-gradient);
            border-radius: 15px;
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3.5rem;
            color: white;
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            position: relative;
            overflow: hidden;
        }

        .product-image::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, rgba(255, 107, 107, 0.1), rgba(76, 205, 196, 0.1));
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .product-card:hover .product-image::before {
            opacity: 1;
        }

        .product-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background: var(--warning-color);
            color: white;
            padding: 0.3rem 0.8rem;
            border-radius: 15px;
            font-size: 0.75rem;
            font-weight: 600;
            text-transform: uppercase;
        }

        .product-info {
            position: relative;
            z-index: 2;
        }

        .product-name {
            color: white;
            font-weight: 700;
            font-size: 1.1rem;
            margin-bottom: 0.5rem;
        }

        .product-description {
            color: rgba(255, 255, 255, 0.7);
            font-size: 0.9rem;
            margin-bottom: 1rem;
            line-height: 1.5;
        }

        .product-price-section {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
        }

        .product-price {
            color: var(--accent-color);
            font-size: 1.4rem;
            font-weight: 800;
        }

        .product-old-price {
            color: rgba(255, 255, 255, 0.5);
            text-decoration: line-through;
            font-size: 1rem;
            margin-left: 0.5rem;
        }

        .product-rating {
            display: flex;
            align-items: center;
            gap: 0.3rem;
            color: #ffd700;
            font-size: 0.9rem;
        }

        .quick-add-btn {
            position: absolute;
            bottom: 15px;
            right: 15px;
            background: var(--secondary-gradient);
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 25px;
            font-size: 0.9rem;
            font-weight: 600;
            cursor: pointer;
            opacity: 0;
            transform: translateY(15px) scale(0.8);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .product-card:hover .quick-add-btn {
            opacity: 1;
            transform: translateY(0) scale(1);
        }

        .quick-add-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 12px 35px rgba(0, 0, 0, 0.3);
        }

        /* Cart Items Premium */
        .cart-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1.5rem;
            background: rgba(255, 255, 255, 0.08);
            border-radius: 15px;
            margin-bottom: 1rem;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .cart-item:hover {
            background: rgba(255, 255, 255, 0.12);
            transform: translateY(-2px);
        }

        .cart-item-image {
            width: 70px;
            height: 70px;
            background: var(--primary-gradient);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            background-size: cover;
            background-position: center;
        }

        /* Trust Indicators */
        .trust-section {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            margin: 4rem 0;
            padding: 3rem 2rem;
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .trust-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            text-align: center;
        }

        .trust-item {
            color: white;
            padding: 1.5rem;
        }

        .trust-icon {
            font-size: 3rem;
            color: var(--accent-color);
            margin-bottom: 1rem;
        }

        .trust-title {
            font-size: 1.2rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
        }

        /* Newsletter */
        .newsletter-section {
            background: var(--glass-bg);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 3rem 2rem;
            text-align: center;
            margin: 4rem 0;
            border: 1px solid var(--glass-border);
        }

        .newsletter-form {
            display: flex;
            gap: 1rem;
            max-width: 400px;
            margin: 2rem auto 0;
        }

        .newsletter-input {
            flex: 1;
            padding: 1rem;
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 25px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1rem;
        }

        .newsletter-btn {
            background: var(--secondary-gradient);
            color: white;
            border: none;
            padding: 1rem 2rem;
            border-radius: 25px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        /* Footer Premium */
        footer {
            background: linear-gradient(135deg, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.6));
            backdrop-filter: blur(20px);
            padding: 4rem 2rem 2rem;
            color: white;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            margin-top: 4rem;
        }

        .footer-content {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 3rem;
        }

        .footer-section h4 {
            color: var(--accent-color);
            margin-bottom: 1rem;
            font-size: 1.2rem;
            font-weight: 700;
        }

        .footer-links {
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .footer-links a {
            color: var(--text-light);
            text-decoration: none;
            transition: all 0.3s ease;
            padding: 0.3rem 0;
        }

        .footer-links a:hover {
            color: var(--accent-color);
            transform: translateX(5px);
        }

        .social-icons {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }

        .social-icon {
            width: 50px;
            height: 50px;
            background: var(--glass-bg);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.3rem;
            transition: all 0.3s ease;
            border: 1px solid var(--glass-border);
        }

        .social-icon:hover {
            background: var(--secondary-gradient);
            transform: translateY(-3px);
        }

        .footer-bottom {
            text-align: center;
            margin-top: 3rem;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: rgba(255, 255, 255, 0.7);
        }

        /* Notifications Premium */
        .notification {
            position: fixed;
            top: 100px;
            right: 20px;
            background: var(--glass-bg);
            backdrop-filter: blur(20px);
            border: 1px solid var(--glass-border);
            color: white;
            padding: 1.5rem 2rem;
            border-radius: 15px;
            z-index: 10000;
            animation: notificationSlide 0.5s ease;
            max-width: 350px;
            box-shadow: var(--shadow-strong);
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .notification i {
            font-size: 1.2rem;
        }

        /* Cart Overlay */
        .cart-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 1001;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
        }

        .cart-overlay.open {
            opacity: 1;
            visibility: visible;
        }

        /* Cart Header */
        .cart-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .cart-title {
            color: white;
            font-size: 1.5rem;
            font-weight: 700;
            margin: 0;
        }

        .cart-close {
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
            padding: 0.5rem;
            border-radius: 50%;
            transition: all 0.3s ease;
        }

        .cart-close:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: scale(1.1);
        }

        /* Cart Total */
        .cart-total {
            margin-top: 2rem;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .clear-cart-btn {
            background: rgba(255, 107, 107, 0.2);
            color: white;
            border: 1px solid rgba(255, 107, 107, 0.5);
            padding: 0.8rem 1.5rem;
            border-radius: 25px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            margin-bottom: 1rem;
            width: 100%;
        }

        .clear-cart-btn:hover {
            background: rgba(255, 107, 107, 0.3);
            transform: translateY(-2px);
        }

        .cart-total-price {
            color: var(--accent-color);
            font-size: 1.3rem;
            font-weight: 700;
            text-align: center;
            margin: 1rem 0;
        }

        .checkout-btn {
            background: var(--secondary-gradient);
            color: white;
            border: none;
            padding: 1rem 2rem;
            border-radius: 25px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
        }

        .checkout-btn:hover:not(:disabled) {
            transform: translateY(-3px);
            box-shadow: 0 12px 35px rgba(0, 0, 0, 0.3);
        }

        .checkout-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        /* Order Modal */
        .order-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 10000;
            display: none;
            align-items: center;
            justify-content: center;
            padding: 2rem;
        }

        .order-modal.open {
            display: flex;
        }

        .order-modal-content {
            background: var(--glass-bg);
            backdrop-filter: blur(30px);
            border: 1px solid var(--glass-border);
            border-radius: 25px;
            padding: 3rem;
            max-width: 600px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
        }

        /* Form Styles */
        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            color: white;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 1rem;
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 15px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--accent-color);
            background: rgba(255, 255, 255, 0.15);
        }

        .form-group input::placeholder,
        .form-group textarea::placeholder {
            color: rgba(255, 255, 255, 0.6);
        }

        .form-actions {
            display: flex;
            gap: 1rem;
            margin-top: 2rem;
        }

        .form-btn {
            flex: 1;
            padding: 1rem 2rem;
            border: none;
            border-radius: 25px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .btn-cancel {
            background: rgba(255, 255, 255, 0.1);
            color: white;
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        .btn-cancel:hover {
            background: rgba(255, 255, 255, 0.2);
        }

        .btn-confirm {
            background: var(--secondary-gradient);
            color: white;
        }

        .btn-confirm:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
        }

        /* Cart Item Styles */
        .cart-item-info {
            flex: 1;
        }

        .cart-item-name {
            color: white;
            font-weight: 700;
            font-size: 1rem;
            margin-bottom: 0.3rem;
        }

        .quantity-btn {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.3);
            color: white;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .quantity-btn:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: scale(1.1);
        }

        .quantity-value {
            color: white;
            font-weight: 600;
            min-width: 30px;
            text-align: center;
        }

        .remove-item {
            background: rgba(255, 107, 107, 0.2);
            border: 1px solid rgba(255, 107, 107, 0.5);
            color: #ff6b6b;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .remove-item:hover {
            background: rgba(255, 107, 107, 0.3);
            transform: scale(1.1);
        }

        @keyframes notificationSlide {
            from {
                transform: translateX(100%);
                opacity: 0;
            }

            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        .notification.success {
            border-left: 4px solid var(--success-color);
        }

        .notification.error {
            border-left: 4px solid var(--warning-color);
        }

        /* Responsive Premium */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .hero-stats {
                gap: 2rem;
            }

            .category-grid {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .cart-sidebar {
                width: 100vw;
                right: -100vw;
            }

            .hero-cta {
                flex-direction: column;
                align-items: center;
            }

            .newsletter-form {
                flex-direction: column;
            }

            .product-grid {
                grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            }
        }

        /* Animations d'entrée */
        .animate-in {
            opacity: 0;
            transform: translateY(50px);
            animation: slideInUp 0.8s ease forwards;
        }

        @keyframes slideInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Loading States */
        .loading {
            position: relative;
            overflow: hidden;
        }
        .loading::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            animation: shimmer 1.5s infinite;
        }

        .logo {
            padding: 10px;
            font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        }

        @keyframes shimmer {
            100% {
                left: 100%;
            }
        }

        h1 {
            margin-top: 100px;
        }

        @media(max-width: 768px) {
            .logo {
                text-align: left;
            }

            input{
                height: 20px!important;
                width: 170px!important;
            }

            h1 {
                margin-top: 150px;
            }

            .bars {
                display: block !important;
                position: relative;
                top: 0px;
                right: 0px;
                font-size: 25px;
                cursor: pointer;
                width: 40px;
                height: 50px;
                border-radius: 50%;
                padding: 10px;
                margin: 10px;
            }

            .bars:hover {
                background: rgba(0, 0, 255, 0.192);
                transform: scale(1.1);
            }

            .navbar {
                align-items: center;
            }
        }

        .categories {
            background: transparent;
        }

        .bars {
            display: none;
        }
        
    </style>
</head>

<body>
    <header id="header">
        <nav class="navbar">
            <div id="entete" style="display: flex; flex-wrap: wrap;">
                <div class="logo">Brayano</div>
                <div class="nav-search">
                    <i class="fas fa-search"></i>
                    <input class='int' type="text" placeholder="Rechercher des produits...">
                </div>
            </div>
            <div class="bars" id="bars">
                <i class='fas fa-bars'></i>
            </div>
            <ul id="block" class="nav-links">
                <li><a href="#accueil"><i class="fas fa-home"></i> Accueil</a></li>
                <li><a href="#categories"><i class="fas fa-th-large"></i> Catégories</a></li>
                <li><a href="#promo"><i class="fas fa-tags" id="promo"></i> Promos</a></li>
                <li><a href="#contact"><i class="fas fa-envelope"></i> Contact</a></li>
            </ul>
        </nav>
    </header>
    <script>
        il = document.getElementById('bars');
        document.getElementById('bars').addEventListener('click', function () {
            const menu = document.getElementById('block');
            if (menu.style.display === 'block') {
                menu.style.display = 'none';
                                il.innerHTML='<i class="fas fa-bars"></i>'

            } else {
                il.innerHTML = '<i class="fa-solid fa-xmark"></i>'
                menu.style.display = 'block';
            }
        });
       document.getElementById('promo').addEventListener('click', function () {
    const div = document.createElement('div');
    div.classList.add('element'); 
    div.innerHTML = `
        <div style="padding: 15px; background: #f9f9f9; border: 1px solid #ddd; border-radius: 8px; margin-top: 10px;">
            <h3 style="color: #555; font-size: 16px; text-align:center;">
                Vous n'avez pas de promotion pour le moment 🚫
            </h3>
        </div>
    `;

    document.getElementById('promos').appendChild(div);
});

    </script>

    <section id="accueil" class="hero">
        <div class="hero-content">
            <h1>Shopping Premium Redéfini</h1>
            <p class="hero-subtitle">Découvrez une expérience d'achat unique avec des produits soigneusement
                sélectionnés et une livraison express partout au Cameroun</p>

            <div class="hero-stats">
                <div class="stat-item">
                    <span class="stat-number">10K+</span>
                    <span class="stat-label">Clients Satisfaits</span>
                </div>
                <div class="stat-item">
                    <span class="stat-number">500+</span>
                    <span class="stat-label">Produits Premium</span>
                </div>
                <div class="stat-item">
                    <span class="stat-number">24h</span>
                    <span class="stat-label">Livraison Express</span>
                </div>
            </div>

            <div class="hero-cta">
                <a href="#categories" style="z-index: 9999;top: -5px;" class="cta-button">
                    <i class="fas fa-shopping-bag"></i>
                    Explorer la Collection
                </a>
                <!-- <a href="#promos" id="secondaire" class="cta-button secondary">
                    <i class="fas fa-percent"></i>
                    Offres Spéciales
                </a> -->
            </div>
        </div>
    </section>

    <!-- Trust Indicators -->
    <div class="categories">
        <div class="trust-section animate-in">
            <div class="trust-grid">
                <div class="trust-item">
                    <div class="trust-icon"><i class="fas fa-shipping-fast"></i></div>
                    <div class="trust-title">Livraison Express</div>
                    <p>Livraison  en 24h à Douala et Yaoundé</p>
                </div>
                <div class="trust-item">
                    <div class="trust-icon"><i class="fas fa-shield-alt"></i></div>
                    <div class="trust-title">Paiement Sécurisé</div>
                    <p>Transactions 100% sécurisées et garanties</p>
                </div>
                <div class="trust-item">
                    <div class="trust-icon"><i class="fas fa-undo"></i></div>
                    <div class="trust-title">Retour Gratuit</div>
                    <p>Retour sous 30 jours sans frais supplémentaires</p>
                </div>
                <div class="trust-item">
                    <div class="trust-icon"><i class="fas fa-headset"></i></div>
                    <div class="trust-title">Support 24/7</div>
                    <p>Service client disponible jour et nuit</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Icône du panier -->
    <div class="cart-icon" onclick="toggleCart()">
        <i class="fas fa-shopping-cart"></i>
        <div class="cart-count" id="cartCount" style="display: none;">0</div>
    </div>

    <!-- Overlay du panier -->
    <div class="cart-overlay" id="cartOverlay" onclick="closeCart()"></div>

    <!-- Sidebar du panier -->
    <div class="cart-sidebar" id="cartSidebar">
        <div class="cart-header">
            <h3 class="cart-title"><i class="fas fa-shopping-bag"></i> Mon Panier</h3>
            <button class="cart-close" onclick="closeCart()"><i class="fas fa-times"></i></button>
        </div>

        <div id="cartItems">
            <div style="text-align: center; padding: 3rem 1rem; color: rgba(255, 255, 255, 0.7);">
                <i class="fas fa-shopping-cart"
                    style="font-size: 4rem; margin-bottom: 1rem; display: block; opacity: 0.5;"></i>
                <h3 style="margin-bottom: 0.5rem;">Panier vide</h3>
                <p>Découvrez nos produits premium et ajoutez vos favoris !</p>
            </div>
        </div>

        <div class="cart-total">
            <button class="clear-cart-btn" onclick="clearCart()">
                <i class="fas fa-trash-alt"></i> Vider le panier
            </button>
            <div class="cart-total-price" id="cartTotal">Total: 0 FCFA</div>
            <button class="checkout-btn" id="checkoutBtn" onclick="openOrderModal()" disabled>
                <i class="fas fa-credit-card"></i> Commander Maintenant
            </button>
        </div>
    </div>

    <!-- Modal de commande -->
    <div class="order-modal" id="orderModal">
        <div class="order-modal-content">
            <h3 style="color: white; text-align: center; margin-bottom: 2rem;">
                <i class="fas fa-clipboard-check"></i>
                Finaliser votre commande
            </h3>

            <form class="order-form" id="orderForm">
                <div class="form-group">
                    <label for="customerName"><i class="fas fa-user"></i> Nom complet *</label>
                    <input type="text" id="customerName" required placeholder="Votre nom complet">
                </div>

                <div class="form-group">
                    <label for="customerPhone"><i class="fas fa-phone"></i> Numéro de téléphone *</label>
                    <input type="tel" id="customerPhone" required placeholder="+237 6XX XXX XXX">
                </div>

                <div class="form-group">
                    <label for="customerEmail"><i class="fas fa-envelope"></i> Email</label>
                    <input type="email" id="customerEmail" placeholder="votre.email@example.com (optionnel)">
                </div>

                <div class="form-group">
                    <label for="customerAddress"><i class="fas fa-map-marker-alt"></i> Adresse de livraison *</label>
                    <textarea id="customerAddress" required
                        placeholder="Votre adresse complète de livraison (quartier, ville)" rows="3"></textarea>
                </div>

                <div class="form-group">
                    <label for="orderNotes"><i class="fas fa-sticky-note"></i> Notes sur la commande</label>
                    <textarea id="orderNotes" placeholder="Instructions spéciales, préférences de livraison..."
                        rows="2"></textarea>
                </div>

                <div class="form-actions">
                    <button type="button" class="form-btn btn-cancel" onclick="closeOrderModal()">
                        <i class="fas fa-times"></i> Annuler
                    </button>
                    <button type="submit" class="form-btn btn-confirm">
                        <i class="fab fa-whatsapp"></i> Envoyer sur WhatsApp
                    </button>
                </div>
            </form>
        </div>
    </div>

    <div id="categories" class="categories">
        <div class="section-header animate-in">
            <h2 class="section-title">Nos Collections Premium</h2>
            <p class="section-subtitle">Découvrez notre gamme soigneusement sélectionnée de produits haut de gamme</p>
        </div>

        <!-- Électronique & Tech -->
        <section id="electronique">
            <div class="category-grid">
                <div class="category-card animate-in">
                    <div class="category-icon"><i class="fa-solid fa-shirt"></i></div>
                    <h3>Habillement & Make Up</h3>
                    <p>Les dernières innovations technologiques : smartphones, ordinateurs, accessoires high-tech avec
                        garantie officielle</p>

                    <div class="product-grid">
                        <div class="product-card" data-name="iPhone 15 Pro Max" data-price="1299000"
                            data-image="images/iphone15-pro-max.jpg">
                            <div class="product-badge">Nouveau</div>
                            <div class="product-image"
                                style="background-image: url('https://images.unsplash.com/photo-1695048133142-1a20484d2569?w=400&h=300&fit=crop');">
                                <i class="fas fa-mobile-alt"></i>
                            </div>
                            <div class="product-info">
                                <div class="product-name">iPhone 15 Pro Max</div>
                                <div class="product-description">Le smartphone le plus avancé avec puce A17 Pro et
                                    caméra 48MP</div>
                                <div class="product-price-section">
                                    <div>
                                        <span class="product-price">1,299,000 FCFA</span>
                                        <span class="product-old-price">1,450,000 FCFA</span>
                                    </div>
                                    <div class="product-rating">
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <span>(4.9)</span>
                                    </div>
                                </div>
                            </div>
                            <button class="quick-add-btn">
                                <i class="fas fa-cart-plus"></i> Ajouter
                            </button>
                        </div>

                        <div class="product-card" data-name="Coffret Soins Visage Bio" data-price="89000"
                            data-image="https://images.unsplash.com/photo-1571781926291-c477ebfd024b?w=400&h=300&fit=crop">
                            <div class="product-image"
                                style="background-image: url('https://images.unsplash.com/photo-1571781926291-c477ebfd024b?w=400&h=300&fit=crop');">
                                <i class="fas fa-leaf"></i>
                            </div>
                            <div class="product-info">
                                <div class="product-name">Coffret Soins Visage Bio</div>
                                <div class="product-description">Gamme complète bio : nettoyant, sérum, crème hydratante
                                </div>
                                <div class="product-price-section">
                                    <div>
                                        <span class="product-price">89,000 FCFA</span>
                                    </div>
                                    <div class="product-rating">
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star-half-alt"></i>
                                        <span>(4.7)</span>
                                    </div>
                                </div>
                            </div>
                            <button class="quick-add-btn">
                                <i class="fas fa-cart-plus"></i> Ajouter
                            </button>
                        </div>

                        <div class="product-card" data-name="Collection Huiles Essentielles" data-price="29000"
                            data-image="https://images.unsplash.com/photo-1608571423902-eed4a5ad8108?w=400&h=300&fit=crop">
                            <div class="product-image"
                                style="background-image: url('https://images.unsplash.com/photo-1608571423902-eed4a5ad8108?w=400&h=300&fit=crop');">
                                <i class="fas fa-seedling"></i>
                            </div>
                            <div class="product-info">
                                <div class="product-name">Collection Huiles Essentielles</div>
                                <div class="product-description">Set de 6 huiles pures : lavande, eucalyptus, tea
                                    tree...</div>
                                <div class="product-price-section">
                                    <div>
                                        <span class="product-price">29,000 FCFA</span>
                                    </div>
                                    <div class="product-rating">
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <span>(4.8)</span>
                                    </div>
                                </div>
                            </div>
                            <button class="quick-add-btn">
                                <i class="fas fa-cart-plus"></i> Ajouter
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Gaming & Loisirs -->
                <div class="category-card animate-in">
                    <div class="category-icon"><i class="fas fa-gamepad"></i></div>
                    <h3>Gaming & Divertissement</h3>
                    <p>Consoles dernière génération, jeux exclusifs, accessoires gaming pro et produits culturels pour
                        vos moments détente</p>

                    <div class="product-grid">
                        <div class="product-card" data-name="PlayStation 5 Pro" data-price="499000"
                            data-image="https://images.unsplash.com/photo-1606144042614-b2417e99c4e3?w=400&h=300&fit=crop">
                            <div class="product-badge">Gaming</div>
                            <div class="product-image"
                                style="background-image: url('https://images.unsplash.com/photo-1606144042614-b2417e99c4e3?w=400&h=300&fit=crop');">
                                <i class="fas fa-gamepad"></i>
                            </div>
                            <div class="product-info">
                                <div class="product-name">PlayStation 5 Pro</div>
                                <div class="product-description">Console nouvelle génération avec 2 manettes incluses
                                </div>
                                <div class="product-price-section">
                                    <div>
                                        <span class="product-price">499,000 FCFA</span>
                                    </div>
                                    <div class="product-rating">
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <span>(4.9)</span>
                                    </div>
                                </div>
                            </div>
                            <button class="quick-add-btn">
                                <i class="fas fa-cart-plus"></i> Ajouter
                            </button>
                        </div>

                        <div class="product-card" data-name="Puzzle Artistique 1000p" data-price="19000"
                            data-image="https://images.unsplash.com/photo-1594736797933-d0401ba2fe65?w=400&h=300&fit=crop">
                            <div class="product-image"
                                style="background-image: url('https://images.unsplash.com/photo-1594736797933-d0401ba2fe65?w=400&h=300&fit=crop');">
                                <i class="fas fa-puzzle-piece"></i>
                            </div>
                            <div class="product-info">
                                <div class="product-name">Puzzle Artistique 1000p</div>
                                <div class="product-description">Puzzle premium avec image d'art contemporain</div>
                                <div class="product-price-section">
                                    <div>
                                        <span class="product-price">19,000 FCFA</span>
                                    </div>
                                    <div class="product-rating">
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star-half-alt"></i>
                                        <span>(4.5)</span>
                                    </div>
                                </div>
                            </div>
                            <button class="quick-add-btn">
                                <i class="fas fa-cart-plus"></i> Ajouter
                            </button>
                        </div>

                        <div class="product-card" data-name="Livre Best-seller 2024" data-price="15000"
                            data-image="https://images.unsplash.com/photo-1481627834876-b7833e8f5570?w=400&h=300&fit=crop">
                            <div class="product-image"
                                style="background-image: url('https://images.unsplash.com/photo-1481627834876-b7833e8f5570?w=400&h=300&fit=crop');">
                                <i class="fas fa-book"></i>
                            </div>
                            <div class="product-info">
                                <div class="product-name">Livre Best-seller 2024</div>
                                <div class="product-description">Roman captivant, lauréat prix littéraire international
                                </div>
                                <div class="product-price-section">
                                    <div>
                                        <span class="product-price">15,000 FCFA</span>
                                    </div>
                                    <div class="product-rating">
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <i class="fas fa-star"></i>
                                        <span>(4.8)</span>
                                    </div>
                                </div>
                            </div>
                            <button class="quick-add-btn">
                                <i class="fas fa-cart-plus"></i> Ajouter
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Newsletter Section -->
        <div class="newsletter-section animate-in">
            <h3 style="color: white; font-size: 2rem; margin-bottom: 1rem;">
                <i class="fas fa-envelope"></i> Restez Informé
            </h3>
            <p style="color: rgba(255, 255, 255, 0.8); font-size: 1.1rem;">
                Recevez nos offres exclusives et les dernières nouveautés en avant-première
            </p>
            <div class="newsletter-form">
                <input type="email" class="newsletter-input" placeholder="Votre adresse email">
                <button class="newsletter-btn">
                    <i class="fas fa-paper-plane"></i> S'abonner
                </button>
            </div>
        </div>
    </div>

    <footer id="contact">
        <div class="footer-content">
            <div class="footer-section">
                <h4><i class="fas fa-store"></i> ShopVerse</h4>
                <p>Votre destination shopping premium au Cameroun. Nous sélectionnons les meilleurs produits pour vous
                    offrir une expérience d'achat exceptionnelle.</p>
                <div class="social-icons">
                    <a href="#" class="social-icon"><i class="fab fa-facebook-f"></i></a>
                    <a href="#" class="social-icon"><i class="fab fa-instagram"></i></a>
                    <a href="#" class="social-icon"><i class="fab fa-twitter"></i></a>
                    <a href="#" class="social-icon"><i class="fab fa-whatsapp"></i></a>
                </div>
            </div>

            <div class="footer-section">
                <h4><i class="fas fa-shopping-bag"></i> Shopping</h4>
                <ul class="footer-links">
                    <li><a href="#electronique">Électronique</a></li>
                    <li><a href="#mode">Mode & Style</a></li>
                    <li><a href="#maison">Maison & Déco</a></li>
                    <li><a href="#sport">Sport & Fitness</a></li>
                    <li><a href="#beaute">Beauté & Wellness</a></li>
                    <li><a href="#gaming">Gaming</a></li>
                </ul>
            </div>

            <div class="footer-section">
                <h4><i class="fas fa-user-cog"></i> Service Client</h4>
                <ul class="footer-links">
                    <li><a href="#">Centre d'aide</a></li>
                    <li><a href="#">Suivi de commande</a></li>
                    <li><a href="#">Retours & échanges</a></li>
                    <li><a href="#">Garantie produits</a></li>
                    <li><a href="#">Guide des tailles</a></li>
                    <li><a href="#">FAQ</a></li>
                </ul>
            </div>

            <div class="footer-section">
                <h4><i class="fas fa-map-marker-alt"></i> Contact</h4>
                <div style="color: rgba(255, 255, 255, 0.8); line-height: 1.8;">
                    <p><i class="fas fa-map-marker-alt"></i> Douala, Littoral, Cameroun</p>
                    <p><i class="fas fa-phone"></i> +237 657 300 644</p>
                    <p><i class="fas fa-envelope"></i> ulrichbrayan@gmail.com</p>
                    <p><i class="fas fa-clock"></i> Lun-Sam: 8h-20h</p>
                    <p><i class="fab fa-whatsapp"></i> Service WhatsApp 24/7</p>
                </div>
            </div>
        </div>

        <div class="footer-bottom">
            <p>&copy; 2024 ShopVerse Cameroun. Tous droits réservés. |
                <a href="#" style="color: var(--accent-color);">Conditions d'utilisation</a> |
                <a href="#" style="color: var(--accent-color);">Politique de confidentialité</a>
            </p>
        </div>
    </footer>

    <script>
        // Configuration et données
        let cart = [];
        const WHATSAPP_NUMBER = "237657300644";

        // Données produits avec vraies images
        const products = {
            "iPhone 15 Pro Max": {
                price: 1299000,
                category: "Électronique",
                image: "https://i.postimg.cc/tJtDWNc1/Screenshot-20250703-215113-2.jpg",
                description: "Le smartphone le plus avancé avec puce A17 Pro et caméra 48MP"
            },
            "MacBook Air M3": {
                price: 1499000,
                category: "Électronique",
                image: "https://images.unsplash.com/photo-1541807084-5c52b6b3adef?w=400&h=300&fit=crop",
                description: "Ultra-portable avec puce M3, écran Liquid Retina 13.6\""
            },
            "AirPods Pro (2ème gen)": {
                price: 279000,
                category: "Électronique",
                image: "https://images.unsplash.com/photo-1606220945770-b5b6c2c55bf1?w=400&h=300&fit=crop",
                description: "Audio spatial, suppression active du bruit, autonomie 30h"
            },
            "Robe Designer Été": {
                price: 89000,
                category: "Mode",
                image: "https://images.unsplash.com/photo-1515372039744-b8f02a3ae446?w=400&h=300&fit=crop",
                description: "Robe légère en soie, coupe élégante, parfaite pour l'été"
            },
            "Sneakers Nike Air Max": {
                price: 159000,
                category: "Mode",
                image: "https://images.unsplash.com/photo-1549298916-b41d501d3772?w=400&h=300&fit=crop",
                description: "Chaussures premium avec technologie Air Max, confort maximal"
            },
            "Sac à Main Cuir Premium": {
                price: 299000,
                category: "Mode",
                image: "https://images.unsplash.com/photo-1584917865442-de89df76afd3?w=400&h=300&fit=crop",
                description: "Sac en cuir véritable italien, design intemporel et élégant"
            },
            "Canapé Scandinave 3 Places": {
                price: 899000,
                category: "Maison",
                image: "https://images.unsplash.com/photo-1555041469-a586c61ea9bc?w=400&h=300&fit=crop",
                description: "Design moderne en tissu premium, structure bois massif"
            },
            "Collection Plantes Premium": {
                price: 29000,
                category: "Maison",
                image: "https://images.unsplash.com/photo-1416879595882-3373a0480b5b?w=400&h=300&fit=crop",
                description: "Set de 3 plantes d'intérieur avec pots design inclus"
            },
            "Lampe Architecte LED": {
                price: 179000,
                category: "Maison",
                image: "https://images.unsplash.com/photo-1507473885765-e6ed057f782c?w=400&h=300&fit=crop",
                description: "Lampe de bureau design avec variateur d'intensité intégré"
            },
            "Chaussures Running Pro": {
                price: 129000,
                category: "Sport",
                image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=400&h=300&fit=crop",
                description: "Technologie avancée d'amorti, légères et respirantes"
            },
            "Set Haltères Ajustables": {
                price: 79000,
                category: "Sport",
                image: "https://images.unsplash.com/photo-1571019613454-1cb2f99b2d8b?w=400&h=300&fit=crop",
                description: "Poids modulables 5-25kg, parfaits pour home gym"
            },
            "Tapis Yoga Premium": {
                price: 39000,
                category: "Sport",
                image: "https://images.unsplash.com/photo-1544367567-0f2fcb009e0b?w=400&h=300&fit=crop",
                description: "Matériau écologique, antidérapant, épaisseur optimale"
            },
            "Kit Maquillage Professionnel": {
                price: 149000,
                category: "Beauté",
                image: "https://images.unsplash.com/photo-1596462502278-27bfdc403348?w=400&h=300&fit=crop",
                description: "Palette complète avec pinceaux premium, longue tenue"
            },
            "Coffret Soins Visage Bio": {
                price: 89000,
                category: "Beauté",
                image: "https://images.unsplash.com/photo-1571781926291-c477ebfd024b?w=400&h=300&fit=crop",
                description: "Gamme complète bio : nettoyant, sérum, crème hydratante"
            },
            "Collection Huiles Essentielles": {
                price: 29000,
                category: "Beauté",
                image: "https://images.unsplash.com/photo-1608571423902-eed4a5ad8108?w=400&h=300&fit=crop",
                description: "Set de 6 huiles pures : lavande, eucalyptus, tea tree..."
            },
            "PlayStation 5 Pro": {
                price: 499000,
                category: "Gaming",
                image: "https://images.unsplash.com/photo-1606144042614-b2417e99c4e3?w=400&h=300&fit=crop",
                description: "Console nouvelle génération avec 2 manettes incluses"
            },
            "Puzzle Artistique 1000p": {
                price: 19000,
                category: "Gaming",
                image: "https://images.unsplash.com/photo-1594736797933-d0401ba2fe65?w=400&h=300&fit=crop",
                description: "Puzzle premium avec image d'art contemporain"
            },
            "Livre Best-seller 2024": {
                price: 15000,
                category: "Gaming",
                image: "https://images.unsplash.com/photo-1481627834876-b7833e8f5570?w=400&h=300&fit=crop",
                description: "Roman captivant, lauréat prix littéraire international"
            }
        };

        // Fonctions de gestion du panier
        function addToCart(productName, productPrice) {
            const existingItem = cart.find(item => item.name === productName);

            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                const product = products[productName];
                cart.push({
                    name: productName,
                    price: productPrice,
                    quantity: 1,
                    image: product.image,
                    description: product.description
                });
            }

            updateCartUI();
            showNotification(`${productName} ajouté au panier !`, 'success');

            // Animation du panier
            const cartIcon = document.querySelector('.cart-icon');
            cartIcon.style.transform = 'scale(1.2)';
            setTimeout(() => {
                cartIcon.style.transform = '';
            }, 200);
        }

        function removeFromCart(productName) {
            cart = cart.filter(item => item.name !== productName);
            updateCartUI();
            showNotification(`Produit retiré du panier`, 'error');
        }

        function updateQuantity(productName, change) {
            const item = cart.find(item => item.name === productName);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    removeFromCart(productName);
                } else {
                    updateCartUI();
                }
            }
        }

        function updateCartUI() {
            const cartCount = document.getElementById('cartCount');
            const cartItems = document.getElementById('cartItems');
            const cartTotal = document.getElementById('cartTotal');
            const checkoutBtn = document.getElementById('checkoutBtn');

            // Compter le nombre total d'articles
            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            cartCount.textContent = totalItems;
            cartCount.style.display = totalItems > 0 ? 'flex' : 'none';

            // Calculer le total
            const totalPrice = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            cartTotal.innerHTML = `<i class="fas fa-coins"></i> Total: ${formatPrice(totalPrice)}`;

            // Activer/désactiver le bouton de commande
            checkoutBtn.disabled = cart.length === 0;

            // Afficher les articles
            if (cart.length === 0) {
                cartItems.innerHTML = `
                    <div style="text-align: center; padding: 3rem 1rem; color: rgba(255, 255, 255, 0.7);">
                        <i class="fas fa-shopping-cart" style="font-size: 4rem; margin-bottom: 1rem; display: block; opacity: 0.5;"></i>
                        <h3 style="margin-bottom: 0.5rem;">Panier vide</h3>
                        <p>Découvrez nos produits premium et ajoutez vos favoris !</p>
                    </div>
                `;
            } else {
                cartItems.innerHTML = cart.map(item => `
                    <div class="cart-item">
                        <div class="cart-item-image" style="background-image: url('${item.image}');">
                        </div>
                        <div class="cart-item-info">
                            <div class="cart-item-name">${item.name}</div>
                            <div class="product-description" style="font-size: 0.8rem; opacity: 0.8; margin: 0.3rem 0;">${item.description}</div>
                            <div class="cart-item-price" style="color: var(--accent-color); font-weight: bold;">${formatPrice(item.price)}</div>
                            <div class="cart-item-quantity" style="display: flex; align-items: center; gap: 0.5rem; margin-top: 0.5rem;">
                                <button class="quantity-btn" onclick="updateQuantity('${item.name}', -1)">
                                    <i class="fas fa-minus"></i>
                                </button>
                                <span class="quantity-value">${item.quantity}</span>
                                <button class="quantity-btn" onclick="updateQuantity('${item.name}', 1)">
                                    <i class="fas fa-plus"></i>
                                </button>
                            </div>
                        </div>
                        <button class="remove-item" onclick="removeFromCart('${item.name}')" title="Supprimer">
                            <i class="fas fa-trash-alt"></i>
                        </button>
                    </div>
                `).join('');
            }
        }

        function formatPrice(price) {
            return new Intl.NumberFormat('fr-FR', {
                minimumFractionDigits: 0,
                maximumFractionDigits: 0
            }).format(price) + ' FCFA';
        }

        function toggleCart() {
            const cartSidebar = document.getElementById('cartSidebar');
            const cartOverlay = document.getElementById('cartOverlay');

            cartSidebar.classList.toggle('open');
            cartOverlay.classList.toggle('open');

            // Désactiver le scroll du body quand le panier est ouvert
            if (cartSidebar.classList.contains('open')) {
                document.body.style.overflow = 'hidden';
            } else {
                document.body.style.overflow = '';
            }
        }

        function closeCart() {
            const cartSidebar = document.getElementById('cartSidebar');
            const cartOverlay = document.getElementById('cartOverlay');

            cartSidebar.classList.remove('open');
            cartOverlay.classList.remove('open');
            document.body.style.overflow = '';
        }

        function openOrderModal() {
            if (cart.length === 0) return;
            document.getElementById('orderModal').classList.add('open');
            document.body.style.overflow = 'hidden';
        }

        function closeOrderModal() {
            document.getElementById('orderModal').classList.remove('open');
            document.body.style.overflow = '';
        }

        function clearCart() {
            if (cart.length === 0) return;

            if (confirm('🗑️ Êtes-vous sûr de vouloir vider votre panier ?')) {
                cart = [];
                updateCartUI();
                showNotification('Panier vidé', 'error');
            }
        }

        function generateWhatsAppMessage() {
            const name = document.getElementById('customerName').value.trim();
            const phone = document.getElementById('customerPhone').value.trim();
            const email = document.getElementById('customerEmail').value.trim();
            const address = document.getElementById('customerAddress').value.trim();
            const notes = document.getElementById('orderNotes').value.trim();

            let message = `🛍️ *NOUVELLE COMMANDE - SHOPVERSE*\n`;
            message += `═══════════════════════════\n\n`;

            message += `👤 *INFORMATIONS CLIENT*\n`;
            message += `▪️ Nom: ${name}\n`;
            message += `▪️ Téléphone: ${phone}\n`;
            if (email) message += `▪️ Email: ${email}\n`;
            message += `▪️ Adresse: ${address}\n\n`;

            message += `🛒 *DÉTAILS DE LA COMMANDE*\n`;
            message += `═══════════════════════════\n`;

            let total = 0;
            cart.forEach((item, index) => {
                const itemTotal = item.price * item.quantity;
                total += itemTotal;
                message += `\n${index + 1}. *${item.name}*\n`;
                message += `   💰 Prix: ${formatPrice(item.price)}\n`;
                message += `   📦 Quantité: ${item.quantity}\n`;
                message += `   💳 Sous-total: ${formatPrice(itemTotal)}\n`;
                message += `   🖼️ Image: ${item.image}`;
            });

            message += `\n\n═══════════════════════════\n`;
            message += `💰 *TOTAL GÉNÉRAL: ${formatPrice(total)}*\n`;
            message += `═══════════════════════════\n\n`;

            if (notes) {
                message += `📝 *NOTES SPÉCIALES:*\n${notes}\n\n`;
            }

            message += `⏰ *Commande passée le:* ${new Date().toLocaleString('fr-FR', {
                timeZone: 'Africa/Douala'
            })}\n`;
            message += `🌐 *Via:* ShopVerse Premium\n`;
            message += `🚚 *Livraison:* Express 24h à Douala/Yaoundé`;

            return message;
        }

        function sendToWhatsApp() {
            const message = generateWhatsAppMessage();
            const encodedMessage = encodeURIComponent(message);
            const whatsappURL = `https://wa.me/${WHATSAPP_NUMBER}?text=${encodedMessage}`;

            // Ouvrir WhatsApp
            window.open(whatsappURL, '_blank');

            // Vider le panier et fermer les modals
            cart = [];
            updateCartUI();
            closeOrderModal();
            closeCart();

            showNotification('🎉 Commande envoyée sur WhatsApp ! Notre équipe vous contactera rapidement.', 'success');
        }

        function showNotification(message, type = 'success') {
            const notification = document.createElement('div');
            notification.className = `notification ${type}`;

            const icon = type === 'success' ? 'fas fa-check-circle' : 'fas fa-exclamation-circle';

            notification.innerHTML = `
                <i class="${icon}"></i>
                <span>${message}</span>
            `;

            document.body.appendChild(notification);

            // Auto-remove après 5 secondes
            setTimeout(() => {
                notification.remove();
            }, 5000);
        }

        // Ajouter les événements onclick aux boutons d'ajout
        document.addEventListener('DOMContentLoaded', function () {
            // Ajouter les événements aux boutons existants
            const addButtons = document.querySelectorAll('.quick-add-btn');
            addButtons.forEach(button => {
                button.addEventListener('click', function () {
                    const productCard = this.closest('.product-card');
                    const productName = productCard.dataset.name;
                    const productPrice = parseInt(productCard.dataset.price);

                    if (productName && productPrice) {
                        addToCart(productName, productPrice);
                    }
                });
            });

            // Header scroll effect
            window.addEventListener('scroll', function () {
                const header = document.getElementById('header');
                if (window.scrollY > 100) {
                    header.classList.add('scrolled');
                } else {
                    header.classList.remove('scrolled');
                }
            });

            // Animation d'entrée des éléments
            const observerOptions = {
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px'
            };

            const observer = new IntersectionObserver(function (entries) {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.animationDelay = '0.1s';
                        entry.target.classList.add('animate-in');
                    }
                });
            }, observerOptions);

            document.querySelectorAll('.animate-in').forEach(el => {
                observer.observe(el);
            });
        });

        // Gestion du formulaire de commande
        document.getElementById('orderForm').addEventListener('submit', function (e) {
            e.preventDefault();
            sendToWhatsApp();
        });

        // Gestion de la newsletter
        document.querySelector('.newsletter-btn').addEventListener('click', function () {
            const email = document.querySelector('.newsletter-input').value.trim();
            if (email && email.includes('@')) {
                showNotification('🎉 Merci de votre inscription à notre newsletter !', 'success');
                document.querySelector('.newsletter-input').value = '';
            } else {
                showNotification('⚠️ Veuillez entrer une adresse email valide', 'error');
            }
        });
    </script>
</body>
