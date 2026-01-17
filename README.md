# Quarto Blog Project

A simple and elegant blog built with Quarto.

## Prerequisites

- [Quarto](https://quarto.org/docs/get-started/) installed on your system
- (Optional) Python or R if you want to include executable code

### Install Quarto

**macOS:**

```bash
brew install quarto
```

**Or download from:** <https://quarto.org/docs/get-started/>

## Project Structure

```
quarto-blog/
├── _quarto.yml          # Main configuration file
├── index.qmd            # Home page with blog listing
├── about.qmd            # About page
├── styles.css           # Custom CSS styles
├── posts/               # All blog posts go here
│   └── welcome/         # Example post folder
│       └── index.qmd    # Post content
└── README.md            # This file
```

## Building and Running

### Preview Locally

```bash
cd quarto-blog
quarto preview
```

This will start a local server (usually at <http://localhost:4444>) and automatically reload when you make changes.

### Build the Site

```bash
quarto render
```

This generates the static site in the `docs/` directory (configured for GitHub Pages).

### Generate HTML for GitHub Pages

To generate both HTML and PDF files in the `docs` folder for GitHub Pages deployment:

```bash
quarto render
```

This will create:
- HTML files for the website
- PDF versions of individual blog posts

Then commit and push:

```bash
git add docs/
git commit -m "Build site with PDFs"
git push
```

**GitHub Pages Setup:**

1. Go to your repository Settings → Pages
2. Under "Source", select "Deploy from a branch"
3. Select branch: `main` and folder: `/docs`
4. Click Save

Your site will be live at: `https://[username].github.io/[repository-name]/`
PDF versions will be available at: `https://[username].github.io/[repository-name]/posts/[post-name]/index.pdf`

## Adding New Blog Posts

### Method 1: Manual Creation

1. Create a new folder in `posts/` directory:

   ```bash
   mkdir posts/my-new-post
   ```

2. Create an `index.qmd` file inside:

   ```bash
   touch posts/my-new-post/index.qmd
   ```

3. Add frontmatter and content:

   ```yaml
   ---
   title: "My New Post Title"
   author: "Your Name"
   date: "2024-01-20"
   categories: [category1, category2]
   image: "thumbnail.jpg"
   ---

   ## Your content here

   Write your blog post using Markdown...
   ```

### Method 2: Quick Command

```bash
cd posts
mkdir my-new-post && cd my-new-post
cat > index.qmd << 'EOF'
---
title: "My New Post"
author: "Your Name"
date: "2024-01-20"
categories: [general]
---

## Introduction

Your content here...
EOF
```

## Frontmatter Options

Essential fields for each blog post:

```yaml
---
title: "Post Title"              # Required
author: "Author Name"            # Optional
date: "YYYY-MM-DD"              # Required for sorting
categories: [cat1, cat2]        # Optional, for filtering
image: "thumbnail.jpg"          # Optional, featured image
description: "Short summary"    # Optional, for previews
draft: false                    # Optional, set true to hide
---
```

## Customization

### Change Theme

Edit `_quarto.yml`:

```yaml
format:
  html:
    theme: [cosmo, flatly, darkly, etc.]
```

Available themes: cosmo, flatly, darkly, journal, lumen, minty, pulse, sandstone, simplex, sketchy, slate, solar, spacelab, superhero, united, yeti

### Modify Navigation

Edit `_quarto.yml` under `website.navbar`:

```yaml
website:
  navbar:
    left:
      - href: index.qmd
        text: Home
      - about.qmd
      - href: posts.qmd
        text: Archive
```

### Custom Styling

Edit `styles.css` to add your custom CSS.

## Publishing

### GitHub Pages (Using docs folder)

The site is configured to build to the `docs/` folder for easy GitHub Pages deployment.

**Steps:**

1. Build your site:

   ```bash
   quarto render
   ```

2. Commit and push the docs folder:

   ```bash
   git add docs/
   git commit -m "Deploy site"
   git push
   ```

3. Enable GitHub Pages:
   - Go to repository Settings → Pages
   - Source: Deploy from a branch
   - Branch: `main`, Folder: `/docs`
   - Save

## Troubleshooting

**Preview not working?**

- Check if Quarto is installed: `quarto --version`
- Ensure you're in the project directory

**Posts not showing?**

- Verify the date format is `YYYY-MM-DD`
- Check that `index.qmd` exists in the post folder
- Ensure frontmatter is valid YAML

**Styling issues?**

- Clear browser cache
- Rebuild: `quarto render`

## Resources

- [Quarto Documentation](https://quarto.org/docs/guide/)
- [Quarto Blog Guide](https://quarto.org/docs/websites/website-blog.html)
- [Markdown Guide](https://www.markdownguide.org/)

## License

MIT License - Feel free to use and modify!
