**🔬 Lab: Debugging with CoT and Verification**
Scenario: A function that "mostly works" but has subtle bugs.
**The Code:**
```
from typing import Generic, TypeVar
T = TypeVar('T')
class PaginationHelper(Generic[T]):
    def __init__(self, collection: list[T], items_per_page: int):
        self._collection = collection
        self._items_per_page = items_per_page
    @property
    def item_count(self) -> int:
        return len(self._collection)
    @property
    def page_count(self) -> int:
        return len(self._collection) // self._items_per_page
    def page_item_count(self, page_index: int) -> int:
        if page_index < 0 or page_index > self.page_count:
            return -1
        if page_index == self.page_count - 1:
            return len(self._collection) % self._items_per_page
        return self._items_per_page
    def page_index(self, item_index: int) -> int:
        if item_index < 0 or item_index > len(self._collection) - 1:
            return -1
        return item_index // self._items_per_page
```
