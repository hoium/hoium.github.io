# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal portfolio website (hoium.me) built with Jekyll and based on the [front-cover](https://github.com/dashingcode/front-cover) theme. It's a single-page static site hosted on GitHub Pages that displays personal information and social media links.

## Development Commands

```sh
make serve           # Runs jekyll serve --incremental
jekyll serve --incremental  # Direct command (faster rebuilds)
```

## Architecture

### Site Structure

- **[index.html](index.html)**: Main page with full HTML template using Jekyll Liquid templating
- **[_config.yml](_config.yml)**: All site content and configuration variables
- **[css/front.css](css/front.css)**: Styling with responsive design (mobile breakpoint at 450px, GitHub corner hides at 500px)
- **[404.html](404.html)**: Custom 404 error page
- **imgs/**: Static assets (background.jpeg, favicon.ico)

### Configuration Variables

All content is managed through [_config.yml](_config.yml):

- **Site info**: `title`, `name`, `description`, `url`, `og_description`
- **Social links**: `github_username`, `facebook_username`, `linkedin_username`, `instagram_username`
- **Contact**: `email_encoded` (base64-encoded for spam protection)
- **Custom links**: `jeep`, `git_repo`
- **Analytics**: `google_analytics_ga4`
- **Images**: `avatar_img_path`, `front_img_path`, `favicon_img_path`

### Email Obfuscation

Email is stored as base64 in `email_encoded` and decoded via JavaScript at runtime to prevent scraping. To update, encode the new email: `echo -n "email@example.com" | base64`

### Content Updates

Edit [_config.yml](_config.yml) rather than [index.html](index.html). The HTML template uses Jekyll Liquid syntax: `{{ site.name }}`, `{{ site.description }}`, etc.

## Ruby Version

Ruby 3.4.8 (pinned in [.ruby-version](.ruby-version)).

## Commit & Pull Request Guidelines

### Commit Message Format

Use clear, concise commit messages that describe the change:

**Format:**

```text
<type>: <description>

[optional body]
```

**Types:**

- `feat`: New feature (e.g., "feat: Add email contact link with obfuscation")
- `fix`: Bug fix (e.g., "fix: Correct mobile responsive layout")
- `style`: CSS/styling changes (e.g., "style: Update social icon hover effects")
- `perf`: Performance improvements (e.g., "perf: Optimize background image size")
- `docs`: Documentation only (e.g., "docs: Update README with build instructions")
- `refactor`: Code restructuring without functional changes
- `chore`: Maintenance tasks (e.g., "chore: Update dependencies")

**Examples:**

```text
feat: Add Open Graph meta tags for social sharing

Implements OG tags for Facebook, LinkedIn, and Twitter Cards
to improve link preview appearance when site is shared.

perf: Reduce background image from 3.3MB to 903KB

Compressed using sips with 70% quality and max 1920px width.
```

### Commit Best Practices

- **Atomic commits**: One logical change per commit
- **Test before committing**: Run `make serve` to verify changes locally
- **No secrets**: Never commit API keys, tokens, or sensitive data
- **Keep backups**: Original files are backed up before optimization (e.g., `background.jpeg.backup`)

### Pull Request Guidelines

**When creating PRs:**

1. **Title**: Use same format as commit messages

   ```text
   feat: Add resume download section
   ```

2. **Description template**:

   ```markdown
   ## Summary
   Brief description of changes

   ## Changes
   - Bullet list of specific changes
   - Another change

   ## Testing
   - [ ] Tested locally with `make serve`
   - [ ] Verified on mobile (< 500px)
   - [ ] Checked social media preview (if applicable)
   - [ ] Verified all links work

   ## Screenshots (if UI changes)
   [Add screenshots here]
   ```

3. **Before submitting**:
   - Ensure Jekyll builds without errors
   - Test responsive design on mobile viewport
   - Verify external links have `rel="noopener noreferrer"`
   - Check that no sensitive info is exposed

### Branch Naming

- `feature/<description>` - New features (e.g., `feature/resume-section`)
- `fix/<description>` - Bug fixes (e.g., `fix/mobile-layout`)
- `perf/<description>` - Performance improvements (e.g., `perf/image-optimization`)
- `docs/<description>` - Documentation updates

### Deployment Notes

- **Main branch** deploys automatically to GitHub Pages
- Changes typically appear within 1-2 minutes
- Jekyll builds on push - check Actions tab for build status
- Test thoroughly before merging to main
