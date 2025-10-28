# The HorizonSec Project Website

Official website for The HorizonSec Project - Open-source, modular security framework for modern application development.

## About

This is the official website showcasing The HorizonSec Project - a comprehensive open-source security framework designed to make application security transparent, actionable, and accessible to builders of all levels.

## About The HorizonSec Project

The HorizonSec Project provides modular security tools that integrate directly into your development workflow:

- **🌍 GAIA Framework**: Security orchestration and management
- **🌱 DEMETER**: Infrastructure security scanning
- **💀 HADES**: Endpoint security and runtime monitoring  
- **🏹 ARTEMIS**: Static code analysis

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
- **Automated Deployment**: GitHub Actions workflow for continuous deployment

## Local Development

To test the website locally:

```bash
# Using Python 3
python3 -m http.server 8080

# Then visit http://localhost:8080 in your browser
```

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

## File Structure

```
.
├── index.html      # Main HTML file with all content
├── styles.css      # Stylesheet with responsive design
├── .gitignore      # Git ignore rules
└── README.md       # This file
```

## Technologies

- HTML5
- CSS3 (with Flexbox and Grid)
- Responsive design with media queries
- No external dependencies or frameworks

## License

Copyright © 2025 HorizonSec.org. All rights reserved.
