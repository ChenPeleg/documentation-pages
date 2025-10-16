# Agent Documentation for GitHub Copilot

This document provides comprehensive information for AI agents (like GitHub Copilot) to help build, maintain, and work with this repository.

## Project Overview

This is a **Jekyll-based documentation site** using the [Just the Docs](https://just-the-docs.github.io/just-the-docs/) theme. The site is automatically built and deployed to GitHub Pages via GitHub Actions.

**Live Site**: https://ChenPeleg.github.io/documentation-pages

## Technology Stack

- **Static Site Generator**: Jekyll 4.3
- **Theme**: Just the Docs (version 0.4.0.rc3)
- **Language**: Ruby 3.x
- **Deployment**: GitHub Pages via GitHub Actions
- **Package Manager**: Bundler

## Repository Structure

```
documentation-pages/
├── .github/
│   └── workflows/
│       └── pages.yml           # GitHub Actions workflow for deployment
├── _includes/                   # Jekyll includes (partials)
├── _sass/                       # Sass stylesheets
├── assets/
│   └── images/
│       └── logo.png            # Site logo
├── docs/                        # Documentation pages
│   ├── changecolor.md          # Page about color schemes
│   ├── documentations.md       # Documentation page
│   ├── hebrew.md               # Hebrew language example
│   └── folder/                 # Sub-folder for nested docs
├── _config.yml                  # Jekyll configuration file
├── Gemfile                      # Ruby dependencies
├── Gemfile.lock                # Locked dependency versions
├── index.md                     # Home page
├── favicon.ico                  # Site favicon
└── README.md                    # Repository README
```

## Building the Site

### Prerequisites

- Ruby 3.1 or higher
- Bundler gem

### Local Development

1. Install dependencies:
   ```bash
   bundle install
   ```

2. Build and serve the site locally:
   ```bash
   bundle exec jekyll serve
   ```
   The site will be available at `http://localhost:4000`

3. Build for production:
   ```bash
   bundle exec jekyll build
   ```
   Output will be in the `_site/` directory

### GitHub Actions Deployment

The site is automatically deployed when changes are pushed to the `main` branch. See `.github/workflows/pages.yml` for the workflow configuration.

## Configuration

### Site Configuration (_config.yml)

- **title**: "The pages tittle" (site title)
- **description**: "learning about Jekyll docs"
- **theme**: just-the-docs
- **logo**: "/assets/images/logo.png"
- **url**: https://ChenPeleg.github.io/documentation-pages

### Theme Customization

The site uses the Just the Docs theme which supports:
- Color schemes (light/dark)
- Navigation ordering via `nav_order` in front matter
- Custom layouts
- Search functionality

## Adding New Documentation Pages

To add a new documentation page:

1. Create a new `.md` file in the `docs/` directory or a subdirectory
2. Add YAML front matter at the top:
   ```yaml
   ---
   layout: default
   title: Your Page Title
   nav_order: 5
   ---
   ```
3. Write your content in Markdown below the front matter
4. The page will automatically appear in the navigation

### Front Matter Options

- `layout`: Page layout (usually `default` or `home`)
- `title`: Page title shown in navigation and page header
- `nav_order`: Number to control navigation order (lower = earlier)
- `parent`: For nested pages, specify the parent page title

## Common Tasks for Agents

### Adding a New Documentation Page

1. Create a new `.md` file in `docs/` directory
2. Add appropriate front matter with `layout`, `title`, and `nav_order`
3. Write content in Markdown format
4. Test locally if possible with `bundle exec jekyll serve`

### Modifying Site Configuration

1. Edit `_config.yml` for site-wide settings
2. Changes require a site rebuild to take effect
3. GitHub Actions will automatically rebuild on push to main

### Updating Theme or Dependencies

1. Edit `Gemfile` to change gem versions
2. Run `bundle update` to update `Gemfile.lock`
3. Test the changes locally before committing

### Adding Custom Styles

1. Add new `.scss` files to the `_sass/` directory
2. Import them in the main stylesheet if needed
3. Follow the existing naming conventions

### Adding Images or Assets

1. Place images in `assets/images/`
2. Reference them in Markdown: `![Alt text](/assets/images/filename.png)`
3. Use absolute paths starting with `/` for consistency

## Troubleshooting

### Common Issues

1. **Site not building**: Check `_config.yml` for syntax errors
2. **Navigation not appearing**: Ensure front matter has correct `title` and `nav_order`
3. **Theme not loading**: Verify `Gemfile` has correct `just-the-docs` version
4. **Deployment failing**: Check GitHub Actions logs in the Actions tab

### Dependencies

If you encounter dependency issues:
```bash
bundle update
bundle install
```

## Best Practices

1. **Use semantic Markdown**: Use proper heading hierarchy (h1, h2, h3)
2. **Keep navigation organized**: Use `nav_order` to maintain logical structure
3. **Test locally**: Always test changes locally before pushing
4. **Follow existing patterns**: Maintain consistency with existing pages
5. **Use relative links sparingly**: Prefer absolute paths from root
6. **Keep commits focused**: Make small, focused commits with clear messages

## Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Just the Docs Theme Documentation](https://just-the-docs.github.io/just-the-docs/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Markdown Guide](https://www.markdownguide.org/)

## Notes for AI Agents

- This is a static site generator project - no database or backend server
- Content is written in Markdown with YAML front matter
- Changes to `_config.yml` require a full site rebuild
- The `_site/` directory is auto-generated and should not be edited directly
- GitHub Actions handles deployment automatically on push to main
- Ruby/Jekyll environment may not always be available for local testing
- Focus on content and configuration files, not generated assets
