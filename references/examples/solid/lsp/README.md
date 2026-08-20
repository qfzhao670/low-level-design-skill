L - Liskov Substitution Principle (LSP)

Definition: It states that objects of a parent class should be replaceable with objects of a child class without breaking the program.

Simple terms.
- If Child class is-a Parent class, then Child should work exactly like Parent
- You should be able to use Child class wherever Parent class is expected
- Child class should not break the behavior that Parent class promises

No class should be forced to implement methods it doesn't use.
Split large interfaces into smaller, more specific ones.