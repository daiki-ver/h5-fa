# AGENTS.md

## Project Overview

This is a static HTML project for the **乐道L80 (LeDao L80)** car event static showcase. The project consists of simple HTML/CSS/JavaScript pages with no build system, testing framework, or linting tools.

## Project Structure

```
H5-FA/
├── index.html          # Main landing page
├── page2.html          # Campground guide/map page
├── images/             # Image assets (P1-P4 images, logos, maps)
├── targetStayleImg/    # Target style images
└── debug/              # Debug screenshots
```

## Build/Lint/Test Commands

### No Build System
This is a **static HTML project** with no build process required. Simply open `index.html` in a browser to view.

### Development
- No dev server configured
- No hot reload available
- Manual browser refresh required

### No Testing
- No test framework present
- No automated tests exist

### No Linting
- No ESLint/Prettier configured
- No code quality checks in place

## Code Style Guidelines

### General
- This is a **vanilla HTML/CSS/JavaScript project**
- No frameworks (React, Vue, Angular) or build tools (Webpack, Vite) used
- All code is inline within HTML files

### HTML
- Use semantic HTML5 elements (`<head>`, `<body>`, `<section>`, `<button>`, etc.)
- Always specify `lang` attribute on `<html>` (e.g., `lang="zh-CN"`)
- Use `charset="UTF-8"` in meta tags
- Include `viewport` meta tag for mobile: `width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no`
- Self-close void elements (e.g., `<img />`, `<br />`)

### CSS
- Place CSS in `<style>` tags within `<head>`
- Use `*` reset with `box-sizing: border-box`
- Use flexbox for layout (see existing patterns)
- Use CSS custom properties for colors if many are used
- Prefer `rem`/`em` for font sizes, `px` for precise spacing
- Mobile-first approach with `@media` queries
- Use `scrollbar-width: none` and `-webkit-scrollbar { display: none; }` to hide scrollbars

### JavaScript
- Place scripts at end of `<body>` or use `defer` attribute
- Use `const` and `let` - avoid `var`
- Use strict equality (`===` and `!==`)
- Use semantic naming for functions (`onCarClick` not `handleCar`)
- Use event delegation where appropriate
- Use `{ passive: true }` for touch events to improve scroll performance
- Avoid inline event handlers (`onclick`) - use `addEventListener` instead
- Use `dataset` API for data attributes (`element.dataset.id` not `element.getAttribute('data-id')`)

### Naming Conventions
- HTML/CSS: kebab-case (`.btn-enter`, `.car-icon`)
- JavaScript: camelCase (`setInitialScroll`, `mapWrapper`)
- Data attributes: kebab-case in HTML (`data-id`, `data-type`), camelCase in JS (`element.dataset.id`)

### Responsive Design
- Design for mobile-first (375px baseline)
- Use percentage-based widths and `vh`/`vw` units
- Test on multiple viewport sizes
- Handle both mouse and touch interactions

### Performance Considerations
- Use `passive: true` for touch scroll listeners
- Lazy load images when possible
- Minimize DOM operations
- Use CSS transforms for animations (GPU acceleration)

### Browser Compatibility
- Target modern browsers (Chrome, Safari, Firefox, Edge)
- Use `-webkit-` prefixes for Safari compatibility
- Consider mobile Safari and Chrome on iOS/Android

## File Organization

- Keep all page assets (HTML, CSS, JS) self-contained when possible
- Images stored in `/images` directory
- Debug artifacts in `/debug` directory
- No shared component library exists

## Common Patterns in This Project

### Page Structure
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Page Title</title>
    <style>/* CSS here */</style>
</head>
<body>
    <!-- Content -->
    <script>/* JS here */</script>
</body>
</html>
```

### Car Icon Element Pattern
```html
<div class="car-icon" data-type="red" data-id="10" style="left: 58%; top: 22%;" onclick="onCarClick(this)">
    <div class="dot">10</div>
    <svg viewBox="0 0 32 32" xmlns="http://www.w3.org/2000/svg"><!-- SVG path --></svg>
    <span class="car-label"></span>
</div>
```

### Touch/Drag Handler Pattern
```javascript
let isDragging = false;
let startX = 0;
let scrollLeft = 0;

element.addEventListener('mousedown', function(e) {
    isDragging = true;
    startX = e.pageX - element.offsetLeft;
    scrollLeft = element.scrollLeft;
});

element.addEventListener('touchstart', function(e) {
    startX = e.touches[0].pageX - element.offsetLeft;
    scrollLeft = element.scrollLeft;
}, { passive: true });
```

## Notes for Agents

- This is a simple static site - no npm, git workflows, or CI/CD
- Direct file edits to `.html` files are the primary workflow
- No type checking or linting enforcement exists
- Manually verify changes in browser after editing
- No backend/API - all data is hardcoded in HTML
