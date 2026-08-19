State Pattern
Imagine you're creating a DirectionService class for a maps application like
Google Maps. This service needs to calculate how long (ETA) it will take to reach your destination and what route (directions) to follow between two locations. The travel time and route change depending on your chosen mode of transport:
- Walking
- Cycling
- Car
- Train

State Pattern: Structure
Context: This is the main class (like DirectionService) that keeps track of which state is currently active.
State: This is the interface that defines what methods all states must have (like calculating ETA or getting directions).
Concrete State. These are the actual state classes (like WalkingMode, CarMode, TrainMode) that implement the State interface. Each one represents a different mode or condition of the Context object.

Examples
Music Player: A music player app that behaves differently depending on its current state (playing, paused, or stopped). The play button does different things in each state.
Order Tracking System: An e-commerce order that moves through different states like Order Placed, Packing, Shipped, Out for Delivery, and Delivered.
Each state has different actions available.
ATM Machine: An ATM that changes behavior based on its state (idle, card inserted, PIN verification, selecting transaction, dispensing cash). Each state allows different operations.
Traffic Light System: A traffic signal that cycles through states (red, yellow, green) where each state determines what vehicles can do and automatically transitions to the next state after a timer.
