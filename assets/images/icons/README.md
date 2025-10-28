# Icons Directory

This directory contains icon files used throughout the HorizonSec website.

## File Organization

- `favicon.ico` - Website favicon
- `feature-icons/` - Icons for feature sections
- `social-icons/` - Social media platform icons
- `ui-icons/` - User interface icons (arrows, checkmarks, etc.)

## Icon Specifications

- **Format**: SVG preferred for scalability, PNG for complex icons
- **Size**: 
  - SVG: Viewbox optimized
  - PNG: 32x32, 64x64, 128x128 variants
- **Style**: Consistent with brand guidelines
- **Color**: Use CSS variables for theming when possible

## Usage

Icons should be implemented using:
1. Inline SVG for icons that need styling
2. `<img>` tags for static icons
3. CSS background-image for decorative icons