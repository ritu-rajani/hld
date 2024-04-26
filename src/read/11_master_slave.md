# Master Slave System
>- In Master-Slave systems, Exactly one machine is marked as Master, and the rest are called
Slaves.
>
# Type of Architecture
## 1. Master Slave systems that are Highly Available and are eventually consistent.
>- Steps:
>- 1. Master system takes the write.
   If the write is successful, return success.
>- 2. Try to sync between slave1 and slave2.
>- Example: Splunk, where we have a lot of logs statements now, there is so much throughput
   coming in, we just want to process the logs even if we miss some logs, it’s ok.

## 2. Master-Slave systems that are Highly Available and eventually consistent:
>- Steps:
>- 1. The Master system takes the write, and if one slave writes, then success is
   returned.
>- 2. All slaves sync.
>- Example: Computing news feed and storing posts, there we don’t want the post to be lost; they
   could be delayed but eventually sync up.

## 3. Master Slave that are Highly Consistent:
>- Steps:
>- 1. Master and all slave take the writes, if all have written, then only return success. 
>- Example: The banking system.

# Internals of Master-Slave systems
>- All writes first come to Master only.
>- Reads can go to any of the machines.
>- Whenever the Master system dies, a new election of the master will take place based on
a different elections algorithm.

# Drawbacks of Master-Slave System:
1. A single master can become the bottleneck when there are too many writes.
2. In highly consistent systems, slaves increase which increases the rate of failure
   and latency also increases.
   For example, For highly consistent systems, if there are 1000 slaves, the
   Master-slave system will not work. We have to do more sharding.


