# Neon Reef Co. Website

A modern, clean e-commerce website for coral and marine life retail, designed to integrate seamlessly with Shopify.

![Neon Reef Co Logo](logo.png)

## 🌊 Features

- **Modern Dark Theme**: Sleek design with vibrant gradient accents matching your brand
- **Responsive Design**: Fully optimized for desktop, tablet, and mobile devices
- **Interactive Elements**: Smooth animations, cart functionality, and user notifications
- **Shopify Ready**: Easy integration with Shopify's platform
- **Performance Optimized**: Fast loading times with lazy loading images

## 🚀 Quick Start - GitHub Setup

### Step 1: Create GitHub Repository

1. Go to [github.com/new](https://github.com/new)
2. Repository name: `neon-reef-co`
3. Make it **Public**
4. Don't initialize with any files
5. Click **Create repository**

### Step 2: Upload Files

1. Click **"uploading an existing file"** link on the empty repo page
2. Drag and drop these files:
   - `index.html`
   - `style.css`
   - `script.js`
   - Your logo image (rename to `logo.png`)
   - This `README.md` file
3. Add commit message: "Initial website upload"
4. Click **Commit changes**

### Step 3: Enable GitHub Pages

1. Go to **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: **main** / **root**
4. Click **Save**
5. Your site will be live at: `https://eggnogsparklebutt.github.io/neon-reef-co/`

## 🛍️ Shopify Integration Options

### Option 1: Custom Storefront (Recommended)

1. **Shopify Storefront API**
   - Use this website as a custom storefront
   - Connect to Shopify's API for product data
   - Maintain full design control

2. **Setup Steps**:
   ```javascript
   // Add to script.js
   const SHOPIFY_DOMAIN = 'your-store.myshopify.com';
   const STOREFRONT_ACCESS_TOKEN = 'your-token-here';
   ```

### Option 2: Convert to Shopify Theme

1. **Create Theme Structure**:
   ```
   neon-reef-co-theme/
   ├── assets/
   │   ├── style.css
   │   └── script.js
   ├── layout/
   │   └── theme.liquid
   ├── templates/
   │   ├── index.liquid
   │   └── product.liquid
   └── config/
       └── settings_schema.json
   ```

2. **Convert HTML to Liquid**:
   - Replace static content with Shopify liquid tags
   - Use `{{ product.title }}` for dynamic content
   - Implement Shopify cart functionality

### Option 3: Embedded Buy Button

1. Simple integration using Shopify Buy Button
2. Keep current website, embed products
3. Less control but easier setup

## 📁 File Structure

```
neon-reef-co/
├── index.html          # Main website file
├── style.css          # Styling with gradient theme
├── script.js          # Interactive functionality
├── logo.png           # Your Neon Reef Co logo
└── README.md          # This file
```

## 🎨 Customization

### Colors
Edit CSS variables in `style.css`:
```css
:root {
    --primary-pink: #e935c1;
    --primary-purple: #8b5cf6;
    --primary-blue: #3b82f6;
    --primary-cyan: #06b6d4;
}
```

### Adding Products
Replace placeholder content in `index.html`:
```html
<div class="product-card">
    <div class="product-image">
        <img src="your-coral-image.jpg" alt="Coral Name">
    </div>
    <div class="product-info">
        <h3 class="product-title">Your Coral Name</h3>
        <p class="product-price">$99.00</p>
    </div>
</div>
```

## 🖼️ Image Optimization

For best performance:
1. Resize images to max 800px width for products
2. Use WebP format when possible
3. Compress images using tools like TinyPNG
4. Use lazy loading for below-fold images

## 📱 Mobile Optimization

The site is fully responsive with:
- Mobile menu toggle
- Touch-friendly buttons
- Optimized font sizes
- Flexible grid layouts

## 🔧 Development

### Local Testing
1. Download all files
2. Open `index.html` in a browser
3. Or use a local server:
   ```bash
   python -m http.server 8000
   # Visit http://localhost:8000
   ```

### Making Changes
1. Edit files locally
2. Test changes
3. Push to GitHub
4. Changes auto-deploy to GitHub Pages

## 📈 Next Steps

1. **Add Real Product Images**: Replace placeholders with your coral photos
2. **Set Up Analytics**: Add Google Analytics or Shopify Analytics
3. **SEO Optimization**: Add meta descriptions and structured data
4. **Payment Integration**: Connect Shopify checkout or payment gateway
5. **Inventory Management**: Link to your inventory system

## 🤝 Support

For Shopify integration help:
- [Shopify Partner Program](https://www.shopify.com/partners)
- [Shopify Developers Documentation](https://shopify.dev/)
- [Liquid Template Language](https://shopify.dev/docs/themes/liquid)

## 📄 License

© 2024 Neon Reef Co. All rights reserved.

---

Built with 💙 for the reef keeping community 