**Building a Feature with Prompt Chains**
**Task: Implement a user registration system with email verification.**

**a) Single prompt approach (problematic):**
Build a complete user registration system with email verification, 
password hashing, database models, API endpoints, and email templates.
Note: This produces shallow implementations across all areas, often with inconsistencies.

**b) Decomposed approach:**

**Prompt 1: Design Phase**
Design the data models for a user registration system with email verification.
Requirements:
- User can register with email and password
- Email verification required before login
- Verification tokens expire after 24 hours
- Track failed login attempts for rate limiting

Output:
1. Entity relationship diagram (text-based)
2. SQLAlchemy models with all fields and relationships
3. Pydantic schemas for API requests/responses

Do not implement business logic yet - just the data layer.


**Prompt 2: Core Business Logic** 
Using the models from the previous step implement the UserService class with these methods:
1. register_user(email, password) -> Result[User]
2. verify_email(token) -> Result[bool]
3. resend_verification(email) -> Result[bool]

Requirements:
- Password hashing with bcrypt
- Generate secure random tokens
- Check for existing users
- Handle token expiration

Use our Result pattern for error handling. Do not implement the API layer yet.

**Prompt 3: API Layer**
Using the service from previous step implement create FastAPI endpoints:
1. POST /auth/register
2. POST /auth/verify-email
3. POST /auth/resend-verification

Include:
- Request validation with Pydantic
- Proper HTTP status codes
- Error response formatting
- OpenAPI documentation strings

Do not implement email sending yet.

**Prompt 4: Email Integration**
Using the endpoints and service from previous steps:
Implement the email notification layer:
1. EmailService class with send_verification_email method
2. Email template for verification (HTML and plain text)
3. Integration with the registration flow
4. Retry logic for failed sends

Use our async patterns with aiosmtplib (async SMTP client for use with asyncio).

**Prompt 5: Testing**
Using the complete implementation from above:
Generate comprehensive tests:
1. Unit tests for UserService (mock database and email)
2. Integration tests for API endpoints
3. Edge cases: duplicate email, expired token, invalid token
Use pytest with fixtures. Include both happy path and error scenarios.
