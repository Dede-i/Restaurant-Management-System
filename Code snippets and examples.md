1 - Controller Module

Example:

public class Controller {
    private Database db;
    private List<Order> orders;
    
    public Controller() {
        db = new Database();
        orders = new ArrayList<>();
    }

    public void addOrder(Order order) {
        orders.add(order);
        db.saveOrder(order);
    }

    public void closeOrder(int orderID) {
        Order order = db.getOrder(orderID);
        order.closeOrder(orderID);
        db.updateOrder(order);
    }
}

Explained : The Controller class manages order operations and maintains data consistency inside the MVC architecture by serving as a mediator between the database and the user interface.

2. Order Module

Example: 

public class Order {
    private int orderID;
    private int staffID;
    private String staffName;
    private ArrayList<OrderDetail> orderDetails;
    private double total;
    
    public Order(int orderID, int staffID, String staffName) {
        this.orderID = orderID;
        this.staffID = staffID;
        this.staffName = staffName;
        this.orderDetails = new ArrayList<>();
        this.total = 0;
    }

    public void addItem(MenuItem item, int quantity) {
        OrderDetail detail = new OrderDetail(item, quantity);
        orderDetails.add(detail);
        total += detail.calculateSubtotal();
    }

    public double calculateTotal() {
        return total;
    }

    public void closeOrder(int orderID) {
        // Logic for closing the order
    }
}

Explained : The Order class is used to handle a customer's order. In order to add products and calculate the total cost.

3. Order Detail Module

Example:

public class OrderDetail {
    private MenuItem item;
    private int quantity;

    public OrderDetail(MenuItem item, int quantity) {
        this.item = item;
        this.quantity = quantity;
    }

    public double calculateSubtotal() {
        return item.getPrice() * quantity;
    }
}

Explained : in OrderDetail, described Each item in an order, together with its price and quantity, retrieves pricing information from the MenuItem class and determines the item's overall cost. Accurate order processing and invoicing depend on this.

4. MenuItem Module

Example:

public class MenuItem {
    private int itemID;
    private String name;
    private double price;

    public MenuItem(int itemID, String name, double price) {
        this.itemID = itemID;
        this.name = name;
        this.price = price;
    }

    public double getPrice() {
        return price;
    }
}

Explained : The MenuItem class provides methods to readily obtain the ID, name, and price of an item. It interacts with classes like OrderDetail to expedite the ordering process and represents orderable products.

5. Database Module

Example:

public class Database {
    private Connection conn;

    public Database() {
        // Establish the database connection
    }

    public void saveOrder(Order order) {
        String query = "INSERT INTO Orders (...) VALUES (...)";
        // Execute the query to save the order
    }

    public Order getOrder(int orderID) {
        String query = "SELECT * FROM Orders WHERE orderID = ?";
        // Execute the query to get the order
        return null;  // Example placeholder
    }

    public void updateOrder(Order order) {
        String query = "UPDATE Orders SET ... WHERE orderID = ?";
        // Execute query to update the order
    }
}

Explained : The Database class functions as the data access layer, offering ways to use SQL queries via JDBC to save, retrieve, and change orders.
