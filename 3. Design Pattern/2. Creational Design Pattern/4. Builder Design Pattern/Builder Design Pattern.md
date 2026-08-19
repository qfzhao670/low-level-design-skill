Builder Design Pattern
When creating an object that needs many different settings - especially when most of them are optional - the constructor becomes messy and confusing.
This creates several problems:
1. Extremely long parameter lists in the constructor
2. Hard to remember which parameters are required and which are optional
3. No flexibility to set only specific values you need

Builder Design Pattern
Problem: When a class constructor needs too many parameters (especially optional ones), the Builder Pattern lets you construct complex objects step-by-step in a clear and readable way.
Solution: Splits the object creation process into separate steps using a
builder
ass. You can set y the properties you need using a fluent
interface
(method chaining)
haking the code clean and easy to understand.