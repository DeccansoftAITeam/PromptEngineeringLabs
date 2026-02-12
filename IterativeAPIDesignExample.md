Step1: Initial Generation Prompt:
Design a REST API endpoint for bulk user import from CSV.

Step2: Critique Prompt:
Analyze this bulk import endpoint for production readiness:
Consider:
1. What happens with 100,000 rows?
2. What if row 50,000 fails validation?
3. How does the client know which rows failed?
4. What about duplicate detection?
5. Memory usage patterns?
6. Timeout handling?
Provide specific issues and severity ratings.

Step3: Improvement Prompt:
Refactor the bulk import to address these issues:
Fix all Issues mentioned
Requirements for new design:
- Stream processing (don't load entire file)
- Batch commits (every 100 rows)
- Detailed error reporting per row
- Return job ID for async processing if > 1000 rows
- Duplicate detection by email field
- Progress tracking capability
