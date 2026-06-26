# OOAD-Patterns-and-Principles
Project Overview
This project is an Object-Oriented Analysis and Design capstone project that simulates a car dealership system using multiple design patterns in Java.
The dealership simulation is built on top of a previous Command Pattern project and extends the system by adding a clock-driven staff workflow. The simulation runs for 10 days, from 8 AM to 7 PM each day. During each hour, customers arrive with random requests such as ordering, servicing, or buying a car.

The project demonstrates the use of the following design patterns:
Command Pattern
Factory Pattern
Singleton Pattern
State Pattern
Observer Pattern
Features
Simulates a car dealership for 10 business days
Uses a clock system to control staff availability
Tracks staff state changes throughout the day
Randomly generates customer requests
Assigns customer requests to available staff members
Calculates staff bonuses based on completed actions
Prints detailed simulation activity to the console
Provides a final summary report for each staff member

Design Patterns Used
Command Pattern
The Command Pattern is used to represent customer requests as command objects.

Examples of commands include:
orderCar
serviceCar
buyCar

Each command is executed by a staff member and applied to a selected car object.
Factory Pattern
The Factory Pattern is used to create different types of cars.
The simulation uses two factories:
USFactory
JapanFactory

These factories create different car objects used in customer requests.
Singleton Pattern
Two classes are implemented as Singletons:
Clock
The Clock class uses an eager Singleton implementation. The clock instance is created when the program starts.
The clock controls the simulation time and notifies staff members when the time changes.

Invoker
The Invoker class uses a lazy Singleton implementation. The invoker instance is created only when it is first requested.
The invoker receives command requests and assigns them to available staff members.

State Pattern
The State Pattern is used to manage staff availability during the day.
Each staff member can be in one of the following states:
NotIn
Arriving
Available
Lunch
Staff members change states based on the current time and their assigned schedule.

Observer Pattern
The Observer Pattern is used between the Clock and the Staff objects.
The Clock acts as the Subject.
The Staff objects act as Observers.
When the clock time changes, it notifies all staff members. Each staff member then updates their state if needed.
Staff Schedule
Staff	Arrival Time	Lunch Time	Leave Time
Ann	8	12	4
Bob	9	1	5
Cal	10	2	6
Deb	11	3	7
Staff States by Time
Time	Ann	Bob	Cal	Deb
Initialized	NotIn	NotIn	NotIn	NotIn
8	Arriving	NotIn	NotIn	NotIn
9	Available	Arriving	NotIn	NotIn
10	Available	Available	Arriving	NotIn
11	Available	Available	Available	Arriving
12	Lunch	Available	Available	Available
1	Available	Lunch	Available	Available
2	Available	Available	Lunch	Available
3	Available	Available	Available	Lunch
4	NotIn	Available	Available	Available
5	NotIn	NotIn	Available	Available
6	NotIn	NotIn	NotIn	Available
7	NotIn	NotIn	NotIn	NotIn

Simulation Flow
The simulation follows these steps:
Create a Simulation object.
Call the run() method.
Initialize the car factories.
Create staff members.
Register staff members as observers of the clock.
Run the dealership simulation for 10 days.
Increment the clock each hour from 8 AM to 7 PM.
Notify staff members when the clock changes.
Generate a random customer request each hour from 8 AM to 6 PM.
Select a random car from one of the factories.
Use the invoker to assign the request to an available staff member.
Execute the command.
Track each staff member’s completed orders, services, sales, and bonus.
Print a final summary report.
Example Console Output
Day 1
Ann moved to Arriving at 8
Time now: 8 AM
Ann is buying USSedan 1 for $260

Ann moved to Available at 9
Bob moved to Arriving at 9
Time now: 9 AM
Sorry, Cal is Not In
Sorry, Deb is Not In
Ann is buying JapanConvertible 2 for $400

Bob moved to Available at 10
Cal moved to Arriving at 10
Time now: 10 AM
Cal is servicing JapanConvertible 3 for $200
Example Final Results
Results:

Ann:
 Orders: 5
 Services: 12
 Sales: 12
 Bonus: $8450

Bob:
 Orders: 5
 Services: 5
 Sales: 8
 Bonus: $5860

Cal:
 Orders: 11
 Services: 5
 Sales: 8
 Bonus: $9430

Deb:
 Orders: 10
 Services: 8
 Sales: 11
 Bonus: $10830


Requirements
Java
JUnit for testing
Coursera coding environment or any Java IDE
Testing
The autograder should be able to instantiate a Simulation object and call the run() method.
Example:
Simulation simulation = new Simulation();
simulation.run();
The program should print the simulation activity and final results to the console.
UML Diagram
The project includes a UML class diagram showing how the previous Command Pattern application was extended to include:
Singleton Pattern
State Pattern
Observer Pattern
The UML diagram also shows the relationship between the clock, staff, states, commands, factories, and simulation classes.
