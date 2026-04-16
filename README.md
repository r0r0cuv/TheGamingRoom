# TheGamingRoom
The Gaming Room Operating Systems and designs 

🎮 Draw It or Lose It – Software Design Project
📌 Overview

This project is a software design document created for The Gaming Room, a company looking to expand their Android game Draw It or Lose It into a web-based, cross-platform application.

The goal of this project is to design a scalable, secure, and efficient system that supports multiple users, teams, and platforms using modern software architecture principles.

🚀 Key Features
Supports multiple teams and players
Ensures unique names for games, teams, and players
Implements Singleton pattern for game service control
Uses Iterator pattern for searching collections
Designed for cross-platform compatibility
Built for a distributed web-based environment
🏗️ System Architecture
🔹 Three-Tier Architecture
Presentation Layer – Web/mobile client interface
Application Layer – Game logic, sessions, scoring
Data Layer – Database and storage management
🔹 Technologies Recommended
Operating System: Linux (Ubuntu / Red Hat)
Web Server: NGINX
Database: PostgreSQL
Cloud Support: Scalable cloud-based infrastructure

💾 Memory Management

To ensure performance and responsiveness:

Uses lazy loading to load images only when needed
Implements caching for recently used images
Supports asynchronous loading to prevent lag
Utilizes Linux memory controls (/proc/sys/vm)

👉 This prevents loading all ~1.6GB of image data at once and improves efficiency.

🗄️ Storage Management
Stores structured data using PostgreSQL
Stores images separately using file/object storage
Uses Content Delivery Networks (CDN) for faster access
Supports backup and replication for reliability
🌐 Distributed Systems & Networking
Uses a client-server architecture
Supports communication across:
Windows
macOS
Linux
Mobile devices
Key Considerations:
Network latency
System outages
Load balancing
Data consistency
🔐 Security Features
HTTPS with TLS encryption
Role-Based Access Control (RBAC)
Secure authentication and session handling
Data protection (in transit and at rest)
Regular updates and patching
🧩 Design Patterns Used
Singleton Pattern – Ensures only one GameService instance
Iterator Pattern – Efficient searching and validation
Object-Oriented Design – Inheritance and encapsulation
📊 Evaluation Summary
Platform	Strength
Linux	Best for servers (scalable, secure, cost-effective)
Windows	User-friendly, widely used
Mac	Stable but expensive
Mobile	Best for clients, not servers
✅ Final Recommendation

The system should be deployed using a Linux-based cloud server with a distributed architecture. This approach provides:

Scalability
Cross-platform support
High performance
Strong security
👩‍💻 Author

Rosalie Reblora
Bachelor of Science in Computer Science


📚 Project Type

📘 Academic Project – SNHU CS 230
Software Design & Architecture

💡 Reflection

This project strengthened my understanding of system architecture, memory and storage management, and distributed systems. It also helped me apply real-world design decisions for building scalable and secure applications.
