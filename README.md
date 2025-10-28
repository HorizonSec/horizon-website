# HorizonSec Project Website

The official website for The HorizonSec Project - open source security tools designed for builders.

## Project Structure

```
horizon-website/
├── index.html                 # Homepage
├── assets/                    # Static assets
│   ├── css/
│   │   ├── base.css          # Shared styles (variables, typography, header, footer)
│   │   ├── home.css          # Homepage-specific styles
│   │   ├── about.css         # About page-specific styles
│   │   ├── features.css      # Features page-specific styles
│   │   ├── getting-started.css # Getting started page-specific styles
│   │   ├── roadmap.css       # Roadmap page-specific styles
│   │   ├── community.css     # Community page-specific styles
│   │   └── faq.css           # FAQ page-specific styles
│   ├── js/
│   │   └── main.js           # Common JavaScript functionality
│   └── images/
│       ├── logos/            # Logo files
│       │   └── horizonSecLogo.png
│       ├── founders/         # Founder photos and team images
│       └── icons/            # Icon assets (SVG, PNG)
├── pages/                     # Interior pages
│   ├── about.html            # About page
│   ├── features.html         # Features overview
│   ├── getting-started.html  # Getting started guide
│   ├── roadmap.html         # Project roadmap
│   ├── community.html       # Community information
│   └── faq.html             # Frequently asked questions
└── README.md                 # This file
```

## About The HorizonSec Project

The HorizonSec Project provides modular security tools that integrate directly into your development workflow:

- **🌍 GAIA Framework**: Security orchestration and management
- **🌱 DEMETER**: Infrastructure security scanning
- **💀 HADES**: Endpoint security and runtime monitoring  
- **🏹 ARTEMIS**: Static code analysis

## CSS Architecture

The website now uses a modular CSS architecture for better maintainability and scalability:

### **Base Styles (`base.css`)**
Contains shared styles used across all pages:
- CSS Reset and variables
- Typography system
- Header and navigation
- Footer
- Button styles
- Page hero sections
- Responsive breakpoints

### **Page-Specific Styles**
Each page has its own CSS file containing only the styles needed for that page:
- `home.css` - Homepage hero, problem/solution sections, community preview
- `about.css` - Mission section, founders, framework modules
- `features.css` - Feature categories, integration requests, coming soon sections
- `getting-started.css` - Installation guides, code blocks, stay updated section
- `roadmap.css` - Timeline, milestones, progress bars, version cards
- `community.css` - Community channels, contribution guides, contact options
- `faq.css` - FAQ navigation, expandable items, search functionality

### **Benefits of This Architecture**
- **Faster Loading**: Pages only load the CSS they need
- **Better Maintenance**: Easier to find and update page-specific styles
- **Scalability**: Easy to add new pages without bloating existing CSS
- **Development**: Reduced CSS conflicts and better code organization
- **Performance**: Smaller file sizes for better user experience

## File Organization Best Practices

### **Assets Directory (`/assets/`)**

- **CSS**: Modular stylesheets in `assets/css/`
- **JavaScript**: All JS files in `assets/js/`
- **Images**: Organized by type in `assets/images/`
  - `logos/`: Brand logos and variants
  - `founders/`: Team member photos
  - `icons/`: UI icons and symbols

### **Pages Directory (`/pages/`)**

All interior pages (non-homepage) are stored here to keep the root directory clean.

### **Path References**

- **From root (`index.html`)**: Use `assets/` and `pages/` prefixes
- **From pages**: Use `../assets/` for assets and relative paths for other pages

## Development

### Local Development

1. Clone the repository
2. Open `index.html` in a web browser
3. For development with live reload, use a local server:
   ```bash
   # Using Python
   python -m http.server 8000
   
   # Using Node.js (if you have http-server installed)
   npx http-server
   ```

### File Naming Conventions

- **HTML files**: lowercase with hyphens (e.g., `getting-started.html`)
- **CSS files**: lowercase with hyphens (e.g., `getting-started.css`)
- **JavaScript files**: lowercase with hyphens (e.g., `navigation-handler.js`)
- **Images**: descriptive names with hyphens
  - Founders: `founder-lastname-firstname.jpg`
  - Icons: `icon-feature-name.svg`

### Adding New Content

#### Adding a New Page

1. Create the HTML file in the `pages/` directory
2. Create a corresponding CSS file in `assets/css/`
3. Include both `base.css` and your page-specific CSS:
   ```html
   <link rel="stylesheet" href="../assets/css/base.css">
   <link rel="stylesheet" href="../assets/css/your-page.css">
   ```
4. Use relative paths: `../assets/js/main.js` for JavaScript
5. Update navigation in all files to include the new page

#### Adding Images

1. Place in appropriate subdirectory under `assets/images/`
2. Use descriptive filenames
3. Optimize images for web (compress, appropriate dimensions)
4. Add to relevant README files in image directories

#### Adding Styles

1. **Shared styles**: Add to `assets/css/base.css`
2. **Page-specific styles**: Add to the relevant page CSS file
3. Follow existing CSS organization and naming conventions
4. Use CSS custom properties (variables) defined in `:root`

## Website Features

- **Comprehensive Content**: Complete information about all HorizonSec modules, features, and roadmap
- **Modern Design**: Dark theme with cybersecurity-focused color palette (cyan/blue accents)
- **Responsive Layout**: Mobile-first design that works on all devices
- **Modular CSS**: Page-specific stylesheets for optimal performance
- **Complete Sections**:
  - Hero section with project overview
  - Problem/solution narrative
  - Framework modules showcase
  - Features and capabilities
  - Getting started guide
  - Project roadmap
  - Community information
  - FAQ section

## GitHub Pages Setup

To deploy this website on GitHub Pages:

1. Go to **Repository Settings** → **Pages**
2. Under **Source**, select the branch you want to deploy (e.g., `main`)
3. Keep the folder as **/ (root)**
4. Click **Save**
5. The site will be available at `https://horizonsec.github.io/horizon-website/`

## Domain Configuration

To point your Namecheap domain to GitHub Pages:

1. In Namecheap, go to **Domain List** → **Manage** → **Advanced DNS**
2. Add these records:
   - **A Record**: Host `@`, Value `185.199.108.153`
   - **A Record**: Host `@`, Value `185.199.109.153`
   - **A Record**: Host `@`, Value `185.199.110.153`
   - **A Record**: Host `@`, Value `185.199.111.153`
   - **CNAME Record**: Host `www`, Value `horizonsec.github.io`
3. In GitHub repository settings → Pages, add your custom domain
4. Enable **Enforce HTTPS**

## Browser Compatibility

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile responsive design
- Progressive enhancement approach

## Technologies

- HTML5
- CSS3 (with Flexbox and Grid)
- Vanilla JavaScript
- Modular CSS architecture
- Responsive design with media queries
- No external dependencies or frameworks

## License

Copyright © 2025 HorizonSec.org. All rights reserved.