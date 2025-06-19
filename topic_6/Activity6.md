# Activity 6  
**Chris King**  
Grand Canyon University  
SDD-630 Mobile Software Development  
Professor Estey  
June 18, 2025 

---


### Data Storage Technologies and Recommendation for TARS

## Introduction

In today's application development landscape, choosing the right data storage technology directly impacts performance, scalability, cost, and future maintenance. Each database type, relational, document, graph, and search engine, was designed with a unique problem in mind. For the TARS mobile app, which focuses on digit recognition and visualized neural activity, it’s critical to align our database choice with the structure of our data and user interactions.

This document outlines the strengths and weaknesses of each major database category and concludes with a recommendation for the best database selection for TARS.

---

## Relational Databases

### Strengths
Relational databases, like MySQL, PostgreSQL, and Oracle, are the oldest and most mature form of data storage. They're built on structured schemas, enforce data integrity via constraints, and support powerful SQL queries. They shine in transactional use cases where data consistency and atomicity are critical.

### Weaknesses
The flip side is rigidity. Schema changes are slow, and handling unstructured or rapidly evolving data can be painful. Scaling relational databases horizontally (across multiple nodes) is more complex compared to NoSQL solutions. They're also less ideal for handling nested or highly variable data structures.

### Best Use Cases
- E-commerce systems (e.g., order processing, user accounts)
- Financial applications
- Enterprise resource planning (ERP)

---

## Document Databases

### Strengths
Document databases like MongoDB and DynamoDB store data in flexible, semi-structured formats like JSON or BSON. They allow for rapid iteration and schema evolution, perfect for fast-moving development environments. You can store nested objects, arrays, and varied structures without redefining your schema.

They're horizontally scalable by default, making them ideal for large-scale or cloud-native applications. Reads and writes are fast, especially when optimized with proper indexing.

### Weaknesses
While flexible, document stores lack the strong ACID guarantees of relational databases unless you add extra complexity. They also require careful design to avoid data duplication or bloated document sizes. However, certain DBMS systems such as DynamoDB provide powerful API's to remedy this.

### Best Use Cases
- Content management systems
- Real-time analytics platforms
- Mobile applications with rapidly evolving data
- Small to large microservices

---

## Graph Databases

### Strengths
Graph databases like Neo4j or Amazon Neptune store data as nodes and relationships. They're purpose-built for use cases involving highly interconnected data, such as social networks, recommendation engines, or fraud detection systems.

They support fast traversal across relationships without expensive joins, which relational databases struggle with.

### Weaknesses
Graph databases are niche. They have a learning curve and are overkill for applications that don’t rely heavily on complex relationships. They also don’t perform as well in aggregate-heavy scenarios.

### Best Use Cases
- Social networks (e.g., LinkedIn’s connection graph)
- Knowledge graphs
- Recommendation engines (e.g., “users who liked this also liked…”)

---

## Search Engine Databases

### Strengths
Technologies like Elasticsearch and Splunk Search are designed for full-text search and analytics over large datasets. They're lightning-fast when it comes to searching across millions of documents, handling fuzzy matching, synonyms, and weighted results.

Search engines also support filtering, aggregations, and faceted search, making them great complements to primary databases in search-heavy applications.

### Weaknesses
Search databases aren’t great for transactional workloads or complex data relationships. They’re eventually consistent and don’t have native support for complex joins or strict ACID compliance.

### Best Use Cases
- Log analysis
- In-app search
- E-commerce product catalogs with complex filtering

---

## Recommendation for TARS

For the TARS mobile app, which handles digit recognition, user interactions, and possibly some logging or search functionality, TARS would benefit the most from the lightweight, fast nature of a **document database**, specifically something like **DynamoDB**.

### Why Document Storage Works for TARS

- **Schema Flexibility**: Our app evolves quickly. Whether storing digit stroke data, user history, model predictions, or visualization configurations, we need flexibility to add or remove fields without massive migrations.
- **Nested Structures**: User input, like drawing data or preprocessing metadata, is naturally nested and variable. Document storage handles this smoothly.
- **Speed and Scale**: TARS may grow to support many users generating frequent data, or multiple neural network architectures. Document databases offer horizontal scaling and fast reads/writes out of the box.
- **Developer Velocity**: As a lean educational app, we benefit from reduced overhead in managing schemas and migrations, which lets us iterate quickly.

### Future Considerations

For search functionality, say, letting users search for previous drawing sessions or explore training data—we could pair DynamoDB with **Elasticsearch** for fast querying and filtering. Something like Splunk Search can also be implemented for logging and monitoring.

---

## Conclusion

Each storage technology serves a different need. Relational databases are unbeatable in highly structured environments. Document databases offer agility and scalability. Graph databases excel in relationship-heavy data. And search engines dominate full-text and analytics use cases.

For TARS, a document database like DynamoDB is the best business and technical fit—balancing performance, flexibility, and future growth.

