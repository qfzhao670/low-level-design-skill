Problem Statement
Imagine you have a weather station that measures temperature. There are multiple devices like phones, TVs, and displays that need to show this temperature.

Without Observer Pattern
The weather station would need to know about every single device and manually update each one when the temperature changes.
This creates a big problem:
- Weather station is tightly connected to all devices
- Adding a new device means changing weather station code
- Removing a device means changing weather station code again
- Weather station depends on specific device types

Observer Pattern Benefits
Loose Coupling: The main object (like WeatherStation) doesn't need to know anything about the specific devices. It just sends notifications to whoever is listening, without caring what type of device it is.
Easy to Scale: You can add as many new devices as vou want (phones, TVs, smartwatches, etc.) without changing a single line of code in the WeatherStation.
Just register the new device and it starts receiving updates automatically.
Flexible at Runtime: Devices can join or leave the notification list anytime while the program is running. A device can start listening when it needs updates and stop listening when it doesn't.