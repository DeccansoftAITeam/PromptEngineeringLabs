**Your Task:** Use Chain of Thought to debug this pagination helper.
**Test scenario:** Collection of 11 items, 5 items per page.
Trace through each property and method:
1. page_count property
   - Expected: 3 pages (items 0-4, 5-9, 10)
   - Actual calculation: 11 // 5 = ?
   - Is this correct?
2. page_item_count(0) - first page
   - Expected: 5
   - Trace through the conditions...
3. page_item_count(2) - last page
   - Expected: 1 (only item index 10)
   - Trace through the conditions...
4. page_item_count(3) - invalid page
   - Expected: -1
   - Trace through...
5. page_index(10) - last item
   - Expected: 2 (third page)
   - Trace through...

**For each bug found, explain the root cause and provide the fix.
Then verify your fixes with the same test cases.**
