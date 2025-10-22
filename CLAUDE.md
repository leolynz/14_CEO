# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Digital Business Card (vCard)** HTML template called "Digi vCard" with a CEO theme. It's a standalone, static website template that requires no build process or package management.

**Template Name**: CEO Business Card Portfolio - Digi vCard
**Created By**: The_Krishna
**Type**: Static HTML/CSS/JavaScript template

## Architecture

### Page Structure

The template consists of 3 main HTML pages:

1. **index.html** - Main landing page with full vCard profile
2. **blog.html** - Dedicated blog listing page
3. **product.html** - Products listing page

All pages share the same layout structure:
- Common preloader animation (`.darksoul-layout`)
- Background animated circles (`.area > .circles`)
- Bootstrap modal system for popups
- Consistent header/footer structure

### Asset Organization

```
assets/
├── css/          # Stylesheets (Bootstrap, custom styles, plugins)
├── js/           # JavaScript libraries and custom scripts
├── images/       # Photos, backgrounds, icons (PNG/JPG)
├── svg/          # Vector icons and graphics
├── webfonts/     # Custom font files
└── contact/      # Contact-related assets
```

### Key Dependencies

**CSS Libraries:**
- Bootstrap 5 (bootstrap.min.css)
- Magnific Popup (lightbox functionality)
- Slick Carousel (sliders)
- Custom cursor styles
- Font Awesome icons (all.min.css)
- Google Fonts: Poppins (all weights)

**JavaScript Libraries:**
- jQuery 3.x
- jQuery UI (datepicker)
- Bootstrap 5 Bundle
- Slick Slider
- Magnific Popup
- Custom cursor.js (651KB - custom cursor effects)

### Custom JavaScript (custom.js)

Located at `assets/js/custom.js`, handles:

1. **Preloader**: 1s delay + 800ms fadeout on window load
2. **Slick Sliders**:
   - `.blog-bottom-sec` - Blog carousel (variableWidth)
   - `.product-bottom-sec` - Products slider (1.5 slides visible)
   - `.gallery-bottom` - Gallery slider (2 slides on desktop, 1 on mobile)
3. **QR Code Functions**:
   - `downloadImage()` - Downloads scanner-img.png
   - `shareImage()` - Uses Web Share API (note: hardcoded path needs updating)

### Main Page Sections (index.html)

The main vCard page is structured with these key sections in order:

1. **Header** - Logo + language selector dropdown (10 languages)
2. **Hero Section** - Background image with profile photo
3. **Profile** - Name (Jordan Smith) + title (CEO)
4. **Social Icons** - 8 social media links
5. **About Me** - Personal bio section
6. **Services** - 4 service cards with images
7. **Make an Appointment** - Date/time picker form
8. **Gallery** - Image gallery with Magnific Popup lightbox
9. **Products** - Product cards with pricing (opens modal)
10. **Testimonials** - Customer reviews carousel
11. **Blog** - Latest news preview (opens modal)
12. **Inquiries** - Contact form (name, phone, email, message)
13. **Contact Me** - Contact details (email, phone, office, hours)
14. **Map** - Google Maps embed
15. **Bottom Actions** - QR scan, share, add to contact buttons
16. **Footer** - Credits

### Modal System

The template uses Bootstrap 5 modals:

- `#blog-modal` - Full blog post view with images and structured content
- `#product-modal` - Product purchase form (name, email, phone, address, payment)
- `#scan-modal` - QR code scanner with download/share buttons
- `#share-media-modal` - Social media sharing options

## Customization Points

### Profile Information

**Primary contact details** appear in multiple locations:
- Profile section: index.html:111-112
- Contact section: index.html:488-568
- Social media links: index.html:116-157
- Footer contact: index.html:589 (tel link), index.html:495 (email)

**Current placeholder data:**
- Name: Jordan Smith
- Email: jordan.smith@mail.com
- Phone: +1 234 567 8900
- Office: (555) 555-1234
- Address: 121 Parkview Street, ST Nova, New York

### Language Selector

The dropdown at index.html:58-95 is non-functional (all links are `javascript:void(0)`). To implement multi-language support, you would need to:
1. Add language files (JSON or JS objects)
2. Integrate language.js (exists but currently unused)
3. Wire up dropdown click handlers

### QR Code Scanner

The scanner image path is hardcoded:
- Display: `assets/images/main-img/scanner-img.png`
- Share function path: Line 68 of custom.js has incorrect path (`/envato/digi-vcard/CEO/...`)

**To fix**: Update the `shareImage()` function to use relative path or current domain.

### Forms Behavior

All forms currently use `javascript:void(0)` - they do not submit anywhere:
- Appointment form (index.html:211-245)
- Inquiry form (index.html:444-479)
- Product purchase modal form (index.html:689-725)

To make functional, add:
- Form validation
- AJAX submission or server-side endpoint
- Success/error feedback

### Google Maps

Current embed shows: 121 Parkview St, Newburgh, NY (index.html:574-576)

To change location:
1. Get new Google Maps embed code
2. Replace entire `<iframe>` element

## Common Tasks

### Changing Profile Photo

Replace: `assets/images/main-img/profile.png` (index.html:108)

### Updating Services

Services section (index.html:172-203) has 4 service cards. Each contains:
- Image: `assets/images/services/servicesN.png`
- Title (h3)
- Description (p)

### Adding Products

Products use Slick slider (index.html:293-324). Each product needs:
- Image in `assets/images/product/`
- Title, description, price
- Modal trigger: `data-bs-toggle="modal" data-bs-target="#product-modal"`

### Modifying Gallery

Gallery images (index.html:254-286) use Magnific Popup. Structure:
```html
<div class="gallery-item">
  <div class="gallery-box">
    <div class="gallery-img"><img src="path" alt=""></div>
    <a href="path" class="img-zoom">
      <div class="gallery-detail"><img src="assets/svg/plus-icon.svg"></div>
    </a>
  </div>
</div>
```

### Styling Customization

Main custom styles: `assets/css/style.css`
Responsive adjustments: `assets/css/media-query.css`

The template uses utility classes:
- `mt-5`, `mt-10`, `mt-15`, `mt-20`, `mt-24`, `mt-30` - margin-top
- `w-100` - width 100%
- `container` - Bootstrap container

## Browser Compatibility Notes

- Preloader uses CSS Grid (`.darksoul-grid`)
- Web Share API (`navigator.share`) only works on mobile browsers and HTTPS
- Background animations use CSS animations (`.circles li`)
- Date picker requires jQuery UI
- All modern features - IE11 not supported
