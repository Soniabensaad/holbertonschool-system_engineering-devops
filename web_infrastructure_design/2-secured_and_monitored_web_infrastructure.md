# <p align="center"> Secured And Monitored Web Infrastructure</p>
<img src="https://github.com/Soniabensaad/holbertonschool-system_engineering-devops/blob/main/web_infrastructure_design/2-secured_and_monitored_web_infrastructure.jpg" widht="100%">

### Requirements

For this infrastructure, the requirements are as follows:

- 3 firewalls
- 1 SSL certificate to serve www.foobar.com via HTTPS
- 3 monitoring clients (data collector for Sumo Logic or other monitoring services)

### Description of the infrastructure

1. `Firewalls`.

- Three firewalls are added to provide network security and control traffic flow.
They act as barriers between the internet and the servers, enforcing access rules and protecting against unauthorized access.

2. `SSL certificate for HTTPS`

- We use an SSL certificate to serve the website www.foobar.com via HTTPS. This makes it possible to encrypt communications between users and the web server, thus guaranteeing the confidentiality and integrity of the data exchanged.

3. `Surveillance clients`

- Monitoring clients are deployed on servers to collect data on infrastructure performance, availability and security. They send the collected information to a centralized data collector, such as Sumo Logic, for analysis and tracking.

### Specificities of the infrastructure

**Role of firewalls:**

  - Firewalls are essential security devices that filter network traffic according to predefined rules. They control network access, block suspicious traffic and protect servers from unauthorized attacks and intrusions.

**Importance of HTTPS traffic:**

  - Traffic is served via HTTPS to ensure the security of communications. The HTTPS protocol uses an SSL certificate to encrypt the data exchanged between the user's browser and the web server. This prevents attackers from intercepting or modifying sensitive data passing between the two.

**Role of surveillance:**

  - Monitoring is a crucial element of the infrastructure. It collects data on server performance, availability and security. Monitoring makes it possible to identify potential problems, analyze trends, and take measures to improve the efficiency and reliability of the infrastructure.

**Data collection by the monitoring tool:**

  - The monitoring tool uses clients deployed on the servers to collect the data. These clients send information such as performance metrics, system logs, and events to a centralized data collector, such as Sumo Logic. The data collected is then analyzed to assess the state of the infrastructure and make informed decisions.

**Monitoring of the request rate per second (QPS) of the web server:**

  - To monitor the rate of requests per second from the web server, you can configure monitoring clients to collect metrics related to requests, such as the total number of requests received per second. This collected data can be analyzed to evaluate server performance and identify any throughput or capacity problems.

### Potential infrastructure problems.

1. SSL termination problem at the load splitter level:

  - SSL termination at the load balancer can be a problem, because it means that traffic between the load balancer and the internal servers is transmitted in clear text. This can expose sensitive data within the infrastructure in the event of network compromise. It is recommended to configure SSL termination at the internal server level for better security.

2. Problem of having a single MySQL server capable of accepting writes:

  - Having a single MySQL server capable of accepting writes can create a single point of failure and cause availability problems. If this server fails, the application will no longer be able to write new data to the database. It is recommended to set up a cluster or replication configuration to ensure redundancy and high data availability.

3. Problem of having servers with the same components (database, web server and application server):

  - Having servers with the same components can be a problem in terms of flexibility and scalability. If all servers have the same roles, it can be difficult to distribute the load optimally and evolve the infrastructure according to needs. A more modular and distributed approach with specific roles for each server can allow for better scalability.
