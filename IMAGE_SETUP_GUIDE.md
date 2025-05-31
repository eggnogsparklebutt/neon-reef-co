# Image Setup Guide for Neon Reef Co

## Logo Setup (IMPORTANT)

### Making Your Logo Transparent
1. Save your logo as **PNG format** (not JPG) to preserve transparency
2. If your logo currently has a black background, you can remove it using:
   - **Online Tool**: [remove.bg](https://www.remove.bg/) - Free and instant
   - **Photoshop**: Use Magic Eraser or Select > Color Range
   - **GIMP (Free)**: Use "Color to Alpha" feature
3. Save as `logo.png` in your main folder

## Organizing Your Coral Images

Based on your Google Drive folder, create this structure:

```
neon-reef-co/
├── logo.png (transparent background)
├── images/
│   ├── hero-coral.jpg (renamed from one of your best wide shots)
│   ├── category-corals.jpg 
│   ├── category-fish.jpg
│   ├── category-inverts.jpg
│   ├── category-equipment.jpg
│   ├── coral-1.jpg (IMG-20250531-WA0003.jpg)
│   ├── coral-2.jpg (IMG-20250531-WA0004.jpg)
│   ├── coral-3.jpg (IMG-20250531-WA0005.jpg)
│   ├── coral-4.jpg (IMG-20250531-WA0006.jpg)
│   ├── coral-5.jpg (IMG-20250531-WA0007.jpg)
│   ├── coral-6.jpg (IMG-20250531-WA0008.jpg)
│   ├── coral-7.jpg (IMG-20250531-WA0009.jpg)
│   └── coral-8.jpg (IMG-20250531-WA0010.jpg)
```

## Image Recommendations

### Hero Image (hero-coral.jpg)
- Use your most vibrant, wide coral shot
- Recommended: IMG-20250531-WA0011.jpg or IMG-20250531-WA0015.jpg
- This will be the main background image

### Category Images
- **category-corals.jpg**: Your best coral colony shot
- **category-fish.jpg**: If you have fish images, otherwise use a coral
- **category-inverts.jpg**: Shrimp/crab/snail image if available
- **category-equipment.jpg**: Tank equipment or full tank shot

### Product Images (coral-1.jpg through coral-8.jpg)
Choose your 8 best coral shots that show:
- Color variety
- Different coral types (LPS, SPS, soft corals)
- Clear, focused images
- Good lighting

## Quick Setup Steps

1. **Download all images** from [your Google Drive folder](https://drive.google.com/drive/folders/1Fv0h8VMPhkSmNno-NZB8lbt9MQPvudZl?usp=sharing)

2. **Create images folder**: 
   - Inside your `neon-reef-co` folder, create a folder named `images`

3. **Rename files** according to the structure above

4. **Optimize images** (optional but recommended):
   - Resize to max 1200px width
   - Compress using [TinyPNG](https://tinypng.com/)
   - This will make your site load faster

## Adding More Products Later

To add more coral products, simply:
1. Add new images to the `images/` folder
2. Copy a product card in `index.html`
3. Update the image source, title, and price

## GitHub Upload

When uploading to GitHub:
1. Upload the transparent `logo.png` to the main folder
2. Create an `images` folder and upload all coral images there
3. The website will automatically display them

## Image Not Showing?

If images don't appear:
- Check file names match exactly (case-sensitive)
- Ensure images are in the `images/` folder
- Verify file extensions (.jpg vs .jpeg)
- Clear browser cache (Ctrl+F5)

---

Your website is now ready to showcase your beautiful corals with a professional, transparent logo! 