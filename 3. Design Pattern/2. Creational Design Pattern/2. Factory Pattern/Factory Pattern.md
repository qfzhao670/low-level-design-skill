Factory Pattern
Imagine you're building a food ordering app where customers can order different types of meals (Pizza, Burger, Pasta). Initially, you might create separate classes for each food type and create objects like this:
pizza = Pizza ()
burger = Burger ()
pasta = Pasta ()
But as your restaurant grows and you keep adding new menu items (Biryani, Dosa, Momos, Chinese, etc.), directly creating these objects in your code becomes messy and hard to manage, especially wen the creation logic gets more complex.

Real World Use Cases
1. User Interface Libraries: When building apps, the type of button or Ul element created depends on which platform you're running on (Windows, macOS, or Linux).
A factory decides which platform-specific component to create at runtime.
2. Database Connections: When an application needs to connect to different database systems (like MySQL or MongoDB), a factory chooses which database connector to create based on the configuration settings.
3. File Export Tools: When users want to export documents to different formats (PDE. Word, HTML), a factory determines which file generator to create based on the user's selection.