# Backend Development Instructions

## Python Guidelines
- Use consistent indentation (4 spaces)
- Follow PEP 8 style guide
- Use type hints for function parameters and return values
- Write descriptive docstrings for classes and functions
- Use meaningful variable and function names in snake_case
- Keep functions focused on a single responsibility

## FastAPI Guidelines
- Organize routes in `src/backend/routers/`
- Use proper HTTP methods (GET, POST, PUT, DELETE)
- Return appropriate HTTP status codes
- Use Pydantic models for request/response validation
- Document endpoints with descriptions and response models
- Handle exceptions with HTTPException

## Database Guidelines
- All database operations in `src/backend/database.py`
- Use parameterized queries to prevent SQL injection
- Use context managers for database connections
- Handle database errors gracefully
- Close connections properly
- Use transactions for multi-step operations

## Security Guidelines
- Never commit credentials or secrets
- Use environment variables for sensitive configuration
- Validate and sanitize all user inputs
- Use password hashing (never store plain text passwords)
- Implement proper authentication and authorization
- Use CORS middleware appropriately
- Validate JWT tokens properly

## API Response Format
```python
# Success response
{
  "message": "Operation successful",
  "data": {...}
}

# Error response
{
  "detail": "Error message"
}
```

## Authentication Pattern
```python
from fastapi import Depends, HTTPException
from fastapi.security import HTTPBearer, HTTPAuthorizationCredentials

security = HTTPBearer()

async def verify_token(credentials: HTTPAuthorizationCredentials = Depends(security)):
    token = credentials.credentials
    # Verify token logic
    if not valid:
        raise HTTPException(status_code=401, detail="Invalid token")
    return user_data
```

## Error Handling
- Use try-except blocks for database operations
- Return meaningful error messages
- Log errors for debugging
- Don't expose sensitive information in error messages

## Testing
- Test all endpoints manually or with automated tests
- Verify authentication flows
- Test edge cases and error conditions
- Ensure proper validation of inputs

## File Organization
- Main app: `src/app.py`
- Database logic: `src/backend/database.py`
- Route handlers: `src/backend/routers/`
- Keep routers focused on specific functionality (auth, activities, etc.)

## Common Patterns
### Router Definition
```python
from fastapi import APIRouter, HTTPException

router = APIRouter(prefix="/api/endpoint", tags=["endpoint"])

@router.get("/")
async def get_items():
    try:
        # Logic here
        return {"data": items}
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))
```

### Database Query
```python
import sqlite3

def get_data():
    try:
        conn = sqlite3.connect('database.db')
        cursor = conn.cursor()
        cursor.execute("SELECT * FROM table WHERE id = ?", (id,))
        result = cursor.fetchall()
        conn.close()
        return result
    except sqlite3.Error as e:
        print(f"Database error: {e}")
        return None
```

## Dependencies
- Keep `requirements.txt` updated
- Pin major versions for stability
- Document any special installation requirements

---
applyTo: "backend/**/*,*.py"
---

## Backend Guidelines

- All API endpoints must be defined in the `routers` folder.
- Load example database content from the `database.py` file.
- Error handling is only logged on the server. Do not propagate to the frontend.
- Ensure all APIs are explained in the documentation.
- Verify changes in the backend are reflected in the frontend (`src/static/**`). If possible breaking changes are found, mention them to the developer.