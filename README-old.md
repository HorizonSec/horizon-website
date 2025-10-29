# The HorizonSec Project Website



The official website for The HorizonSec Project - open source security tools designed for builders. Official website for The HorizonSec Project - Open-source, modular security framework for modern application development.



## Project Structure## About



```This is the official website showcasing The HorizonSec Project - a comprehensive open-source security framework designed to make security transparent, actionable, and accessible to builders of all levels.

horizon-website/

├── index.html                 # Homepage## About The HorizonSec Project

├── assets/                    # Static assets

│   ├── css/The HorizonSec Project provides modular security tools that integrate directly into your development workflow:

│   │   └── styles.css        # Main stylesheet

│   ├── js/- **🌍 GAIA Framework**: Security orchestration and management

│   │   └── main.js           # Common JavaScript functionality- **🌱 DEMETER**: Infrastructure security scanning

│   └── images/- **💀 HADES**: Endpoint security and runtime monitoring  

│       ├── logos/            # Logo files- **🏹 ARTEMIS**: Static code analysis

│       │   └── horizonSecLogo.png

│       ├── founders/         # Founder photos and team images## Website Features

│       └── icons/            # Icon assets (SVG, PNG)

├── pages/                     # Interior pages- **Comprehensive Content**: Complete information about all HorizonSec modules, features, and roadmap

│   ├── about.html            # About page- **Modern Design**: Dark theme with cybersecurity-focused color palette (cyan/blue accents)

│   ├── features.html         # Features overview- **Responsive Layout**: Mobile-first design that works on all devices

│   ├── getting-started.html  # Getting started guide- **Complete Sections**:

│   ├── roadmap.html         # Project roadmap  - Hero section with project overview

│   ├── community.html       # Community information  - Problem/solution narrative

│   └── faq.html             # Frequently asked questions  - Framework modules showcase

└── README.md                 # This file  - Features and capabilities

```  - Getting started guide

  - Project roadmap

## About The HorizonSec Project  - Community information

  - FAQ section

The HorizonSec Project provides modular security tools that integrate directly into your development workflow:- **Automated Deployment**: GitHub Actions workflow for continuous deployment



- **🌍 GAIA Framework**: Security orchestration and management## Local Development

- **🌱 DEMETER**: Infrastructure security scanning

- **💀 HADES**: Endpoint security and runtime monitoring  To test the website locally:

- **🏹 ARTEMIS**: Static code analysis

```bash

## File Organization Best Practices# Using Python 3

python3 -m http.server 8080

### Assets Directory (`/assets/`)

# Then visit http://localhost:8080 in your browser

- **CSS**: All stylesheets in `assets/css/````

- **JavaScript**: All JS files in `assets/js/`

- **Images**: Organized by type in `assets/images/`## GitHub Pages Setup

  - `logos/`: Brand logos and variants

  - `founders/`: Team member photosTo deploy this website on GitHub Pages:

  - `icons/`: UI icons and symbols

1. Go to **Repository Settings** → **Pages**

### Pages Directory (`/pages/`)2. Under **Source**, select the branch you want to deploy (e.g., `main`)

3. Keep the folder as **/ (root)**

All interior pages (non-homepage) are stored here to keep the root directory clean.4. Click **Save**

5. The site will be available at `https://horizonsec.github.io/horizon-website/`

### Path References

## Domain Configuration

- **From root (`index.html`)**: Use `assets/` and `pages/` prefixes

- **From pages**: Use `../assets/` for assets and relative paths for other pagesTo point your Namecheap domain to GitHub Pages:



## Development1. In Namecheap, go to **Domain List** → **Manage** → **Advanced DNS**

2. Add these records:

### Local Development   - **A Record**: Host `@`, Value `185.199.108.153`

   - **A Record**: Host `@`, Value `185.199.109.153`

1. Clone the repository   - **A Record**: Host `@`, Value `185.199.110.153`

2. Open `index.html` in a web browser   - **A Record**: Host `@`, Value `185.199.111.153`

3. For development with live reload, use a local server:   - **CNAME Record**: Host `www`, Value `horizonsec.github.io`

   ```bash3. In GitHub repository settings → Pages, add your custom domain

   # Using Python4. Enable **Enforce HTTPS**

   python -m http.server 8000

   ## File Structure

   # Using Node.js (if you have http-server installed)

   npx http-server```

   ```.

├── index.html      # Main HTML file with all content

### File Naming Conventions├── styles.css      # Stylesheet with responsive design

├── .gitignore      # Git ignore rules

- **HTML files**: lowercase with hyphens (e.g., `getting-started.html`)└── README.md       # This file

- **CSS files**: lowercase with hyphens (e.g., `main-styles.css`)```

- **JavaScript files**: lowercase with hyphens (e.g., `navigation-handler.js`)

- **Images**: descriptive names with hyphens## Technologies

  - Founders: `founder-lastname-firstname.jpg`

  - Icons: `icon-feature-name.svg`- HTML5

- CSS3 (with Flexbox and Grid)

### Adding New Content- Responsive design with media queries

- No external dependencies or frameworks

#### Adding a New Page

## License

1. Create the HTML file in the `pages/` directory

2. Use relative paths: `../assets/css/styles.css` for CSSCopyright © 2025 HorizonSec.org. All rights reserved.

3. Use relative paths: `../assets/js/main.js` for JavaScript
4. Update navigation in all files to include the new page

#### Adding Images

1. Place in appropriate subdirectory under `assets/images/`
2. Use descriptive filenames
3. Optimize images for web (compress, appropriate dimensions)
4. Add to relevant README files in image directories

#### Adding Styles

1. Add to `assets/css/styles.css`
2. Follow existing CSS organization and naming conventions
3. Use CSS custom properties (variables) defined in `:root`

## Website Features

- **Comprehensive Content**: Complete information about all HorizonSec modules, features, and roadmap
- **Modern Design**: Dark theme with cybersecurity-focused color palette (cyan/blue accents)
- **Responsive Layout**: Mobile-first design that works on all devices
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
- Responsive design with media queries
- No external dependencies or frameworks

## License

Copyright © 2025 HorizonSec.org. All rights reserved.
