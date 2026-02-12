**Role:** You are a senior Python security architect.
**Task:** Design the authentication flow for user login.
Requirements
1.	LoginCommand
  o	Accepts email and password
  o	Input validation using a Python validation approach (e.g., Pydantic / custom validators)
2.	Token Strategy
  o	JWT access token with 15-minute expiry
  o	Refresh token with 7-day expiry
3.	Account Lockout
  o	Lock account after 5 failed login attempts
  o	Lockout duration: 30 minutes
4.	Audit Logging
  o	Log every authentication attempt (success or failure)
  o	Capture:
      Timestamp
      User identifier (if available)
      Client IP address
5.	Result Pattern
  o	Use a Result[T]-style return object instead of raising exceptions
  o	Explicit success/failure states with error codes/messages

**Context**: You are building a Python-based Web API following Clean Architecture principles, organized into the following layers:
  •	API: HTTP controllers / routers (e.g., FastAPI or Flask blueprints)
  •	Application Use-case handlers (Commands / Queries pattern) / Validation logic & Application-level DTOs)
  •	Domain (Entities, Value Objects, Business rules (no framework dependencies))
  •	Infrastructure (ORM (e.g., SQLAlchemy), 
Users are stored in SQL Server using a Python ORM. Authentication is handled using JWT access tokens and refresh tokens.

**Output Format**
  •	login_command.py
  •	login_command_handler.py
  •	login_command_validator.py
  •	authentication_result.py (record / dataclass)

All public classes and methods should include docstrings.

**Constraints**
  •	No external authentication frameworks (e.g., OAuth providers)
  •	Only standard Python crypto / JWT libraries
  •	Password rules:
      o	Minimum 8 characters
      o	At least one uppercase letter
      o	One lowercase letter
      o	One number
      o	One special character
  •	Token generation must be thread-safe
