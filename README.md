
# Kookaburra Spring Boot Starter

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-2.7.18-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Spring Cloud](https://img.shields.io/badge/Spring%20Cloud-2021.0.8-brightgreen.svg)](https://spring.io/projects/spring-cloud)

Koala Spring Boot Starter is a robust and feature-rich library designed to extend the capabilities of Spring Boot 2.7.18 and Spring Cloud 2021.0.8. It simplifies the process of building decentralized, cluster-aware applications, and provides seamless integration with multiple service discovery mechanisms. This component enables your Spring Boot projects to operate as a cohesive, fault-tolerant cluster with minimal configuration.

---

## Features

### 1. Decentralized Clustering and Leader Election

Koala Spring Boot Starter enables applications with the same `spring.application.name` to form a decentralized cluster. This cluster operates without a central coordinating server, providing the following capabilities:
- **Peer-to-Peer Service Discovery**: Each node in the cluster can automatically discover other nodes, allowing for seamless inter-node communication.
- **Cluster-Wide Notifications**: Nodes can notify others of state changes, enabling real-time cluster state management.
- **Automatic Leader Election**: A leader is automatically selected among the nodes in the cluster. If the leader node goes offline, the component detects the failure and triggers a re-election to ensure high availability.
- **Fault Recovery**: When a node rejoins the cluster, it is reintegrated into the system, and the cluster state is updated dynamically.

This feature is invaluable for scenarios requiring high availability, distributed task coordination, and failover handling.

---

### 2. Built-in Redis-Based Registry

Koala Spring Boot Starter includes an embedded service registry implemented on top of Redis 7.x. This lightweight, high-performance registry eliminates the need for an external service discovery mechanism. Key characteristics include:
- **Scalable and High Throughput**: Utilizes Redis as a distributed in-memory datastore, ensuring low latency and high availability.
- **Dynamic Service Registration**: Services register and deregister dynamically based on their lifecycle events.
- **Cluster Metadata Management**: Stores cluster-wide metadata efficiently, facilitating advanced node management capabilities.

This built-in registry makes it ideal for projects that prefer minimal external dependencies while leveraging the power of Redis.

---

### 3. Integration with Third-Party Registries

Koala Spring Boot Starter seamlessly integrates with popular service registries such as **Eureka**, **Zookeeper**, and other Spring Cloud-supported discovery mechanisms. This provides the flexibility to use existing infrastructure while maintaining a unified programming model:
- **Unified API**: A consistent and developer-friendly API abstracts the underlying registry, making it easy to switch between different discovery mechanisms.
- **Polyglot Support**: Compatible with hybrid environments where some microservices might use different registries.
- **Automatic Fallbacks**: If the primary registry is unavailable, the component can failover to a backup registry, ensuring uninterrupted operation.

This extensibility ensures that developers can harness the full potential of Koala Starter while adapting it to varied deployment architectures.

---

### 4. Enhanced Feign Client with Load Balancing

Koala Spring Boot Starter extends the capabilities of Spring Cloud Feign by introducing built-in load balancing, supporting advanced routing and failover mechanisms:
- **Load Balancing Algorithms**: Provides multiple strategies, including round-robin, least connections, weighted distribution, and custom algorithms, giving developers full control over traffic distribution.
- **Dynamic Client Discovery**: Feign clients can dynamically discover and interact with services in the cluster, even in mixed environments.
- **Resilience Features**: Includes circuit breaker patterns, retry mechanisms, and timeout management, ensuring reliability in unstable networks.
- **Utility Libraries**: A rich set of utility classes simplifies common tasks such as serialization, request customization, and debugging of Feign calls.

These features make Koala Starter an excellent choice for distributed systems requiring robust communication patterns and scalable service interactions.

---

## Getting Started

### 1. Add Dependency

Add the following dependency to your `pom.xml`:
```xml
<dependency>
    <groupId>com.example</groupId>
    <artifactId>koala-spring-boot-starter</artifactId>
    <version>1.0.0</version>
</dependency>
```

### 2. Configure Application Properties

Add the necessary configurations to your `application.yml` file:
```yaml
spring:
  application:
    name: your-application-name
koala:
  cluster:
    enabled: true
    registry:
      type: redis # Options: redis, eureka, zookeeper
      address: redis://localhost:6379
```

### 3. Start Your Application

Ensure Redis is running if you're using the built-in registry. Run your Spring Boot application, and it will automatically participate in the cluster.

---

## Documentation

For more detailed instructions and advanced configurations, refer to the [Official Documentation](https://github.com/paganini2008/koala-spring-boot-starter/wiki).

---

## Contributing

We welcome contributions! Please refer to the [Contributing Guide](CONTRIBUTING.md) for details on how to get involved.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Koala Spring Boot Starter empowers developers to create high-performance, scalable, and fault-tolerant distributed systems with minimal effort. Its rich feature set makes it an essential tool for modern microservice architectures.
