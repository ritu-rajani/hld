# CAP Theoram
>- The CAP theorem, also known as Brewer's theorem, is a fundamental principle in distributed systems theory, proposed by computer scientist Eric Brewer in 2000. 
>- It states that in a distributed data store, it's impossible to simultaneously guarantee all three of the following properties:
>- 1. Consistency (C): Every read receives the most recent write or an error.
>- 2. Availability (A): Every request receives a response, every system is always up and running.
>- 3. Partition tolerance (P): The system continues to operate despite network partitions or communication failures between nodes.

In simpler terms, when designing a distributed system, you can only prioritize two out of the three properties: consistency, availability, and partition tolerance.
This theorem has significant implications for designing and understanding distributed systems, as it helps in making trade-offs between these properties based on specific requirements and constraints.

Let's break down the CAP theorem with some examples:

1. **Consistency (C)**:
    - Imagine a distributed database where multiple nodes store copies of the data. In a consistent system, when a write operation is performed on one node, all subsequent read operations from any node will return the updated value.
    - Example: In a banking application, if you transfer money from one account to another, you expect that subsequent balance inquiries will reflect the transfer immediately across all nodes in the system.

2. **Availability (A)**:
    - Availability ensures that every request to the system receives a response, even if it means returning stale or outdated data. This means that the system remains operational and responsive to user requests even under adverse conditions.
    - Example: Consider a social media platform where users are constantly posting updates. Even if the system experiences network issues or node failures, users should still be able to access the platform and view existing posts, even if they're not the absolute latest ones.

3. **Partition Tolerance (P)**:
    - Partition tolerance refers to the system's ability to continue functioning despite network partitions or communication failures between nodes. In other words, the system should be resilient to network issues or node failures without sacrificing either consistency or availability.
    - Example: In a globally distributed system where data is replicated across different regions, network partitions can occur due to network congestion or outages. The system should be able to handle these partitions gracefully without losing data consistency or becoming unavailable to users in any region.

Now, according to the CAP theorem, you can only prioritize two out of these three properties at any given time. Here are some common trade-offs:

- **CP Systems**: 
- Prioritize consistency and partition tolerance over availability. 
- These systems sacrifice availability to ensure that data consistency is maintained even during network partitions.
- example - Amazon , BMS
- **AP Systems**: 
- Prioritize availability and partition tolerance over consistency. 
- These systems prioritize remaining operational and responsive, even if it means returning potentially inconsistent or outdated data during network partitions.
- example - facebook , netflix
- **CA Systems**: 
- Prioritize consistency and availability but may sacrifice partition tolerance. 
- These systems typically operate in environments where network partitions are rare, allowing them to maintain both consistency and availability without sacrificing partition tolerance.
- example - local caches(no partitions are there in local caches)

Different distributed systems make different trade-offs based on their specific requirements and use cases.