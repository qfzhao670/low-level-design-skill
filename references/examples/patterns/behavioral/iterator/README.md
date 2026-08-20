Problem Statement
Imagine you're working with different data structures like arrays, lists, or trees, and you want to go through each element one by one. If you don't use the Iterator pattern, anyone using your collection must know its internal organization. Each type of collection would need its own unique way to loop through items.

Iterator Pattern
The Challenge
How do you go through items in a collection (list, array, tree, etc.) without needing to know how the collection stores those items internally?
The Solution
Iterator Pattern gives you a standard way to loop through any collection while keeping its internal organization hidden. Every collection provides the same interface for accessing items one by one.
Main Components
- Iterator: Defines the methods to move through items in a collection (like has_next) and next()).
- Collection: Stores the items and creates an iterator that knows how to access them properly.