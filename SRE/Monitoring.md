## Monitoring

- Insight into a system, 
- Tracking the health,availability
- what is happening internally in the system


- We need to figure out: 
    - **what** to monitor: what data to collect
    - **how** to monitor it: how to collect that data
    - **where** to store the monitoring data: how to store that data
    - **who** can access historical monitoring data: how to display that data for developers and for those who will find it useful. 
    - **how** to look at data
    

- Observe and check the progress or quality over a period
- Keep under systematic review.
- you need define what quality is

### How to Monitor

- Two separate types of monitoring that software needs: 
    - **metrics**: number measurements, anything that can be measured as a numerical value
    - **logs**: events, which have numbers and other data attached, but are often less structured. Some logs are complete JSON blobs of data, while others are just human-formatted strings of text. 
    
- Example for a web application: 
    - metrics can be: (REL)
        - request counts (**R**equests)
        - error counts (**E**rrors)
        - request duration (**L**atency)
    - logs:
        - error stack trace
    
- We can increment a counter everytime an error occurs and write that error details into an error log, with timestamp
- You can increment the counter to find out how many requests you serve result into errors and can quickly view long-term error progress. 
- Request duration: duration recording the time it took to respond as well as the URL hit (GET/POST/HEAD) and status code returned.

### Why Monitoring is Important

- how do you know a service is working?
- how do you know a service is not working?
- How do you define what does it mean that the service is working?
- Monitoring is important because it provides us the data-driven view of our application and proves to us it is working. 


- StatsD: monitoring system by Etsy. Push based system.
- Two monitoring function calls: 
    - increment: the number of requests received, number of times a user performs an action
    - time: how long it takes to talk to a dependency
- Prometheus: monitoring system by SoundCloud. Pull based system

- Event-driven monitoring: Log information by writing to plain text files, or JSON objects written to  std output, or to database. 

What should we monitor

- monitor everything vs wait and see approach. 
- wait for an event to happen and during postmorterm, the team wished they had a piece of data, then it should be instrumented, monitored and stored. 
- To start with monitoring for new apps, start by error counts, request counts and request durations. 
- If the service has batch processing, data pipeline, or cron job - then monitor job invocations, job durations, and job successes.
- Goal: validate that the service is doing what is expected
- Start by recording business logic like how many records in the database, metrics around connecting to our dependencies, how many types of actions are happening. 
- then focus on capacity, which is a recording of the resources the servers are using - metrics such as hard drive storage, network bandwidth, CPU and memory

