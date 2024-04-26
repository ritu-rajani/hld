# Caching
>- Process of storing frequently used data near to you and in a faster storage than db is called Caching.
>- Can be done any where example browser, appserver , etc.

# Types of Caching

## 1. In-Browser Caching
- First place we start Caching is inside the browser.
- As soon as we type the website name instead of directly going to DNS server , it checks first inside its cache if domain name mapping with this website is available.
- We can cache some IPs so that browser doesn't need to communicate with the DNS server every time to get the same IP address.
- This caching is done of smaller entries that are likely not to change very often and is called in-browser caching. 
- Browser caches DNS and static information like images, videos, and JavaScript files. 
- This is why a website takes time to load for the first time but loads quickly because the browser caches the information.

## 2. CDN
- Content delivery network
- When you try to access from your browser, a request is made to the load balancer, and then it goes to the application server and requests files from the file storage.
- Transferring of files in the same region / country is faster but can take time when machine is located in different content/country.
- Every user across the globe should have good and fast user experience and hence to solve this problem we have CDN.
- It is mainly used for file storage like multimedia (images/videos) because  receiving the HTML part/ code part is quick since it is much smaller than the multimedia images/videos/big docs.
- Companies like Akamai,Cloudflare,CloudFront by Amazon,Fastly provides CDN services.
- They have storage machines across the globe.
- They store the data and distribute to all regions  and provide different CDN links to access data in a particular region. 
- Accessing these files from the nearest region happens at a much larger pace. 
- Also, we pay per use for using these CDN services.

> One question you might think is how your machine talks to the nearest region only(gets its IP, not of some machine located in another region), when CDN has links for all the regions. 
> Well, this happens in two ways:
> 1. A lot of ISP have CDN integrations. Tight coupling with them helps in giving access to the nearest IP address. For example, Netflix’s CDN does that.
> 2. Anycast (https://www.cloudflare.com/en-gb/learning/cdn/glossary/anycast-network/)
> 
> This CDN process to get information from the nearest machine is also a form of caching.

## 3. Local Caching
- It is caching done on the application server/database server so that we don't have to hit the database repeatedly to access data.

## 4. Global Caching
- Global caching stores data in a location that is accessible across multiple devices, processes, or users within a distributed computing environment.
- Cached data is shared and can be accessed by multiple clients or processes simultaneously.

# Problems related to caching
- Cache is limited in size
- It is not the actual source of truth; that is, the actual data is somewhere else. It stores a replica of data.
- Data can become stale and inconsistent with time (Data in Database - actual source of truth - changes. But is not reflected in cache)

# Cache Invalidation Strategy
- One solution that is proposed so that cache doesn’t become stale is :

## 1. TTL (Time to Live) 
- Entries in the cache will be valid for only a period. And after that, to again get the entries, you need to fetch them again.
- So, for example, if you cache an entry X at timestamp T with TTL of 60 seconds, then for all requests asking for entry X within 60 seconds of T, you read directly from cache. When you go asking for entry X at timestamp T+61, the entry X is gone and you need to fetch again. 
- low TTL can results in lots of cache misses and expires the file very frequently
- high TTL can results in stale files for longer period and can be inconsistent

## 2. Keeping cache and DB in sync :
- We can keep cache and db in sync with these strategies : 

***1. Write Through Cache***
- whenever there is a write request it first updates the cache and then updates the db
- if db updates fail , reverts from cache as well.
- reading is faster , writing is slower
- For a read-heavy system, this could be a great approach.<br>
***2. Write Back Cache***
- First, the write is written in the cache. 
- The moment write in the cache succeeds, you return success to the client. 
- Data is then synced to the database asynchronously (without blocking current ongoing request).
- The method is preferred where you don't care about the data loss immediately, like in an analytic system where exact data in the DB doesn't matter, and analytical trends analysis won't be affected if we lose data or two.
- It is inconsistent, but it will give very high throughput and very low latency.
- Async version of write through.<br>
***3. Write Around Cache***
- writes are written directly to database and cache is updated after TTL/any mechanism.
- TTL or any similar mechanism is used to fetch the data from the database to cache to sync with it.

# Cache Eviction Strategy
Cache can hold the limited data and hence there are various eviction strategies to remove data from the cache to make space for new writes. Some of them are:
- FIFO (First In, First Out)
- LRU (Least Recently Used)
- LIFO (Last In, First Out)
- MRU (Most Recently Used)
The eviction strategy must be chosen based on the data that is more likely to be accessed. The caching strategy should be designed in such a way that you have a lot of cache hits than a cache miss.

# Global Caching vs Local Caching
Deciding between using a local cache or a global cache depends on various factors such as the specific requirements of your application, the scale of your system, and the nature of the data being cached. Here are some considerations to help you make that decision:

1. **Scope of Data Access**: Consider whether the data that needs to be cached is specific to each user or request (local scope) or if it is shared across multiple users or requests (global scope). If the data is specific to each user or request, a local cache might be more appropriate. If the data is shared across multiple users or requests, a global cache might be necessary.

2. **Performance Requirements**: Evaluate the performance requirements of your application. Local caches can provide faster access to data since they are typically located closer to the application, but they might not be suitable for sharing data across different instances or servers. Global caches can provide shared access to data but might introduce additional latency due to network communication.

3. **Consistency Requirements**: Consider the consistency requirements of your application. Local caches can provide strong consistency guarantees since they are typically managed within the same process or machine. Global caches might introduce eventual consistency issues due to network latency and distributed nature.

4. **Scalability**: Think about the scalability requirements of your application. Global caches can be scaled horizontally to accommodate increasing load by adding more cache nodes, but they might introduce additional complexity in managing distributed systems. Local caches might be easier to manage but could become a bottleneck as the application scales.

5. **Data Size**: Consider the size of the data being cached. Local caches are suitable for caching small to moderate-sized data since they are typically limited by the resources of the application process or machine. Global caches, especially distributed caching solutions, can handle larger datasets more efficiently.

6. **Failure Tolerance**: Evaluate the tolerance to failures in your application. Global caches, especially distributed ones, might introduce additional points of failure due to network communication and distributed nature. Local caches are more resilient to network failures but might not be suitable for high availability scenarios.

7. **Cost Consideration**: Consider the cost implications of using a global cache versus a local cache. Global caching solutions might involve additional infrastructure costs for setting up and maintaining distributed systems. Local caches might be more cost-effective for smaller-scale applications.

Ultimately, the decision between using a local cache or a global cache depends on balancing these factors according to the specific requirements and constraints of your application. It's often beneficial to start with a simple local cache and then evaluate the need for a global cache as your application evolves and scales.





