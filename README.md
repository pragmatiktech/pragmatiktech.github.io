# pragmatik.tech

A technical blog and educational website focused on embedded systems programming, generative AI, and machine learning, built with Quarto and hosted on Netlify.

## 🚀 About

**pragmatik.tech** is dedicated to sharing knowledge and tutorials on cutting-edge technology topics:

- **Embedded Systems**: Programming with TinyGo and MicroPython, with emphasis on Raspberry Pi Pico
- **Generative AI**: Programming in Java (using LangChain4J) and Python
- **Machine Learning**: Coming soon

Visit the live site: [https://pragmatik.tech](https://pragmatik.tech)

## 🛠️ Technical Stack

- **Framework**: [Quarto](https://quarto.org/) - Open-source scientific and technical publishing system
- **Hosting**: Netlify (deployed from GitHub `gh-pages` branch)
- **CI/CD**: GitHub Actions for automated rendering and publishing
- **Content**: Markdown (.md) and Quarto Markdown (.qmd) files
- **Theme**: United theme with custom CSS styling
- **Fonts**: Space Grotesk (main), Fira Code (code blocks)

## 📁 Project Structure

```
pragmatiktech.github.io/
├── _quarto.yml          # Main Quarto configuration
├── _publish.yml         # Publishing configuration  
├── index.qmd           # Homepage with article listings
├── about.qmd           # About page
├── styles.css          # Custom CSS styles
├── netlify.toml        # Netlify build plugin configuration
├── embedded/           # Embedded systems articles
│   ├── setting-up-tinygo.qmd
│   ├── blinking-an-led.md
│   ├── gpio-and-interrupts.qmd
│   ├── channels.qmd
│   └── concurrency-goroutines.md
├── static/             # Static assets (images, logos, etc.)
│   └── images/
├── .github/            # GitHub Actions workflows
├── _site/              # Generated site output (auto-generated)
└── package.json        # Node.js dependencies
```

## 🚀 Getting Started

### Prerequisites

- [Quarto](https://quarto.org/docs/get-started/) installed
- [Node.js](https://nodejs.org/) (for dependencies)

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/pragmatiktech/pragmatiktech.github.io.git
   cd pragmatiktech.github.io
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Preview the site locally**
   ```bash
   quarto preview
   ```
   The site will be available at `http://localhost:2805`

4. **Build the site**
   ```bash
   quarto render
   ```

### Adding New Content

1. **Create a new article**
   - Add a `.qmd` or `.md` file in the appropriate directory (e.g., `embedded/`)
   - Include proper frontmatter:
     ```yaml
     ---
     title: "Your Article Title"
     date: "2024-01-01"
     categories: ["embedded", "tinygo"]
     image: "/static/images/your-image.png"
     ---
     ```

2. **The article will automatically appear** in the homepage listings and navigation

## 🎨 Customization

### Styling
- Main styles: `styles.css`
- Theme: United (configured in `_quarto.yml`)
- Custom fonts loaded from Google Fonts

### Configuration
- Website settings: `_quarto.yml`
- Publishing settings: `_publish.yml`
- Navigation and sidebar automatically generated

## 📝 Content Guidelines

- Use clear, descriptive titles
- Include relevant categories and tags
- Add cover images when possible
- Follow consistent formatting
- Include code examples with proper syntax highlighting
- Test all embedded code examples

## 🚢 Deployment

The site uses a two-stage deployment process following the [Quarto Netlify GitHub Action workflow](https://quarto.org/docs/publishing/netlify.html#github-action):

### Stage 1: GitHub Actions Rendering
1. Push changes to the `main` branch (or trigger manually)
2. GitHub Actions workflow (`.github/workflows/publish.yml`) runs automatically
3. Quarto renders the site and publishes to the `gh-pages` branch
4. Uses `freeze: auto` to cache computational results locally

### Stage 2: Netlify Deployment
1. Netlify monitors the `gh-pages` branch for changes
2. Netlify automatically deploys the pre-rendered content
3. Site is live at [https://pragmatik.tech](https://pragmatik.tech)
4. Uses the `@quarto/netlify-plugin-quarto` build plugin

### Key Configuration Files
- `.github/workflows/publish.yml` - GitHub Action for rendering
- `netlify.toml` - Netlify build plugin configuration
- `package.json` - Netlify plugin dependencies
- `CNAME` - Custom domain configuration

## 🔗 Social Links

- **YouTube**: [@pragmatiktech](https://youtube.com/@pragmatiktech)
- **GitHub**: [pragmatiktech](https://github.com/pragmatiktech)
- **LinkedIn**: [charath](https://linkedin.com/in/charath)

## 👨‍💻 Author

**Charath Ranganathan** - CTO at CoreStory, with 4+ decades of programming experience spanning from BASIC on handheld computers to modern embedded systems and AI development.

## 📄 License

Content is shared under [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/).

## 🤝 Contributing

While this is primarily a personal blog, suggestions and corrections are welcome:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 🐛 Issues

If you find any issues with the site, please [open an issue](https://github.com/pragmatiktech/pragmatiktech.github.io/issues) on GitHub.

---

Built with ❤️ using [Quarto](https://quarto.org/)