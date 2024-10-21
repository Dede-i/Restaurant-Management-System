# Restaurant Management System

The Restaurant Management System is composed of several key components and modules that work together to handle various functionalities, such as managing orders, employees, menu items, and database operations. Below is a detailed breakdown of these components:

## 1. Controller Module

The Controller serves as the system's central coordinator. It processes input from the user interface and directs the flow of information between different modules, such as Order, Database, and Employee.

**Responsibilities**:
- Mediates between the user interface and the business logic.
- Manages the flow of information between different parts of the system.
- Handles order lifecycle events, such as creating, updating, or deleting orders.
- Delegates tasks to the appropriate modules (e.g., saving an order to the database or assigning an employee to an order).

## 2. Order Module

The Order module represents a customer’s order in the system. It stores the details of an order, including the items ordered, the total cost, and the employee responsible for handling the order.

**Responsibilities**:
- Manages the list of ordered items and quantities.
- Calculates the total price of an order.
- Handles the state of the order (e.g., open, closed, or canceled).
- Interacts with other modules such as OrderDetail for detailed item handling.

## 3. Order Detail Module

The OrderDetail module represents the details of each item in an order. It stores information such as the item ordered, the quantity, and calculates the subtotal for that specific item.

**Responsibilities**:
- Stores the quantity and specific menu items for each order.
- Calculates the subtotal for each item in an order.
- Serves as a bridge between the Order and MenuItem classes, holding detailed information about individual items.

## 4. MenuItem Module

The MenuItem module represents the items available in the restaurant, such as food or drinks. It contains information like each item's name, price, and unique identifier.

**Responsibilities**:
- Stores the attributes of individual menu items, such as name, price, and item ID.
- Provides necessary information to calculate the cost of items in an order.
- Works with the OrderDetail class to represent specific items within customer orders.

## 5. Database Module

The Database module is responsible for managing all interactions with the database, including saving, retrieving, and updating data related to orders, employees, and menu items.

**Responsibilities**:
- Manages database connections and executes queries to persist or retrieve data.
- Handles CRUD (Create, Read, Update, Delete) operations for different entities such as orders, menu items, and employees.
- Ensures the integrity and persistence of data across the system.
- Facilitates interaction between the system’s components and the underlying data store.

## 6. Employee and Manager Modules

The Employee and Manager modules represent the staff working in the restaurant. While Employee handles general staff-related operations, the Manager class extends Employee to include additional management responsibilities, such as approving orders or overseeing staff.

### Employee Class Responsibilities:
- Stores basic information about employees, including ID, name, and role.
- Handles tasks assigned to the employee, such as managing orders.

### Manager Class Responsibilities:
- Extends the functionality of Employee by adding manager-specific operations.
- Handles approval of orders, employee management, and other supervisory tasks.
- Has additional privileges compared to regular employees in the system.

## Component Interaction

- The Controller module orchestrates the flow of information between the Order, Database, and Employee modules, ensuring proper execution of business logic.
- Orders interact with the OrderDetail module to handle individual item details, which in turn reference the MenuItem module for price and item data.
- Employee and Manager modules are responsible for order handling and employee management, while the Database module ensures all data is persisted and retrieved as needed.
