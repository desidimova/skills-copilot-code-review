# GitHub Copilot Instructions

## Project Overview
This is a web application for Mergington High School's extracurricular activities management system.

## Code Style Guidelines
- Use consistent indentation (2 spaces for HTML/CSS/JS, 4 spaces for Python)
- Follow semantic HTML practices
- Use descriptive variable and function names
- Add comments for complex logic

## Technology Stack
- **Frontend**: HTML, CSS, JavaScript (vanilla)
- **Backend**: Python with FastAPI
- **Database**: SQLite

## Key Conventions
- API routes are organized in `src/backend/routers/`
- Static files (HTML, CSS, JS) are in `src/static/`
- Database operations are handled in `src/backend/database.py`

## Testing
- Ensure all changes maintain existing functionality
- Test authentication flows when modifying auth-related code
- Verify responsive design for UI changes

## Security

- Validate input sanitization practices.
- Search for risks that might expose user data.
- Prefer loading configuration and content from the database instead of hard coded content. If absolutely necessary, load it from environment variables or a non-committed config file.

## Code Quality

- Use consistent naming conventions.
- Try to reduce code duplication.
- Prefer maintainability and readability over optimization.
- If a method is used a lot, try to optimize it for performance.
- Prefer explicit error handling over silent failures.
