# Shopify Integration Guide for Neon Reef Co

## ⚠️ Why You're Getting "Branch isn't a valid theme" Error

**The current files are a static HTML website, NOT a Shopify theme!**

Shopify expects a specific folder structure with Liquid template files. Your current files are just HTML/CSS/JS, which is why Shopify can't recognize it as a theme.

## 🎯 Your Options

### Option 1: Use as External Website (Easiest)
- Keep your website on GitHub Pages
- Add "Buy Now" buttons that link to your Shopify store
- Use Shopify Buy Button on your static site

### Option 2: Convert to Shopify Theme (Complex)
You need to create this EXACT structure:

```
neon-reef-co/
├── assets/           # CSS, JS, images
├── config/           # Theme settings
├── layout/           # Main theme wrapper
├── locales/          # Translation files
├── sections/         # Reusable page sections
├── snippets/         # Small reusable code
├── templates/        # Page templates
└── templates.json    # Theme configuration
```

### Option 3: Use Page Builder App (Recommended)
1. Install a Shopify page builder app (like PageFly, Shogun)
2. Recreate your design in the builder
3. No coding required

## 🛠️ Quick Fix: Shopify Buy Button

Add this to your existing website:

```html
<!-- Shopify Buy Button -->
<div id='product-component-1234567890'></div>
<script type="text/javascript">
(function () {
  var scriptURL = 'https://sdks.shopifycdn.com/buy-button/latest/buy-button-storefront.min.js';
  window.ShopifyBuy && window.ShopifyBuy.UI ? initializeBuyButton() : loadScript();

  function loadScript() {
    var script = document.createElement('script');
    script.async = true;
    script.src = scriptURL;
    document.head.appendChild(script);
    script.onload = initializeBuyButton;
  }

  function initializeBuyButton() {
    var client = ShopifyBuy.buildClient({
      domain: 'your-store.myshopify.com',
      storefrontAccessToken: 'your-token-here',
    });

    ShopifyBuy.UI.onReady(client).then(function (ui) {
      ui.createComponent('product', {
        id: 'YOUR-PRODUCT-ID',
        node: document.getElementById('product-component-1234567890'),
      });
    });
  }
})();
</script>
```

## 📝 To Create a Proper Shopify Theme

You would need these files:

### 1. `layout/theme.liquid`
```liquid
<!DOCTYPE html>
<html>
<head>
  {{ content_for_header }}
  {{ 'style.css' | asset_url | stylesheet_tag }}
</head>
<body>
  {{ content_for_layout }}
  {{ 'script.js' | asset_url | script_tag }}
</body>
</html>
```

### 2. `templates/index.json`
```json
{
  "sections": {
    "hero": {
      "type": "hero-banner"
    },
    "products": {
      "type": "featured-products"
    }
  },
  "order": ["hero", "products"]
}
```

### 3. `config/settings_schema.json`
```json
[
  {
    "name": "theme_info",
    "theme_name": "Neon Reef Co",
    "theme_version": "1.0.0",
    "theme_author": "Your Name"
  }
]
```

## 🚀 Immediate Solution

1. **Keep your site on GitHub Pages**: `https://eggnogsparklebutt.github.io/neon-reef-co/`
2. **Create a Shopify store separately**
3. **Link them together**:
   - Add a "Shop" button on your website that goes to Shopify
   - Or use Shopify Buy Buttons on your static site

## 💡 Why This Approach Works

- Your beautiful design stays intact
- No need to learn Shopify's Liquid language
- Easier to maintain
- Can still process payments through Shopify

## Need Help?

- **Shopify Theme Development**: [shopify.dev/themes](https://shopify.dev/themes)
- **Buy Button Documentation**: [help.shopify.com/en/manual/online-sales-channels/buy-button](https://help.shopify.com/en/manual/online-sales-channels/buy-button)
- **Page Builder Apps**: Search "page builder" in Shopify App Store 