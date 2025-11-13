# WAD

graph TB
    Client[Frontend Client<br/>HTML / CSS / JS] --> Gateway[API Gateway<br/>Express.js]
    
    Gateway --> AuthService[Auth Service<br/>Register & Login]
    Gateway --> MenuService[Menu Service<br/>Menu Makanan]
    Gateway --> OrderService[Order Service<br/>Cart & Order]
    Gateway --> DeliveryService[Delivery Service<br/>Pengelolaan Delivery]
    
    AuthService -.->|HTTP Request/Response| MenuService
    MenuService -.->|HTTP Request/Response| OrderService
    OrderService -.->|HTTP Request/Response| DeliveryService
    DeliveryService -.->|HTTP Request/Response| AuthService
    
    subgraph ServiceLayer [Service Layer]
        AuthService
        MenuService
        OrderService
        DeliveryService
    end
    
    subgraph DataLayer [Data Layer (SQLite)]
        AuthDB[(Auth DB)]
        MenuDB[(Menu DB)]
        OrderDB[(Order DB)]
        DeliveryDB[(Delivery DB)]
    end
    
    AuthService --> AuthDB
    MenuService --> MenuDB
    OrderService --> OrderDB
    DeliveryService --> DeliveryDB
