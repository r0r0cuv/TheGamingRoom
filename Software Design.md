 

# Draw it or Lose it
# CS 230 Project Software Design 
Version 1.0

 ![gaming room](gamingRoomPic.jpg)


Document Revision History

Version:   1.0		

Date:  	   04/16/2023 	     

Author:	   Rosalie Reblora             

Comments:  Updated Recommendations section with system architecture, memory, storage, and security details.


#  Executive Summary

The Gaming Room would like to transition their Android game Draw It or Lose It into a web-based application that allows for cross-platform play. We will implement object-oriented design and software design patterns to create the application. An abstract base class called Entity will hold shared attributes like id and name. Game, Team, and Player will inherit from Entity. Code reuse will be increased while maintaining a higher level of organization.

We will use the Singleton pattern to limit GameService to only one instance in memory. The Iterator pattern will allow us to iterate through our collections to check that names are unique among games, teams, and players.

They also need a system that allows for more than one team or player, but each game, team, and player must have a unique name. Also, there should only be one instance of GameService in memory.

# Requirements

The client requires the following:
•	The game must support one or more teams
•	Each team must have multiple players
•	Game and team names must be unique
•	The system must allow users to check if a name is already in use
•	Only one instance of the game service can exist in memory
•	The application must be web-based and support multiple platforms


# Design Constraints

There are multiple constraints on the design of this application.

1. It must run on multiple platforms - we will be using Java as it is platform-independent.
2. It must run as part of a distributed environment - Users will be running our program over a network. This creates latency and scalability issues. They will also be using it concurrently.
3. Only one instance of game service should exist - constrains the way we create new objects. We will use the Singleton pattern to implement this.
4. Names must be unique - We will need to search through our existing objects during creation with some iteration. Then we will add our constraints.
5. Application must be written with clean code - So we can scale it and add features in the future.


# Operating Systems Architectures
The recommended Linux server platform uses a multiuser, multitasking architecture with protected processes, virtual memory, and a hierarchical file system. Linux separates user space from kernel space, which improves system stability and security because applications cannot directly control hardware or other protected resources without going through the operating system. Linux also uses process scheduling and memory management features to support many simultaneous users and requests efficiently. The kernel documentation describes resource control through cgroups, which can partition and limit system resources for groups of processes. 
For this game, the architecture should follow a three-tier design:
1.	Presentation layer for the web or mobile client 
2.	Application layer for game logic, sessions, and scoring 
3.	Data layer for persistent storage such as users, teams, games, and image metadata 
This architecture supports scalability because each layer can be updated or expanded independently. A reverse proxy such as NGINX can sit in front of the application servers to manage HTTPS connections and distribute traffic across multiple instances. NGINX officially supports reverse proxying, load balancing, and caching, which makes it suitable for high-availability web applications. 

# Domain Model

Below is the UML diagram displaying our game application and relationship between components.The Entity class holds all attributes that are shared amongst the Game, Team, and Player classes (id and name). Since Game, Team, and Player all inherit from Entity, this reduces code duplication and allows easier maintenance (inheritance).GameService is responsible for all objects in the application and regulates who has access to them. This class follows the Singleton pattern. Only one GameService instance can exist in memory at one time. GameService also follows the Iterator pattern when it searches through a collection of objects. Additionally, GameService makes sure that names are not duplicated before inserting a new object.

Game will store multiple Teams, and Team will store multiple Players. This relationship satisfies the requirement that states a game can have many teams, and a team can have many players. It also shows hierarchy (has-a) relationships.

Lastly, the diagram shows examples of encapsulation. Each class manages its own data and methods. Access to this data is regulated by the methods provided in each class.

![UML Diagram](images/uml-diagram.jpg)

 # Evaluation

Development Requirements	Mac	Linux	Windows	Mobile Devices
Server Side	Macs offer developers a stable UNIX based system that they like. They also tend to be pricey and are rarely used as large server deployments.	Linux is the best option for servers due to its stability, security, and cost-effectiveness. It supports most web technologies and is widely used in production environments.	Windows servers are user-friendly and integrate well with Microsoft tools, but they require licensing costs and are less flexible than Linux.	Mobile devices are not suitable for server-side hosting due to limited processing power and scalability.
Client Side	Supports web applications well, but development may require Apple-specific tools and higher cost.	Flexible and free, but may require more technical expertise for support.	Most widely used platform, making it easier to support users with lower development cost and time.
	Require responsive design or mobile apps, increasing development time and complexity but essential for user accessibility.
Development Tools	Tools include Xcode, IntelliJ IDEA, and Visual Studio Code. Supports Java, Swift, and web technologies.	Supports tools like Eclipse, VS Code, and Git. Ideal for Java, Python, and web development.	Supports Visual Studio, Eclipse, and IntelliJ. Strong support for Java, C#, and web applications.	Development tools include Android Studio and Xcode, along with frameworks like React Native or Flutter.

 
# Recommendations

Operating Platform

I recommend that The Gaming Room host Draw It or Lose It on a Linux-based server platform, such as Ubuntu Server or Red Hat Enterprise Linux, in a cloud environment. Linux is a strong choice because it is stable, scalable, cost-effective, and widely used for web applications. It also works well with modern web servers, containers, and databases. Since the game needs to support users on multiple device types and operating systems, a Linux server can provide a centralized platform for the application backend while allowing clients to connect through standard web technologies. Linux also offers strong process isolation, user and group permissions, and flexible resource management features in the kernel. 
A Linux server platform is appropriate because Draw It or Lose It is essentially a multiplayer, web-based application. Instead of building separate server backends for each client operating system, the company can maintain one backend service and let users connect from Windows, macOS, Linux, Android, or iOS through a browser or lightweight client. This reduces maintenance complexity and improves portability.

Operating Systems Architectures

The recommended Linux server platform uses a multiuser, multitasking architecture with protected processes, virtual memory, and a hierarchical file system. Linux separates user space from kernel space, which improves system stability and security because applications cannot directly control hardware or other protected resources without going through the operating system. Linux also uses process scheduling and memory management features to support many simultaneous users and requests efficiently. The kernel documentation describes resource control through cgroups, which can partition and limit system resources for groups of processes. 
For this game, the architecture should follow a three-tier design:
4.	Presentation layer for the web or mobile client 
5.	Application layer for game logic, sessions, and scoring 
6.	Data layer for persistent storage such as users, teams, games, and image metadata 
This architecture supports scalability because each layer can be updated or expanded independently. A reverse proxy such as NGINX can sit in front of the application servers to manage HTTPS connections and distribute traffic across multiple instances. NGINX officially supports reverse proxying, load balancing, and caching, which makes it suitable for high-availability web applications. 

Storage Management

An appropriate storage solution for Draw It or Lose It is a combination of PostgreSQL for structured application data and object or file storage for image assets. PostgreSQL is a strong relational database choice because it is known for reliability, data integrity, access control, and replication support. These capabilities are useful for storing user accounts, game sessions, team records, scores, and audit data. PostgreSQL documentation highlights its support for roles, authentication, backup, restore, high availability, and replication. 
Because the game may need to manage around 200 large image files, storing all images directly in the database would be less efficient than keeping them in external storage and saving only their metadata and paths in PostgreSQL. A content delivery approach can also improve performance by placing image content closer to users geographically. This reduces latency and helps the game load drawing images faster for players across different regions. The storage system should also support backups, redundancy, and replication so that game data is not lost during failures. PostgreSQL’s write-ahead logging and replication features support this need. 

Memory Management

The Linux platform uses virtual memory, paging, and resource controls to manage RAM efficiently. Its /proc/sys/vm controls and memory-management subsystem allow the operating system to decide what should remain in physical memory and what can be moved or reclaimed. Linux also supports memory control groups, which can limit memory usage for specific workloads and help prevent one service from exhausting the entire server. 
For Draw It or Lose It, this matters because the game may involve roughly 1.6 GB of image data if 200 images at 8 MB each were loaded at once. The application should not load all images into memory at startup. Instead, it should use lazy loading, caching, and asynchronous loading. Only the current image and a small number of likely next images should be loaded into memory. Recently used images can remain in cache briefly to improve response time. This approach reduces lag, avoids unnecessary memory consumption, and keeps the application responsive even when many users are connected at the same time. NGINX can also buffer proxied responses and, when needed, spill excess data to temporary disk files instead of holding everything in memory. 

Distributed Systems and Networks

To support communication across multiple platforms, Draw It or Lose It should use a distributed client-server architecture. In this design, clients on different operating systems connect over the internet to centralized application services using standard network protocols such as HTTPS. The server manages authentication, game state, images, and persistence, while the client focuses on rendering the interface and sending player actions. This model allows the same backend to serve web browsers and other clients regardless of their local operating system.
The distributed system should include a reverse proxy/load balancer, one or more application server instances, and a database server. NGINX can distribute incoming traffic among multiple app servers, improving throughput and fault tolerance. PostgreSQL can provide reliable transactional storage, while replication and backups improve recovery options. 
There are important dependencies to consider:
•	Connectivity: Clients need reliable internet access to communicate with the backend. 
•	Latency: Slow network connections may delay image loading or player responses. 
•	Outages: If a server instance fails, load balancing and redundancy should reroute traffic to healthy instances. 
•	Database availability: If the database becomes unavailable, game progress and account functions may be interrupted. 
•	Session consistency: Users must remain authenticated and synchronized during gameplay. 
To reduce these risks, the system should use health checks, redundancy, retry logic, and monitoring. Static assets such as images should be cached when possible, while critical game data should be stored in a transactional database.

Security

Security should be built into both the server platform and the application design. Linux provides strong security foundations through user accounts, group permissions, protected credentials, and process isolation. The Linux kernel documentation explains that credentials such as user IDs and group IDs are tied to system objects and processes, helping enforce access control. 
To protect user information between platforms, all traffic should use HTTPS with TLS. OWASP states that full-session TLS is essential to protect credentials and session identifiers from interception. TLS also helps verify that clients are connected to the legitimate server. In addition, secure cookies, session expiration, unpredictable session identifiers, and strong authentication controls should be used. 
To protect user information on the platform, the system should implement:
•	Role-based access control so users and administrators only have the permissions they need 
•	Database authentication and roles to restrict access to stored data 
•	Encryption for sensitive data in transit and, where appropriate, at rest 
•	Regular patching and updates for Linux, NGINX, and PostgreSQL 
•	Backups and logging for recovery and auditing 
•	Input validation to reduce risks such as injection attacks 
PostgreSQL supports client authentication, roles, and secure administration, while Linux and NGINX support secure service separation and protected network access. Keeping supported software versions current is also important because PostgreSQL continues to publish security updates for supported releases. 

# Final Recommendation
Overall, The Gaming Room should deploy Draw It or Lose It on a Linux-based cloud server platform using a distributed web architecture. This recommendation best supports cross-platform access, scalability, cost efficiency, and strong security. Linux provides stable operating system architecture and effective memory management, PostgreSQL offers reliable storage for structured data, and a reverse proxy such as NGINX supports load balancing and secure connections. Together, these technologies provide a practical and flexible foundation for expanding the game across multiple computing environments.
