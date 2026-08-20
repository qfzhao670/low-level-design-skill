Problem Statement
Imagine you're building an app like Flipkart or Amazon.
Customers can get different types of discounts:
- Diwali Sale - 20% off on everything
- Student Discount - 15% off with college ID
- First Order - $100 flat discount

Without Strategy Pattern
Every time a new discount type comes, you have to modify this function.
Too many if-else statements make code messy.
Hard to test each discount type separately.
Violates Open/Closed Principle (we learned in SOLID!)