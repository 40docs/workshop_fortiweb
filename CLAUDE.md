# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a FortiWeb workshop documentation site built with MkDocs Material. It provides hands-on labs for learning FortiWeb web application firewall configuration and security features including SQL injection protection, bot detection, CSRF protection, user tracking, and machine learning API protection.

## Architecture

- **Documentation Framework**: MkDocs with Material theme
- **Content Structure**: Markdown-based lab documentation in `docs/Hands-on-Labs/`
- **Theme**: Custom 40docs workshop theme (cloned from `40docs/workshop_theme_template`)
- **Deployment**: GitHub Actions workflow for automated GitHub Pages deployment
- **Lab Format**: Progressive hands-on exercises (Labs 1-8) covering FortiWeb configuration

## Key Components

### Documentation Structure
- `docs/index.md`: Landing page with custom CSS styling
- `docs/Hands-on-Labs/`: Contains numbered lab modules (01-08)
- Lab progression: Access → Setup → Bot Protection → ML API → Web Shell → CSRF → User Tracking → SQL Injection
- Each lab includes step-by-step instructions with UI screenshots and CLI alternatives

### Build System
- **Local Development**: Python virtual environment with MkDocs serve
- **Production**: GitHub Actions workflow with theme cloning and artifact deployment
- **Theme Dependency**: Requires cloning `40docs/workshop_theme_template` as `theme/` directory

## Development Commands

### Local Development Setup
```bash
# Create and activate virtual environment
python3 -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Clone required theme for local preview
git clone https://github.com/40docs/workshop_theme_template.git theme

# Start development server
mkdocs serve
```

### Content Management
```bash
# Build site locally
mkdocs build --verbose

# Deploy (automatic on push to main)
git add .
git commit -m "Update workshop content"
git push origin main
```

## Configuration Files

- `mkdocs.yml`: Site configuration, theme settings, markdown extensions, navigation
- `requirements.txt`: Python dependencies for MkDocs and extensions
- `.github/workflows/deploy.yml`: GitHub Actions deployment pipeline
- Site deploys automatically to: `https://40docs.github.io/workshop_fortiweb/`

## Content Guidelines

### Lab Documentation Format
- Use numbered prefixes (01-, 02-, etc.) for proper ordering
- Include both UI and CLI instruction variants using tabbed content
- Store images in `docs/Hands-on-Labs/images/` with descriptive names
- Use MkDocs admonitions for notes, warnings, and tips
- Follow progressive lab structure building on previous configurations

### Markdown Features Available
- Admonitions (note, warning, tip)
- Code syntax highlighting
- Tabbed content sections
- Mermaid diagrams
- Image lightbox (glightbox plugin)
- Search functionality

## Deployment Notes

- GitHub Pages must be enabled with "GitHub Actions" as source
- Site builds on every push to main branch
- Theme is automatically cloned during GitHub Actions build
- Local preview requires manual theme cloning
- Build warnings about missing theme files locally are normal and don't affect deployed site