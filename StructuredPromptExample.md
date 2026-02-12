**Role:**
You are a Senior Python Software Engineer with experience in writing production-ready code 

**Task:**
Design and implement a function that validates whether a given string is a valid email address.

**Audience:**
The function is intended for junior developers who will read and reuse this code in a real-world backend application.

**Context / Input:** 
Email validation is required for a user registration system. The function will receive a single string input representing an email address.

**Constraints:**
•	Language: Python
•	Use regex-based validation
•	Function must:
  o	Return True for valid email addresses
  o	Return False for invalid ones
•	Avoid:
  o	Overly complex regex
  o	External libraries
•	Include:
  o	Clear function name
  o	Inline comments
•	Keep the solution simple, readable, and production-appropriate

**Output Format:**
Provide:
1.	The Python function
2.	A brief explanation (2–3 lines)
3.	Example usage with at least 3 test cases

**Examples:**
Valid examples:
  1.	user@example.com
  2.	john.doe123@gmail.com
Invalid examples:
  •	user@com
  •	@gmail.com
  •	usergmail.com
