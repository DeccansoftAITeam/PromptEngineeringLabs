Task: Create method to update customer address
Example 1:
# Input: Create a method to get user by ID
# Output:
async def get_user_by_id(self, user_id: int) -> Result[UserDTO]:
    user = await self.repository.find_by_id(user_id)
    if user is None:
        return Result.not_found(f"User {user_id} not found")
    
    return Result.success(UserDTO.from_entity(user))
Example 2:
# Input: Create a method to delete a product
# Output:
async def delete_product(self, product_id: int) -> Result[bool]:
    product = await self.repository.find_by_id(product_id)
    if product is None:
        return Result.not_found(f"Product {product_id} not found")
    
    await self.repository.delete(product)
    return Result.success(True)
