# HorizonSec Website

Official website for HorizonSec.org - A professional cybersecurity solutions provider.

## About

This is a static website hosted on GitHub Pages that mirrors to the HorizonSec.org domain via Namecheap DNS configuration.

## Features

- **Responsive Design**: Mobile-friendly layout that works on all devices
- **Modern UI**: Professional gradient color scheme with blue/dark theme
- **Complete Sections**:
  - Navigation header with smooth scrolling
  - Hero section with call-to-action
  - About section with company statistics
  - Services showcase (6 key offerings)
  - Contact information and form
  - Professional footer

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
