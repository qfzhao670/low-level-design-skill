Adapter Pattern
The Adapter Pattern is a design pattern that lets two systems or components that weren't designed to work together communicate with each other by creating a bridge between them.

Problem Statement
Imagine you're building an e-commerce website (like Flipkart or Amazon) that sends email notifications to customers (order confirmations, shipping updates, etc.).
Right now, you're using your own custom email system called EmailNotificationService. Everything works fine!
But now you want to switch to a popular third-party email service like SendGrid (which is faster, more reliable, and handles spam better).
The Problem: Your existing code expects one interface, but SendGrid has a completely different interface. They don't match!
