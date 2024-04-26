# PACELC theorem
>- is built upon the CAP theorem and adds additional considerations.
>- It extends the CAP theorem by considering the trade-offs between consistency and latency in distributed systems, especially under partition conditions.
>- The PACELC theorem suggests that during network partitions (P), a distributed system must choose between ensuring high availability (A) and maintaining consistency (C) or providing low latency (L) with eventual consistency (C).
>- example - write through cache is high lantency and consistent system. Whereas write back cache is low latency and eventually consistent system.
> (eventually consistent system means not always consistent and data is sync later not immediately)
