# Kynowa Branding & Logo Guide

## Overview
This guide explains how to replace the favicon, logos, and branding images for your Kynowa website.

## 1. Favicon (Browser Tab Icon)

### Current Location
`public/favicon.svg`

### How to Replace

**Option A: SVG Favicon (Recommended)**
1. Create or obtain your Kynowa logo as an SVG file
2. Save it as `favicon.svg`
3. Replace the existing file at `public/favicon.svg`

**Option B: PNG Favicon**
1. Create a square PNG image (recommended: 512x512px or 256x256px)
2. Save it as `favicon.png`
3. Place it in the `public/` directory
4. Update the reference in `src/layouts/Layout.astro` line 32:
   ```html
   <!-- Change from: -->
   <link rel="icon" type="image/svg+xml" href="/favicon.svg" />

   <!-- To: -->
   <link rel="icon" type="image/png" href="/favicon.png" />
   ```

**Option C: Multi-format Favicon (Best Practice)**
For maximum compatibility, use multiple formats:

1. Create these files:
   - `favicon.ico` (16x16, 32x32, 48x48 multi-size)
   - `favicon-16x16.png` (16x16)
   - `favicon-32x32.png` (32x32)
   - `apple-touch-icon.png` (180x180 for Apple devices)

2. Place all files in the `public/` directory

3. Update `src/layouts/Layout.astro` to include:
   ```html
   <link rel="icon" type="image/x-icon" href="/favicon.ico" />
   <link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png" />
   <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png" />
   <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png" />
   ```

### Free Tools for Creating Favicons
- **Favicon.io**: https://favicon.io/ (Generate from text, image, or emoji)
- **RealFaviconGenerator**: https://realfavicongenerator.net/ (Generate all sizes)
- **Canva**: https://www.canva.com/ (Design custom icon)

---

## 2. Logo in Navigation Bar

### Current Location
The logo text "Kynowa" appears in `src/components/navbar/navbar.astro` (lines 32-33)

### How to Replace Text Logo with Image Logo

1. **Prepare your logo image:**
   - Recommended format: SVG (scalable) or PNG with transparent background
   - Recommended height: 40-50px (width can vary)
   - Save as `logo.svg` or `logo.png` in the `public/` directory

2. **Update the navbar component:**

   Edit `src/components/navbar/navbar.astro` line 32-33:

   ```astro
   <!-- Current text logo: -->
   <a href="/" class="text-lg">
     <span class="font-bold text-slate-800">Kynowa</span>
   </a>

   <!-- Replace with image logo: -->
   <a href="/" class="flex items-center">
     <img src="/logo.svg" alt="Kynowa" class="h-10 w-auto" />
   </a>
   ```

### Dark Background Logo Option
If you need a different logo for dark backgrounds:

```astro
<a href="/" class="flex items-center">
  <img
    src="/logo.svg"
    alt="Kynowa"
    class="h-10 w-auto dark:hidden"
  />
  <img
    src="/logo-white.svg"
    alt="Kynowa"
    class="h-10 w-auto hidden dark:block"
  />
</a>
```

---

## 3. Social Media Preview Image (Open Graph)

### Current Location
`public/opengraph.jpg`

### What is this?
When someone shares your website on social media (Facebook, Twitter, LinkedIn), this image appears as the preview.

### How to Replace

1. **Create an image with these specs:**
   - Dimensions: 1200x630px (Facebook/LinkedIn standard)
   - Format: JPG or PNG
   - Content: Your logo + tagline or key message
   - File size: Keep under 1MB

2. **Save and replace:**
   - Save your image as `opengraph.jpg` or `opengraph.png`
   - Replace the existing file at `public/opengraph.jpg`

3. **If you change the filename:**
   - Update `src/layouts/Layout.astro` line 16:
   ```javascript
   // Change from:
   const resolvedImageWithDomain = new URL("/opengraph.jpg", Astro.site).toString();

   // To (if using PNG):
   const resolvedImageWithDomain = new URL("/opengraph.png", Astro.site).toString();
   ```

### Design Tips for Open Graph Images
- Include your logo prominently
- Add a tagline: "IT Consulting & Cloud Solutions"
- Use Melbourne skyline or tech imagery
- Keep text large and readable (minimum 60px font)
- Use brand colors

### Free Tools for Creating Open Graph Images
- **Canva**: https://www.canva.com/ (Templates available)
- **Figma**: https://www.figma.com/ (Free design tool)
- **Adobe Express**: https://www.adobe.com/express/ (Quick templates)

---

## 4. Hero Image (Homepage Main Image)

### Current Location
`src/assets/hero.png`

### What is this?
The large image displayed on the right side of the homepage hero section.

### How to Replace

1. **Prepare your image:**
   - Recommended dimensions: 600x600px to 800x800px
   - Format: PNG (with transparency) or JPG
   - Content suggestions:
     - IT infrastructure illustration
     - Cloud computing graphic
     - Cybersecurity themed image
     - Professional team photo
     - Melbourne cityscape

2. **Add your image:**
   - Save your image in `src/assets/` directory
   - Name it something descriptive like `hero-kynowa.png`

3. **Update the hero component:**

   Edit `src/components/hero.astro` lines 3 and 12-13:

   ```astro
   // Change line 3:
   import heroImage from "@/assets/hero-kynowa.png";

   // Update alt text on line 13:
   alt="Kynowa IT Consulting Services"
   ```

### Free Stock Images
- **unDraw**: https://undraw.co/ (Customizable illustrations)
- **Unsplash**: https://unsplash.com/ (Free high-quality photos - search "technology")
- **Pexels**: https://www.pexels.com/ (Free stock photos)
- **Storyset**: https://storyset.com/ (IT/Tech illustrations)

---

## 5. Additional Branding Assets (Optional)

### Email Signature Logo
If you need a logo for email signatures:
- Create a PNG or JPG version
- Recommended dimensions: 300x100px or 400x150px
- Save in `public/` directory as `email-logo.png`

### Letterhead/Documents
For business documents:
- High-resolution PNG or PDF
- Minimum 300 DPI for printing
- Include ABN when available

---

## Quick Checklist

Before deploying, ensure you've updated:
- [ ] `public/favicon.svg` or `public/favicon.ico`
- [ ] `public/opengraph.jpg` - Social media preview image
- [ ] `src/assets/hero.png` - Homepage hero image
- [ ] Logo in navbar (if using image instead of text)
- [ ] Verify all images load correctly in development mode

---

## Testing Your Changes

1. **Start development server:**
   ```bash
   pnpm dev
   ```

2. **Check these locations:**
   - Browser tab for favicon
   - Homepage navigation bar for logo
   - Homepage hero section for main image
   - Inspect page `<head>` for Open Graph tags

3. **Test social media preview:**
   - Use Facebook Debugger: https://developers.facebook.com/tools/debug/
   - Use Twitter Card Validator: https://cards-dev.twitter.com/validator
   - Use LinkedIn Post Inspector: https://www.linkedin.com/post-inspector/

---

## File Summary

| Asset | Location | Purpose | Recommended Size |
|-------|----------|---------|------------------|
| Favicon | `public/favicon.svg` | Browser tab icon | 32x32px to 512x512px |
| Logo | `public/logo.svg` | Navigation bar | Height: 40-50px |
| Open Graph | `public/opengraph.jpg` | Social media preview | 1200x630px |
| Hero Image | `src/assets/hero.png` | Homepage main image | 600x800px |
| Apple Touch Icon | `public/apple-touch-icon.png` | iOS home screen | 180x180px |

---

## Need Help?

- **Astro Image Optimization Docs**: https://docs.astro.build/en/guides/images/
- **SVG Optimization**: https://jakearchibald.github.io/svgomg/
- **Image Compression**: https://tinypng.com/

All images in the `public/` directory are served as-is. Images in `src/assets/` are optimized by Astro during build.
