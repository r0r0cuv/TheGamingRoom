# TheGamingRoom
The Gaming Room Operating Systems and designs 

Project Report
Client & Software Requirements

The client for this project is The Gaming Room, which currently has an Android version of Draw It or Lose It and wanted a web-based, cross-platform version of the game created. Some key system requirements included supporting multiple teams with players, unique game/team names as well as player names, and using a distributed application architecture that could support mutliple users while only having one instance of the game service running(using design patterns).

What Did I Do Well

I think I did well with coming up with the system analysis and picking the technologies to use. I was able to clearly communicate why a Linux server would be optimal as well as what types of architecture(distibuted) and database(postgresql) would suit their needs. I applied design patterns such as Singleton and Iterator to help facilitate some of these requirements.

What Was Helpful To You in the Design Process

I found it helpful working through the design document before writing any code. It helped me layout my ideas on how I wanted the application to be structured, how I wanted pieces to interact with each other, and catch some problems before they happened(i.e. memory,scaling). During development this then helped me not be as confused when writing my code.

What Would you Improve

If I could redo one thing for this project it would be the initial system architecture picture and description. I would make it more in-depth and visually easier to understand how all of the different parts of the distributed system talk to each other.

How did you determine the users’ needs?

I determined the users need by using concepts such as performance, scalability, and usability. An example of this would be me using ideas such as lazy loading, caching results to improve performance and decrease lag time while playing games. Understanding the users needs is important to factor into your software because you want to make sure the software is usable, runs well, and doesn't have any lag.

How did you go about Designing your software?

I approached designing my software by first doing a requirement analysis, picking out architectures, and design patterns to suit those requirements. In the future I would take a similar approach and use things such as OOP when designing my application, making sure to modularize my architecture, and planning for how my software will scale later on. I would also do more flwo charts and maybe use a prototyping software.
