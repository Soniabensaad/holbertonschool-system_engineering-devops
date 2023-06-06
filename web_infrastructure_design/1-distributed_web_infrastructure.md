# <p align="center">Distributed Web Infrastructure</p>
<img src="" width="100%">

### Requirements

For this infrastructure, the requirements are as follows:

- 2 additional servers
- 1 web server (Nginx)
- 1 application server
- 1 load balancer (HAproxy)
- 1 set of application files (your code base)
- 1 database (MySQL)

### Description of the infrastructure
  
. Server

The server is a physical or virtual machine that hosts the entire web infrastructure.
It runs the necessary software and services to serve the website.
. Domain Name and DNS Record

The domain name (foobar.com) is the human-readable address used to identify the website.
The www record configured for the domain points to the server's IP address (8.8.8.8).
DNS record for www:

The DNS record for www in www.foobar.com is a CNAME (Canonical Name) record.
It is used to alias or map the www subdomain to the root domain (foobar.com).

. Web Server (Nginx)

The web server (Nginx) receives incoming HTTP requests from the user's browser.
It listens on port 80 and handles the initial processing of the request.
It retrieves the requested resources and sends the response back to the user's browser.
. Application Server

The application server runs the code base of the website.
It processes dynamic content, executes server-side code, and interacts with the database.
It communicates with the web server to generate the appropriate response.
The application files contain the source code and related files of the website.
They include HTML, CSS, JavaScript, server-side scripts, and any other necessary files.
. Database (MySQL)

The database (MySQL) stores and manages the website's data.
It is used to persist and retrieve information for dynamic content.
The application server communicates with the database to perform data operations.
. Server-User Communication
The server communicates with the user's computer over the Internet using the HTTP protocol.
When the user requests a webpage, the server responds by sending the requested content back to the user's browser.
### Specificities of the infrastructure
  
- `Load splitter distribution algorithm`: The distribution algorithm used in HAproxy can be configured according to specific needs, such as round-robin, minimum number of connections, or IP-hash. This algorithm determines how requests are distributed among the available servers.

- `Load balancer configuration`: The load balancer is configured in active-passive mode. This means that only one server is active and processes incoming requests, while the other servers remain in passive mode and take over only in the event of an active server failure. This guarantees high availability of the website.

- `Primary-Replica database cluster`: The database cluster is configured using the Primary-Replica (Master-Slave) model. The primary node (master) manages write operations, while replicated nodes (slaves) manage read operations. The data is replicated asynchronously from the primary node to the replicated nodes to ensure data consistency and better availability.

- `Difference between the primary node and the replicated node`: The primary node is responsible for writing and updating the database. It is used by the application for write requests. The replicated nodes are used for read operations and serve as a backup in the event of a failure of the primary node. They guarantee high availability and improve performance by distributing read operations between replicated nodes.
  

### Potential infrastructure problems.
  
1. `Single point of failure (SPOF)`:

- Each component of the infrastructure can become a single point of failure. In the event of a server, load balancer or database failure, this may lead to a service interruption or unavailability of the website.

2. `Security issues`:

- The current infrastructure does not include firewalls, which makes it vulnerable to attacks and intrusions. It is recommended to add a firewall to control network traffic and protect servers from potential threats.

- The absence of HTTPS (secure HTTP) exposes communications between users and the web server to the risk of data breach. The implementation of HTTPS is essential to secure exchanges and protect data confidentiality.

3. `Lack of supervision`:

- The infrastructure does not have a monitoring system in place. It is recommended to implement a monitoring system to monitor performance, detect problems and failures, and take preventive or corrective measures.
