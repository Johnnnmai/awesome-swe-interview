# Object-Oriented Design Questions

Object-oriented design (OOD) interviews test your ability to model real-world systems as classes, define relationships, and apply design principles. These questions appear in about 25.0% of SWE interview processes, most commonly at companies like Amazon, Microsoft, and Bloomberg. The format is typically 30-45 minutes.

## The Interview Format

The interviewer gives you a system to model (a parking lot, an elevator, a chess game). You are expected to:
1. Clarify requirements and scope
2. Identify the main entities (classes)
3. Define their attributes and methods
4. Establish relationships (inheritance, composition, association)
5. Apply design patterns where appropriate
6. Handle edge cases and extensions

Unlike system design interviews, OOD focuses on code-level architecture rather than infrastructure. You may be asked to write actual class definitions, method signatures, or pseudocode.

## The Framework

Step 1: Gather requirements (3-5 minutes)
Ask clarifying questions. What features are in scope? What should the system support? What are the constraints? A parking lot system for a shopping mall has different requirements than one for an airport.

Step 2: Identify core classes (5 minutes)
List the nouns in the problem. These are usually your classes. For a parking lot: ParkingLot, ParkingSpot, Vehicle, Ticket, Payment. Group related entities.

Step 3: Define relationships (5-10 minutes)
Determine how classes relate to each other. A ParkingLot has many ParkingSpots (composition). A Vehicle is parked in a ParkingSpot (association). A Car is a type of Vehicle (inheritance). Use "has-a" for composition and "is-a" for inheritance.

Step 4: Design interfaces and methods (10-15 minutes)
Define the key methods for each class. What actions can each entity perform? A ParkingLot can `park(vehicle)`, `unpark(ticket)`, `getAvailableSpots()`. Focus on the public interface first.

Step 5: Apply design patterns (5 minutes)
Identify where common patterns apply. Strategy pattern for different pricing schemes. Observer pattern for notification when spots become available. Factory pattern for creating different vehicle types.

Step 6: Handle extensions (5 minutes)
The interviewer often asks "what if we want to add X?" Your design should be extensible. SOLID principles help here.

## SOLID Principles

These principles come up frequently in OOD discussions. Know them and be ready to explain how your design applies them.

Single Responsibility: each class should have one reason to change. A ParkingSpot class should not handle payment processing.

Open/Closed: classes should be open for extension, closed for modification. Adding a new vehicle type (motorcycle) should not require changing existing vehicle classes.

Liskov Substitution: subclasses should be usable wherever their parent class is expected. If your code works with a Vehicle, it should work with Car, Truck, or Motorcycle without modification.

Interface Segregation: clients should not be forced to depend on interfaces they do not use. A VehicleParking interface and a VehicleCharging interface are better than one MonolithicVehicle interface with both.

Dependency Inversion: depend on abstractions, not concretions. Your ParkingLot should depend on a PaymentProcessor interface, not directly on a StripePaymentProcessor class.

## Common Design Patterns

Factory pattern
Use when: you need to create objects without specifying the exact class. A VehicleFactory creates Car, Truck, or Motorcycle objects based on input parameters. This decouples object creation from usage.

Observer pattern
Use when: multiple objects need to react to state changes. When a ParkingSpot becomes available, the notification system, the display board, and the mobile app all need to update. The spot publishes an event, and subscribers react.

Strategy pattern
Use when: you need interchangeable algorithms. Different pricing strategies (hourly, daily, monthly) for a parking lot. Each strategy implements a common PricingStrategy interface with a `calculateFee(duration)` method.

Singleton pattern
Use when: exactly one instance of a class should exist. A ParkingLotManager that coordinates all operations. Use cautiously; singletons make testing harder.

Builder pattern
Use when: constructing complex objects step by step. Building a Reservation object with many optional parameters (date, time, party size, special requests, dietary restrictions).

## Common Questions

Design a parking lot system

Requirements: multiple floors, different spot sizes (compact, regular, large), different vehicle types, entry/exit tracking, payment processing.

Key classes:
- `ParkingLot`: contains floors, manages entry/exit
- `ParkingFloor`: contains spots, tracks availability per floor
- `ParkingSpot`: abstract class with CompactSpot, RegularSpot, LargeSpot subclasses
- `Vehicle`: abstract class with Car, Truck, Motorcycle subclasses
- `Ticket`: records entry time, vehicle, assigned spot
- `Payment`: handles fee calculation and payment processing

Design decisions: how to find the nearest available spot (strategy pattern for different allocation algorithms). How to handle full lots (observer pattern to notify waiting vehicles). How to calculate fees (strategy pattern for different pricing tiers).

Design an elevator system

Requirements: multiple elevators in a building, up/down requests from each floor, internal floor selection, efficient scheduling.

Key classes:
- `ElevatorSystem`: coordinates all elevators
- `Elevator`: tracks current floor, direction, passenger requests
- `Request`: external (floor + direction) or internal (target floor)
- `Scheduler`: determines which elevator handles each request
- `Door`: manages open/close state with safety checks
- `Display`: shows current floor and direction

Design decisions: scheduling algorithm (SCAN, LOOK, nearest car). How to handle peak hours. Emergency stop and priority override. This question tests your ability to model state machines (elevator states: idle, moving up, moving down, door open).

Design a library management system

Requirements: book catalog, member management, book checkout/return, reservations, fine calculation.

Key classes:
- `Library`: manages the overall system
- `Book`: title, author, ISBN, copies
- `BookItem`: individual physical copy with barcode, status
- `Member`: borrowing history, active loans, fines
- `Loan`: tracks which member has which book item, due date
- `Reservation`: queued request for a book
- `Fine`: calculates overdue fees

Design decisions: how to handle reservations when all copies are checked out (queue with notification). How to manage different member types (student vs faculty with different borrowing limits). Search functionality (by title, author, ISBN, subject).

Design a chess game

Requirements: standard chess rules, two players, move validation, check/checkmate detection.

Key classes:
- `Game`: manages the overall game state, turn order
- `Board`: 8x8 grid of cells
- `Cell`: position on the board, may contain a piece
- `Piece`: abstract class with King, Queen, Rook, Bishop, Knight, Pawn subclasses
- `Player`: name, color, captured pieces
- `Move`: from position, to position, piece, captured piece

Design decisions: move validation (each piece subclass implements its own `canMove(from, to, board)` method). Special moves (castling, en passant, pawn promotion). Check detection (after each move, verify the opponent's king is not in check). Game state (active, check, checkmate, stalemate, draw).

Design a vending machine

Requirements: multiple products, coin/bill acceptance, change dispensing, inventory management.

Key classes:
- `VendingMachine`: state machine managing the transaction flow
- `Product`: name, price, slot position
- `Inventory`: tracks quantity of each product
- `Coin` / `Bill`: denomination, value
- `Transaction`: tracks inserted money, selected product, change

Design decisions: state machine pattern (idle, accepting money, dispensing, returning change). How to handle insufficient funds. How to make change (greedy algorithm with available denominations). What happens when a product is out of stock.

Design an online bookstore

Requirements: book catalog, shopping cart, user accounts, order processing, payment, reviews.

Key classes:
- `Bookstore`: facade for the system
- `Book`: title, author, price, description, category
- `User`: account info, address, payment methods
- `ShoppingCart`: list of items with quantities
- `Order`: user, items, shipping address, payment, status
- `Review`: user, book, rating, text
- `Payment`: interface with CreditCardPayment, PayPalPayment implementations

Design decisions: inventory management (reserve stock when added to cart vs at checkout). Pricing (discounts, coupons as a strategy pattern). Order status tracking (state pattern: placed, confirmed, shipped, delivered).

Design a file system

Requirements: files and directories, create/delete/move/rename, permissions, search.

Key classes:
- `FileSystem`: root directory, path resolution
- `Entry`: abstract class for files and directories
- `File`: extends Entry, contains content, size, type
- `Directory`: extends Entry, contains list of entries (composite pattern)
- `Permission`: read/write/execute for owner/group/other
- `User`: name, groups

Design decisions: composite pattern for the directory tree (directories contain entries, which can be files or directories). Path resolution algorithm. Permission checking at each level. How to handle symbolic links.

Design a restaurant reservation system

Requirements: table management, reservation booking, waitlist, time slot management.

Key classes:
- `Restaurant`: tables, operating hours, reservations
- `Table`: capacity, location, status
- `Reservation`: party size, date/time, duration, contact info, status
- `TimeSlot`: represents an available booking window
- `WaitList`: queue of parties waiting for a table
- `Customer`: name, contact, reservation history

Design decisions: how to match party size to table capacity (allow slightly larger tables, avoid wasting large tables on small parties). Reservation conflicts and double-booking prevention. Cancellation policy and no-show handling. Peak time management.

## How to Prepare

Practice modeling everyday systems. Pick an object around you (a coffee machine, a traffic light, a playlist) and design its class structure. Identify entities, relationships, and methods.

Know the five SOLID principles and be ready to explain them with examples. Interviewers often ask "how does your design follow the Single Responsibility Principle?" or "what if we wanted to add a new payment method?"

Study common design patterns. You do not need to memorize all 23 GoF patterns. Focus on Factory, Observer, Strategy, Singleton, Builder, Composite, and State. Know when to apply each and what problem it solves.

Practice writing class diagrams or pseudocode quickly. You have limited time, so your notation needs to be clear and fast. UML is optional; clear class definitions with attributes and method signatures are sufficient.

## Common Mistakes

Over-engineering. Adding unnecessary abstractions, patterns, or classes. Start simple and add complexity only when the requirements demand it.

Ignoring edge cases. What happens when the parking lot is full? What happens when a chess piece is pinned? Interviewers probe these scenarios.

Forgetting about concurrency. In a real system, multiple users interact simultaneously. Mention thread safety, locks, or concurrent data structures where relevant.

Not applying SOLID principles. If your design violates these principles, the interviewer will notice. A class that handles both data storage and UI rendering is a red flag.

Treating it like a system design question. OOD is about class-level architecture, not infrastructure. You do not need to discuss databases, load balancers, or CDNs unless specifically asked.
