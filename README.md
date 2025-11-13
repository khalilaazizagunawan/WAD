# WAD

graph TB
    Client[Frontend Client] --> Gateway[API Gateway]
    
    Gateway --> Service1[Service 1<br/>Provider & Consumer]
    Gateway --> Service2[Service 2<br/>Provider & Consumer]
    Gateway --> Service3[Service 3<br/>Provider & Consumer]
    Gateway --> Service4[Service 4<br/>Provider & Consumer]
    
    Service1 -.->|HTTP Request/Response| Service2
    Service2 -.->|HTTP Request/Response| Service3
    Service3 -.->|HTTP Request/Response| Service4
    Service4 -.->|HTTP Request/Response| Service1
    
    subgraph ServiceLayer [Service Layer]
        Service1
        Service2
        Service3
        Service4
    end
    
    subgraph DataLayer [Data Layer]
        DB1[(Database 1)]
        DB2[(Database 2)]
        DB3[(Database 3)]
        DB4[(Database 4)]
    end
    
    Service1 --> DB1
    Service2 --> DB2
    Service3 --> DB3
    Service4 --> DB4

