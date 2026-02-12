Your Task - Apply these patterns in sequence:
**Step 1: Chain of Thought Analysis**
Analyze this code step by step:
1. List all the responsibilities this single method has
2. Identify the code smells (name each one)
3. Map which SOLID principles are violated
4. Trace through a call with report_type="sales", format="html" to show complexity

**Step 2: Step-Back for Strategy**
Before refactoring, consider:
1. The patterns that typically solve these problems (Strategy, Factory, Builder)
2. Our constraint: Must maintain backward compatibility with existing callers
3. Our goal: Enable adding new report types and formats without modifying existing code
Recommend a refactoring strategy with phases.

**Step 3: Few-Shot for Implementation**
Here's how we implement the Strategy pattern in our codebase:
Example - Payment Processing:
from abc import ABC, abstractmethod
from typing import Protocol
```
class PaymentProcessor(Protocol):
    def process(self, request: PaymentRequest) -> PaymentResult: ...

class CreditCardProcessor:
    def process(self, request: PaymentRequest) -> PaymentResult:
        ...

class PayPalProcessor:
    def process(self, request: PaymentRequest) -> PaymentResult:
        ...

class PaymentService:
    def __init__(self, processors: dict[PaymentType, PaymentProcessor]):
        self._processors = processors
    
    def process(self, request: PaymentRequest) -> PaymentResult:
        processor = self._processors[request.payment_type]
        return processor.process(request)
```
Now apply this same pattern to the ReportGenerator for report types.

**Step 4: Self-Verification**
Review your refactored code:
1. Verify all original functionality is preserved
2. Show how to add a new report type (prove Open-Closed principle)
3. Show how to add a new format (prove extensibility)
4. Identify any remaining code smells
