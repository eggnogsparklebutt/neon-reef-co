# Converting Your HTML Site to a Shopify Theme 🎨

## YES! You CAN Keep Your Design! 

Here's exactly how to convert your beautiful website into a Shopify theme. You'll keep all your styling and design - just need to reorganize the files.

---

## Step 1: Create Theme Structure

Create these folders in a new directory called `neon-reef-theme`:

```
neon-reef-theme/
├── assets/          (your CSS and JS files go here)
├── config/          (theme settings)
├── layout/          (main template wrapper)
├── templates/       (page templates)
├── sections/        (reusable sections)
└── snippets/        (small reusable pieces)
```

---

## Step 2: Convert Your Files

### 1. Move CSS to assets/
- Rename `style.css` to `style.css.liquid`
- Place in `assets/` folder

### 2. Move JS to assets/
- Keep `script.js` as is
- Place in `assets/` folder

### 3. Create layout/theme.liquid
This replaces your index.html structure:

```liquid
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ page_title }} - {{ shop.name }}</title>
    {{ 'style.css' | asset_url | stylesheet_tag }}
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    {{ content_for_header }}
</head>
<body>
    {% section 'header' %}
    
    <main>
        {{ content_for_layout }}
    </main>
    
    {% section 'footer' %}
    
    {{ 'script.js' | asset_url | script_tag }}
</body>
</html>
```

### 4. Create sections/header.liquid
Copy your header HTML here:

```liquid
<header class="header">
    <div class="header-top">
        <div class="container">
            <p>Free Shipping on Orders Over $199 | Australia Wide Express Delivery</p>
        </div>
    </div>
    <nav class="navbar">
        <div class="container">
            <div class="nav-wrapper">
                <div class="logo">
                    <!-- Your logo SVG here -->
                </div>
                <div class="nav-menu" id="navMenu">
                    {% for link in linklists.main-menu.links %}
                        <a href="{{ link.url }}" class="nav-link">{{ link.title }}</a>
                    {% endfor %}
                </div>
                <div class="nav-icons">
                    <button class="icon-btn search-btn"><i class="fas fa-search"></i></button>
                    <a href="/account" class="icon-btn"><i class="fas fa-user"></i></a>
                    <a href="/cart" class="icon-btn cart-btn">
                        <i class="fas fa-shopping-cart"></i>
                        <span class="cart-count">{{ cart.item_count }}</span>
                    </a>
                    <button class="mobile-menu-btn" id="mobileMenuBtn">
                        <i class="fas fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>
    </nav>
</header>
```

### 5. Create templates/index.liquid
Your homepage content:

```liquid
{% section 'hero' %}
{% section 'categories' %}
{% section 'featured-products' %}
{% section 'info-banner' %}
{% section 'newsletter' %}
```

### 6. Create sections/hero.liquid
```liquid
<section class="hero">
    <div class="hero-background">
        <img src="https://images.unsplash.com/photo-1583212292454-1fe6229603b7?w=1600&h=900&fit=crop" alt="Vibrant coral reef">
    </div>
    <div class="hero-content">
        <h1 class="hero-title"><span class="gradient-text">Bring the ocean home</span></h1>
        <p class="hero-subtitle">Australia's Premier Destination for Exotic Corals & Marine Life</p>
        <div class="hero-buttons">
            <a href="/collections/corals" class="btn btn-primary">Shop Corals</a>
            <a href="/collections/new-arrivals" class="btn btn-secondary">New Arrivals</a>
        </div>
    </div>
    <div class="hero-gradient"></div>
</section>
```

### 7. Create sections/featured-products.liquid
This connects to real Shopify products:

```liquid
<section class="featured-products">
    <div class="container">
        <h2 class="section-title">Featured Products</h2>
        <div class="products-grid">
            {% assign featured = collections['featured'].products | limit: 8 %}
            {% for product in featured %}
            <div class="product-card">
                <div class="product-image">
                    <img src="{{ product.featured_image | img_url: '400x400' }}" alt="{{ product.title }}">
                    {% if product.available == false %}
                        <div class="product-badge">Sold Out</div>
                    {% elsif product.created_at > 7_days_ago %}
                        <div class="product-badge">New</div>
                    {% endif %}
                    <div class="product-actions">
                        <a href="{{ product.url }}" class="quick-view">Quick View</a>
                    </div>
                </div>
                <div class="product-info">
                    <h3 class="product-title">{{ product.title }}</h3>
                    <p class="product-price">{{ product.price | money }}</p>
                    <form action="/cart/add" method="post">
                        <input type="hidden" name="id" value="{{ product.selected_or_first_available_variant.id }}">
                        <button type="submit" class="btn btn-primary btn-small">Add to Cart</button>
                    </form>
                </div>
            </div>
            {% endfor %}
        </div>
    </div>
</section>
```

---

## Step 3: Upload to Shopify

1. **Zip your theme folder**
   - Select all folders (assets, config, layout, etc.)
   - Create a ZIP file

2. **Upload to Shopify**
   - Go to Online Store > Themes
   - Click "Upload theme"
   - Select your ZIP file

3. **Customize**
   - Click "Customize" on your theme
   - Add products
   - Configure settings

---

## What Changes from HTML to Liquid?

| HTML | Liquid |
|------|--------|
| Static product cards | `{% for product in collection.products %}` |
| Fixed prices | `{{ product.price | money }}` |
| Static cart count | `{{ cart.item_count }}` |
| Hard-coded links | `{{ link.url }}` |
| Static images | `{{ product.image | img_url: '400x400' }}` |

---

## Quick Copy-Paste Solution

If you want the ABSOLUTE quickest solution:

1. **Create these 4 files minimum:**

**layout/theme.liquid** - Your HTML wrapper
**templates/index.liquid** - Your homepage
**assets/style.css.liquid** - Your CSS (just rename)
**assets/script.js** - Your JS (keep as is)

2. **In theme.liquid**, paste your entire index.html but:
   - Replace the body content with `{{ content_for_layout }}`
   - Add `{{ content_for_header }}` in the head

3. **In templates/index.liquid**, paste everything that was inside your body tags

That's it! Your design is now a Shopify theme! 🎉

---

## Need More Help?

The main thing to remember:
- **Your design stays exactly the same**
- **You're just reorganizing files**
- **Shopify will handle the product data**

Your beautiful gradient colors, layout, and styling all remain intact! 