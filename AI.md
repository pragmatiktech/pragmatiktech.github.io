# AI.md - Project Documentation and Maintenance Notes

## Project Overview

**pragmatik.tech** is a technical blog/website built with Quarto, focused on:
- Embedded systems programming (TinyGo, MicroPython, Raspberry Pi Pico)
- Generative AI programming (Java with LangChain4J, Python)
- Machine learning (planned content)

## Technical Stack

- **Framework**: Quarto (static site generator)
- **Hosting**: GitHub Pages (pragmatiktech.github.io)
- **Domain**: pragmatik.tech
- **Content**: Markdown/QMD files
- **Theme**: United theme with custom CSS
- **Fonts**: Space Grotesk (main), Fira Code (code blocks)

## Project Structure

```
pragmatiktech.github.io/
├── _quarto.yml          # Main Quarto configuration
├── _publish.yml         # Publishing configuration
├── index.qmd           # Homepage with article listings
├── about.qmd           # About page
├── styles.css          # Custom CSS styles
├── embedded/           # Embedded systems articles
│   ├── setting-up-tinygo.qmd
│   ├── blinking-an-led.md
│   ├── gpio-and-interrupts.qmd
│   ├── channels.qmd
│   └── concurrency-goroutines.md
├── static/             # Static assets (images, etc.)
├── .github/            # GitHub Actions workflows
└── _site/              # Generated site (auto-generated)
```

## Key Configuration Details

### Website Configuration
- Site URL: https://pragmatik.tech
- Preview port: 2805
- Navbar: Dark theme with logo, social links (YouTube, GitHub, LinkedIn)
- Sidebar: Floating style with embedded systems section
- Footer: Copyright, Creative Commons license, social links

### Content Organization
- Articles are organized by topic (embedded/, future: ai/, ml/)
- Homepage shows recent articles in grid format (2 columns, max 10 items)
- Automatic listing generation from QMD/MD files
- Categories and tags supported

### Branding
- Logo: `/static/images/pragmatik-logo-inverse.png`
- Profile image: `/static/images/profile.png`
- Favicon: `/favicon.ico`
- Color scheme: Dark navbar, custom CSS theming

## Author Information
- **Name**: Charath Ranganathan
- **Role**: CTO at CoreStory
- **Background**: 4+ decades of programming experience
- **Interests**: Embedded systems, AI/ML, flight instruction
- **Social**: 
  - YouTube: @pragmatiktech
  - LinkedIn: /in/charath
  - GitHub: pragmatiktech

## Development Workflow

### Adding New Articles
1. Create `.qmd` or `.md` file in appropriate directory
2. Include frontmatter with title, date, categories
3. Content automatically appears in listings
4. Build with `quarto render`
5. Publish to GitHub Pages

### Maintenance Tasks
- Keep embedded systems content current with TinyGo/MicroPython updates
- Add new AI/ML content as planned
- Monitor and update dependencies
- Ensure social links remain active

## Technical Notes

### Quarto Features Used
- Website project type
- Automatic listings
- Custom CSS theming
- Code syntax highlighting
- Social media integration
- Creative Commons licensing

### Performance Considerations
- Static site generation for fast loading
- Optimized Google Fonts loading
- Efficient CSS organization
- Image optimization in static assets

### SEO & Accessibility
- Proper heading structure
- Alt text for images
- Semantic HTML from Quarto
- Mobile-responsive design
- External links open in new windows

## Future Enhancements
1. Add AI/ML content sections
2. Implement search functionality
3. Add RSS feed
4. Enhance social sharing
5. Add comment system
6. Create video embedding for YouTube content
7. Add newsletter signup
8. Implement analytics

## Deployment

The site uses a two-stage deployment process following the [Quarto Netlify GitHub Action workflow](https://quarto.org/docs/publishing/netlify.html#github-action):

1. **GitHub Actions**: Renders the site and publishes to `gh-pages` branch
   - Triggered on push to `main` branch or manual workflow dispatch
   - Uses `quarto-dev/quarto-actions/publish@v2` with `target: gh-pages`
   - Requires `GITHUB_TOKEN` secret (automatically provided)
   
2. **Netlify**: Deploys the `gh-pages` branch content
   - Netlify is connected to the `gh-pages` branch of the repository
   - Custom domain (pragmatik.tech) configured via CNAME
   - Uses Netlify's build plugin for Quarto: `@quarto/netlify-plugin-quarto`

### Key Configuration Files
- `.github/workflows/publish.yml` - GitHub Action workflow
- `netlify.toml` - Netlify build plugin configuration  
- `package.json` - Netlify plugin dependency
- `CNAME` - Custom domain configuration

## Key Files to Monitor
- `_quarto.yml` - Main configuration
- `index.qmd` - Homepage content and listings
- `about.qmd` - Author information
- `styles.css` - Custom styling
- Articles in `embedded/` directory

Last updated: 2024