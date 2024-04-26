# What’s system design?

>- Low level design covers the structure of code in a given component. 
>- However, a large scale system will have multiple components / services. High level design is about the optimal design of which components to have for a fast and efficient system. 
>- It is the process of designing the architecture, components , modules , interfaces ad data to meet the requirement and build and efficient system
>- ensuring factors like scalability , reliability , performance and security


# What is Distributed System and why do we need it?
>- It is a collection of independent computers that communicate and coordinate through a network.
>- It appears to be a single computer to a user but it is a single coherant system with distributed load.
>- Problems it solve:
>- 1. Scalabilty : can scale horizontally by adding/removing machines in a network , distributes the increasing workload
>- 2. SPF : It solves the problem of single point of failure , if one machines dies it doesn't hamper the whole system. Other nodes can also take responsibility of failed nodes.
>- 3. Performance : By distributing tasks on multiple machines, reduces the latency by parallel computations and data processing
>- 4. Data Replication : Can replicate data in multiple machines , effective against fault tolerance and data loss
>- 5. Geographical Distribution : Can easily deploy application multiple locations, reduce latency for users across the globe.

# How our browser processes any request?
When you enter a URL into your browser and hit Enter, several steps occur behind the scenes to process your request and display the requested webpage:

1. **URL Parsing**: The browser parses the entered URL to extract components such as the protocol (HTTP/HTTPS), domain name, and path.

2. **DNS Lookup**: The browser checks its cache to see if it has the IP address corresponding to the domain name. If not, it performs a Domain Name System (DNS) lookup to resolve the domain name to an IP address. Once resolved, the browser can send the request to the server.

3. **Establishing a TCP Connection**: The browser initiates a Transmission Control Protocol (TCP) connection with the server using the resolved IP address and the appropriate port (typically port 80 for HTTP and port 443 for HTTPS).

4. **Sending the HTTP Request**: The browser constructs an HTTP request based on the parsed URL and sends it to the server over the established TCP connection. The request includes information such as the HTTP method (GET, POST, etc.), headers (e.g., User-Agent, Accept), and sometimes a request body (for methods like POST).

5. **Server Processing**: Upon receiving the request, the server processes it by fetching the requested resource (e.g., HTML file, image, script) from its storage, executing server-side code (if any), and generating an appropriate HTTP response.

6. **Receiving the HTTP Response**: The server sends back an HTTP response to the browser over the same TCP connection. The response includes a status code (indicating the success or failure of the request), headers (e.g., Content-Type, Content-Length), and the response body (e.g., HTML content, image data).

7. **Rendering the Webpage**: The browser receives the HTTP response and starts rendering the webpage. It parses the HTML content to build the Document Object Model (DOM), processes CSS stylesheets to create the Render Tree, and executes JavaScript code to add interactivity and dynamic content.

8. **Fetching Additional Resources**: The browser may encounter external resources referenced in the HTML content (e.g., images, scripts, stylesheets), and it initiates separate HTTP requests to fetch each resource in parallel.

9. **Displaying the Webpage**: As resources are fetched and processed, the browser continues rendering the webpage, laying out elements on the screen according to CSS styles, and displaying the final rendered content to the user.

Throughout this process, the browser may also perform various optimizations and caching mechanisms to improve performance, such as caching DNS records, storing cached copies of resources, and reusing TCP connections for subsequent requests to the same server.

# What is DNS?
> Domain name system is the hierarchical naming system for computer or services or any resource that are connected to internet.
> It is decentralized
> It is like a registry which maps all the domain names to ip addresses of systems over internet

# ICANN
>- Internet Corporation for Assigned Names and Numbers
>- is a non profit organization responsible for coordinating and overseeing global DNS, ipaddress allocation.
>- Manages the allocation of domain names and IP addresses, ensures they are unique and globally accessible.

