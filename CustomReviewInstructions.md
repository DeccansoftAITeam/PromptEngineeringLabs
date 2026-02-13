# Custom Review Instructions
## Make reviews project-specific:
Create .vscode/settings.json:
```
{
  "github.copilot.chat.reviewSelection.enabled": true,
  "github.copilot.chat.reviewSelection.instructions": [
    {
      "file": ".github/copilot-review-instructions.md"
    }
  ]
}
```
# Create .github/copilot-review-instructions.md:

## Code Review Guidelines for Projects
## Security Requirements
- All database queries must use parameterized statements
- API keys must be in environment variables
- All user inputs must be validated and sanitized
- Authentication required on all non-public endpoints

## Code Quality Standards
- Functions should not exceed 50 lines
- Maximum cyclomatic complexity: 10
- All public methods must have JSDoc comments
- Consistent error handling with custom error classes

## Testing Requirements
- Every function must have unit tests
- Minimum 80% code coverage
- Integration tests for API endpoints
- E2E tests for critical user flows

## Specific Frameworks
- React: Use functional components with hooks
- Express: Use async/await, not callbacks
- Database: Use TypeORM, migrations required
- Logging: Use Winston, not console.log

## What NOT to flag
- Console.log in test files is acceptable
- Long functions in generated migration files
- TODO comments (we track them in Jira)

