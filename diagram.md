```mermaid
classDiagram
    class Customer {
        -String name
        -String phone
        -String address
        -String membershipId
        +register()
        +update()
        +delete()
        +getDiscounts()
    }

    class Order {
        -String orderId
        -DateTime orderTime
        -double totalAmount
        -String status
        -String paymentMethod
        +calculateTotal()
        +updateStatus()
        +addToCart()
        +confirmOrder()
    }

    class Product {
        -String name
        -double price
        -String type
        -int preparationTime
        +updatePrice()
        +updateDetails()
    }

    class SingleProduct {
        -List~String~ ingredients
        -int calories
        -String category
        +getIngredients()
        +updateIngredients()
    }

    class ComboProduct {
        -List~SingleProduct~ items
        +addItem()
        +removeItem()
        +calculateComboPrice()
    }

    class OrderHistory {
        -List~Order~ orders
        -DateTime orderDate
        -double totalSpent
        +viewHistory()
        +getOrderDetails()
    }

    class Staff {
        -String staffId
        -String name
        -String role
        +manageOrders()
        +updateOrderStatus()
        +checkInventory()
    }

    class Supplier {
        -String name
        -String address
        -List~Product~ suppliedProducts
        -double price
        +updateInfo()
        +addNewProduct()
        +updatePrice()
    }

    Customer "1" -- "0..*" Order : places
    Customer "1" -- "1" OrderHistory : has
    Order "1" -- "1..*" Product : contains
    Product <|-- SingleProduct : extends
    Product <|-- ComboProduct : extends
    Staff "1" -- "0..*" Order : manages
    Supplier "1" -- "0..*" Product : supplies
    Order "0..*" -- "1" OrderHistory : recorded in
