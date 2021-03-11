To design a tinyURL system, the first thing to think about is functionality. An interviewer would expect, 

A system that support the ability for a user to take a URL and convert it to a new URL that is “tiny”. Other 
functionality may include:
* Ability to receive analytics and tracking on the URL
* Ability to perform actions on Tiny URL’s that you have created such as viewing, updating, and deleting them. 

If you are to design such a system, a good place to start is the functional requirements so that we end up with a 
design that can meet the system level needs of throughput, persistence and latency required. 

We can assume that users will want, 
* Sub-second responses in creating their URL; Anything slower will lead them to a competitor or to not use our
 application in the future. 
* Reasonable level of persistence; One can imagine that a URL may be active for years. We can assume 5 years as a 
starting point, and configure this value differently as we learn users habits over time. 
* High level of throughput; We want our system to be able to support a high volume of users as we want our product to be
 successful and have a high level of adoption. 
* Extremely high availability for the re-direct. While users may be willing to retry in creating the URL (even that is a stretch assumption) they certainly will lose trust if they see that redirects fail as they do not have data or information on the number of successful redirects. We can also assume that the presence of that data may confuse users, as users will expect that the redirect just works as it is the core value of the URL. 

For the system, we will need to consider:
* Compute and Network resources
* Redundancy and Failover
* Persistence
* Change management
* Operational Intelligence

Thus, a good starting point is to calculate throughput as, 

Throughput = Number of events for a similar application over a period of time / units of time required to obtain events per second

So if Facebook posts happen 100M times over a day, 

Throughput = 100M a day / (24 # hours * 60 # minutes * 60 #seconds) = ~ 1200 post per second

Now we could better approximate our own throughput by searching for similar use cases and seeing the load, or if we have
 an existing platform we are integrating into we can use data from that platform to inform our anticipated throughput.
