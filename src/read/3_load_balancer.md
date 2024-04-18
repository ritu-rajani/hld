# Load Balancer
>- A Load Balancer is a physical/virtual device used to balance the network load across Web-Servers.
>- A load balancer is a device that distributes network or application traffic across several servers. 
>- It helps scale horizontally across an ever-increasing number of servers.
>- Acts as gatekeeper/entry point
>- The entire traffic, irrespective of whether it is from a handheld device or a system, arrives directly at the load balancer. 
>- The load balancer then sends the traffic to one of the available servers, based on certain decision-making algorithms.

# Working
Load balancers employ various techniques and algorithms to distribute incoming traffic across multiple servers or computing resources. Here's how they typically accomplish this:

1. **Health Checks**: Load balancers continuously monitor the health and availability of backend servers by periodically sending health check requests. If a server fails to respond or is determined to be unhealthy based on predefined criteria (such as response time or error rate), the load balancer removes it from the pool of available servers.

2. **Load Balancing Algorithms**: Load balancers use different algorithms to determine how incoming requests should be distributed among the available servers. Some common load balancing algorithms include:

    - Round Robin: Requests are distributed sequentially to each server in the pool in a circular manner.
    - Least Connections: Requests are sent to the server with the fewest active connections, helping to evenly distribute the load based on server capacity.
    - Weighted Round Robin: Servers are assigned weights based on their capacity or performance, with higher-weighted servers receiving more requests.
    - Least Response Time: Requests are directed to the server with the lowest response time, optimizing for faster processing and reduced latency.

3. **Session Persistence/Sticky Sessions**: Load balancers can maintain session persistence by associating a client's session with a specific backend server for the duration of the session. This ensures that all requests from the same client are routed to the same server, which is essential for applications requiring stateful interactions or session management.

4. **Dynamic Configuration**: Load balancers often support dynamic configuration to adapt to changing traffic patterns or server conditions. Administrators can adjust load balancing settings, add or remove servers from the pool, or change routing rules without disrupting ongoing traffic.

5. **Content-based Routing**: Advanced load balancers can inspect the content of incoming requests, such as URL paths, HTTP headers, or request parameters, and make routing decisions based on predefined rules or policies. This allows for more sophisticated traffic management, such as routing requests to specific backend servers based on request characteristics.

By combining these techniques and algorithms, load balancers can effectively distribute incoming traffic across multiple servers or computing resources, ensuring high availability, scalability, and performance for applications and services.

# How does Load balancer knows  machines are alive?
1. **Push Technique (Health Check)** 
   - The load balancer sends HTTP requests to a predefined endpoint on each backend server and evaluates the response status code to determine server health.
   - For example, a 200 OK response indicates that the server is healthy, while other status codes (e.g., 404 Not Found, 50x Server Error) may indicate server issues.
2. **Pull Technique (HeartBeat)** 
   - The heartbeat technique in load balancing involves using periodic heartbeat messages exchanged between the load balancer and backend servers to determine the health and availability of servers.
   - The load balancer monitors the receipt of heartbeat messages from each backend server. 
   - If a server fails to send a heartbeat message within a specified timeout period, the load balancer considers the server to be unresponsive or unavailable.

