**Example 1: Basic Task Delegation**
1.	Goto GitHub.com and Select your Repository
2.	Create a GitHub Issue
a.	Provide the Title: Provide documentation for the python files.
b.	Description: Use JSDoc standards and provides comprehensive information about each component's purpose, parameters, and behavior, making the codebase more maintainable and easier for developers to understand.
3.	Assign the Issue to GitCopilot
a.	Click on "Assignees" → Select "Copilot" 
b.	- Or comment: `@copilot please implement this`
4.	What happens
a.	Agent creates a PR immediately (with empty initial commit) 
b.	Works in isolated GitHub Actions environment 
c.	Pushes incremental commits as it develops 
d.	Requests your review when complete 4. 
5.	Review the PR:
a.	 Check the documentation generated
b.	Comment if changes needed: “@copilot please add information about parameters types”
6.	Review and Complete the Pull Request.

**Example 2: Delegating from VS Code Chat:**
1.	In VS Code Chat: 
You: I need to refactor our database queries to use connection pooling. Currently we're opening a new connection for each query which is inefficient. Create a connection pool and update all queries to use it.
2.	Click button before the  key in Chat Window  Select Continue in Cloud (Delegate to coding agent)        
3.	What happens:
a.	Entire chat context transfers to Coding Agent
b.	PR created with detailed description
c.	Agent works autonomously in background
d.	You continue working on other tasks
4.	Comple the Pull Request after review.

**Example 3: Multi-Issue Assignment**
Scenario: End of sprint cleanup - assign multiple small tasks
1.	Issues to create and assign to Copilot:
      1: Add JSDoc comments to all public methods in src/utils/ 
      2: Update dependencies with minor version updates 
      3: Fix all ESLint warnings in src/components/ 
      4: Add missing unit tests for DateFormatter class 
      5: Replace console.log with proper logging using winston
2.	Assign all 5 to Copilot at once
    •	Agent works on them in parallel
    •	Creates separate PR for each
    •	You review in order of completion
