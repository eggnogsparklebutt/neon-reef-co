# 🚀 SUPER SIMPLE Copy-Paste Shopify Theme

Want to use your EXACT design in Shopify? Here's the copy-paste way:

## Step 1: Create These Folders
```
neon-reef-theme/
├── assets/
├── layout/
└── templates/
```

## Step 2: Create 4 Files (Just Copy & Paste!)

### File 1: `assets/style.css.liquid`
- Just copy your ENTIRE `style.css` file
- Save it as `style.css.liquid` in the assets folder
- That's it! No changes needed!

### File 2: `assets/script.js`
- Copy your ENTIRE `script.js` file  
- Save it in the assets folder
- Done!

### File 3: `layout/theme.liquid`
Copy and paste this EXACTLY:

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
    {{ content_for_layout }}
    {{ 'script.js' | asset_url | script_tag }}
</body>
</html>
```

### File 4: `templates/index.liquid`
1. Open your `index.html`
2. Copy EVERYTHING between `<body>` and `</body>` 
3. Paste it into this file
4. Save!

## Step 3: Make it Dynamic (Optional but Cool!)

Want the cart to actually work? Just replace this in your pasted HTML:

**Find:** `<span class="cart-count">0</span>`  
**Replace:** `<span class="cart-count">{{ cart.item_count }}</span>`

**Find:** Any "Add to Cart" button  
**Replace with:**
```html
<form action="/cart/add" method="post">
    <input type="hidden" name="id" value="PRODUCT_ID_HERE">
    <button type="submit" class="btn btn-primary btn-small">Add to Cart</button>
</form>
```

## Step 4: Upload to Shopify

1. Put your 4 files in the folders
2. ZIP the `neon-reef-theme` folder
3. In Shopify Admin: Online Store → Themes → Upload theme
4. Upload your ZIP file

## 🎉 THAT'S IT! Your design is now a Shopify theme!

---

## Want Products to Show Automatically?

Replace your product grid HTML with this:

```liquid
<div class="products-grid">
    {% for product in collections.all.products limit: 8 %}
    <div class="product-card">
        <div class="product-image">
            <img src="{{ product.featured_image | img_url: '400x400' }}" alt="{{ product.title }}">
            <div class="product-actions">
                <a href="{{ product.url }}" class="quick-view">Quick View</a>
            </div>
        </div>
        <div class="product-info">
            <h3 class="product-title">{{ product.title }}</h3>
            <p class="product-price">{{ product.price | money }}</p>
            <form action="/cart/add" method="post">
                <input type="hidden" name="id" value="{{ product.variants.first.id }}">
                <button type="submit" class="btn btn-primary btn-small">Add to Cart</button>
            </form>
        </div>
    </div>
    {% endfor %}
</div>
```

---

## The Truth:
- Your beautiful gradient design? ✅ Stays exactly the same
- Your CSS animations? ✅ Work perfectly  
- Your layout? ✅ Unchanged
- Just organized differently for Shopify to understand!

## Still Confused?
The ONLY real changes:
1. Split your HTML into 2 files (theme.liquid + index.liquid)
2. Rename style.css → style.css.liquid
3. That's literally it! 