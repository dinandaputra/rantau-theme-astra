# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a WordPress child theme called "Rantau" that extends the Astra parent theme. It's a minimal child theme setup designed for customization while inheriting all functionality from the Astra parent theme.

## Project Structure

- `functions.php` - Theme functions file that enqueues child theme styles
- `style.css` - Child theme stylesheet with theme metadata header
- `screenshot.jpg` - Theme preview image

## Key Technical Details

### WordPress Child Theme Architecture
- **Parent Theme**: Astra (located at `../astra/`)
- **Template Hierarchy**: This child theme inherits all templates from Astra unless overridden
- **Style Loading**: Child theme styles are enqueued after parent theme styles with priority 15

### Current Implementation
- Theme version: 1.0.0
- Text domain: `rantau`
- Constant defined: `CHILD_THEME_RANTAU_VERSION`
- Style enqueue hook: `wp_enqueue_scripts` with priority 15

## Development Guidelines

### IMPORTANT: Documentation Research Before Coding
**ALWAYS use context7 MCP to retrieve up-to-date documentation before implementing any code that uses external libraries, frameworks, or WordPress APIs:**

1. **Before writing any code**, use `mcp__context7__resolve-library-id` to find the relevant library documentation
2. Then use `mcp__context7__get-library-docs` to retrieve specific documentation for the implementation
3. This ensures code is written with the latest best practices and API usage

Examples of when to use context7:
- Before using WordPress hooks, filters, or functions
- When implementing Astra theme customizations
- When working with any PHP libraries or frameworks
- Before using JavaScript libraries or CSS frameworks

### Frontend Development and Testing
**ALWAYS use Playwright MCP when making frontend changes:**

1. **After implementing frontend changes**, use Playwright MCP tools to:
   - Navigate to the site using `mcp__playwright__browser_navigate`
   - Take screenshots with `mcp__playwright__browser_take_screenshot` to verify visual changes
   - Use `mcp__playwright__browser_snapshot` to capture the page structure
   - Test interactive elements with `mcp__playwright__browser_click` and form interactions

2. **Testing workflow for frontend changes:**
   - Make CSS/template changes
   - Navigate to the affected page
   - Take before/after screenshots
   - Verify responsive design at different viewport sizes using `mcp__playwright__browser_resize`
   - Test any interactive elements or JavaScript functionality

3. **Use cases for Playwright MCP:**
   - Verifying CSS changes in `style.css`
   - Testing template overrides from parent theme
   - Checking responsive design breakpoints
   - Validating JavaScript interactions
   - Ensuring cross-browser compatibility

### Adding Custom Functionality
- Add PHP customizations to `functions.php`
- Add CSS customizations to `style.css`
- To override parent theme templates, copy them from `../astra/` maintaining the same directory structure

### WordPress Coding Standards
- Follow WordPress PHP coding standards
- Use appropriate WordPress hooks and filters
- Escape output with WordPress escaping functions (`esc_html()`, `esc_attr()`, etc.)
- Sanitize input data appropriately

### File Modifications
- Always check if functionality can be achieved through hooks/filters before overriding templates
- When overriding parent theme files, maintain the same file structure as the parent theme
- CSS should be added to `style.css` rather than creating new stylesheet files unless necessary