**🔬 Lab: Decomposition Planning**
**Objective: Practice breaking down complex tasks into prompt chains.**

**Scenario:** You need to build an order processing system with:
  •	Shopping cart management
  •	Inventory validation
  •	Payment processing
  •	Order confirmation emails
  •	Order history

**Tasks:**
1.	Plan the decomposition: Write out 5-7 prompts you would use, with: 
    o	Clear objective for each prompt
    o	Expected output from each
    o	What context carries forward to the next
2.	Identify dependencies: Draw a simple diagram showing which prompts depend on outputs from others
3.	Execute the first two prompts: 
    o	Submit your Prompt 1 (data models)
    o	Take the output and use it in Prompt 2 (core service)
    o	Note any adjustments needed in handoff

**Starter structure:**
**Prompt 1: Data Models**
- Objective: Define Cart, CartItem, Order, OrderItem entities
- Output: SQLAlchemy models + Pydantic schemas
- Carries forward: Model definitions

**Prompt 2: Cart Service**
- Objective: Implement add/remove/update cart operations
- Input needed: Models from Prompt 1
- Output: CartService class
- Carries forward: Service interface

**Prompt 3: ...**
