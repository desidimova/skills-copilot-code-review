# Frontend Development Instructions

## HTML Guidelines
- Use semantic HTML5 elements (`<header>`, `<main>`, `<footer>`, `<section>`, `<article>`, etc.)
- Include proper accessibility attributes (ARIA labels, roles, alt text)
- Maintain consistent indentation (2 spaces)
- Ensure all forms have proper labels and validation

## CSS Guidelines
- Use meaningful class names that describe purpose, not appearance
- Follow BEM naming convention where appropriate
- Organize CSS properties logically (positioning, display, box model, typography, visual)
- Use CSS variables for colors, spacing, and other repeated values
- Ensure responsive design using media queries
- Mobile-first approach when adding new styles

## JavaScript Guidelines
- Use vanilla JavaScript (no frameworks in this project)
- Use `const` and `let`, avoid `var`
- Use arrow functions for callbacks
- Handle errors gracefully with try-catch blocks
- Use async/await for asynchronous operations
- Add event listeners using `addEventListener`
- Clean up event listeners when removing elements
- Use meaningful variable and function names

## API Integration
- All API calls should use `fetch()` with proper error handling
- Base API URL: `/api`
- Authentication token stored in `localStorage` as `auth_token`
- Include authentication header: `Authorization: Bearer ${token}`
- Handle common HTTP status codes (200, 401, 403, 404, 500)

## File Organization
- HTML files: `src/static/`
- CSS files: `src/static/`
- JavaScript files: `src/static/`
- Keep related functionality together in the same JS file

## Common Patterns
### Modal Management
```javascript
// Show modal
modal.classList.remove('hidden');

// Hide modal
modal.classList.add('hidden');
```

### API Call Pattern
```javascript
async function fetchData() {
  try {
    const response = await fetch('/api/endpoint');
    if (!response.ok) throw new Error('Request failed');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
    showMessage('Error loading data', 'error');
  }
}
```

## Accessibility
- Ensure keyboard navigation works for all interactive elements
- Use proper ARIA attributes for dynamic content
- Maintain sufficient color contrast
- Provide text alternatives for icons
- Test with screen readers when possible

## Browser Compatibility
- Target modern browsers (Chrome, Firefox, Safari, Edge)
- Avoid experimental features without fallbacks
- Test responsive design on multiple screen sizes

---
applyTo: "*.html,*.css,*.js"
---

## Frontend Guidelines

- Use accessibility attributes (alt text, aria labels) and color schemes.
- Use responsive design for compatibility with mobile devices.
- Validate HTML structure and semantic elements