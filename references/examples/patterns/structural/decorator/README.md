Decorator Pattern
You need to add new features or behaviors to an object while your program is running, but creating subclasses for every possible combination would create way too many classes or simply isn't practical.

The Problem: Coffee Shop Ordering System
Imagine you're building a coffee shop ordering system. You start with a basic Coffee, but customers want to customize it with different add-ons like Milk, Sugar, Whipped Cream, and Vanilla Syrup - without changing the basic Coffee class or creating tons of subclasses for every combination.
Without Decorator Pattern, you'd need:
- Coffee
- CoffeeWithMilk
- CoffeeWithSugar
- CoffeeWithWhippedCream
- CoffeeWithMilkAndSugar
- CoffeeWithMilkAndWhippedCream
- CoffeeWithMilkSugarAndWhippedCream