#Latency and Throughput

> ## 1. The Problem
Imagine Uber has just announced a 50% discount on all rides.

Millions of users open the app at the same time to request rides.

The servers are now receiving an enormous number of requests.

Two important questions arise:
- How quickly can the system respond to each request?
- How many requests can the system handle every second?

A system that responds very quickly but can only serve a handful of users isn't practical.

As systems grow, engineers need to measure both speed and capacity.

This leads us to two of the most important performance metrics in system design:
- Latency 
- Throughput
---
> ## 2. The Solution
Latency and throughput  measure two different aspects of system performance.
- Latency measures how long a single operation takes.
- Throughput measures how much work the system can complete over a period of time.

**They each answer this question**
- Latency:    How fast is one request?
- Throughput:  How many requests can we process?

Both metrics are equally important.

A high-performance system aims for:
- Low latency
- High throughput

---

> ## 3. How It Works

### What is Latency?
Latency is the time taken for a request to travel through the entire system and receive a response.

It starts when the client sends a request and ends when the client receives the response.

Latency is usually measured in:
- milliseconds(ms)
- microseconds for extremely fast systems

  Example
  Suppose your phone requests your Uber trip history:

  ```
  Request sent      0 ms
  Server receives   20 ms
  Database query    50 ms
  Server responds   80 ms
  Phone receives   120 ms
  ```

  The latency is:

  ```
  120 milliseconds
  ```
  The user only cares about the total waiting time.

  They don't care which component caused the delay.

  Latency is rarely caused by one thing.

  Instead, it is the sum of many small delays.

  ```
  Total Latency =
  Network Time
  + Server Processing
  + Database Queries
  + Cache Lookups
  + External API Calls
  + Response Transmission
  ```
For example:
```
- Internal travel takes 35ms
- Authentication 5ms
- Database query takes 25ms
- Business logic takes 15ms
- Sending response takes 20ms
```

Total latency:
```
100ms
```
Optimizing a system often means reducing one or more of these components.

---
### What is throughput?
Throughput means how much work a system completes within a specific amount of time.

Examples include:
- requests per second (RPS)
- transactions per second (TPS)
- messages processed per second
- videos streamed per minute
  
Unlike latency, throughput isn't about a single request.

It's about the entire system's capacity

Example
Suppose an API processes:

```
10,000 requests
```
in
```
1 second
```
Its throughput is:
```
10,000 requests/second
```

--- 
> ## Why improving one doesn't always improve the other
Consider two systems.

**System A**
- Processes one request in 10ms
- Can only process one request at a time

Latency is excellent.
Throughput is poor.

**System B**
- Processes 50,000 requests simultaneously
- Average response time is 150ms
Latency is higher
Throughput is much greater.

In real-world systems, engineers balance these two metrics depending on the application's requirements.
---
> ## 4. Real-World Example

### Netflix

When you press Play, you expect the video to start almost immediately.

This is a latency problem.

Once the movie starts, Netflix must continuously deliver video data without interruption.

Serving millions of viewers around the world at the same time is a throughput challenge.

A successful streaming platform therefore requires:

- low startup latency
- extremely high throughput across its infrastructure
---
> ## 5. Advantanges & Trade-offs
There is often a trade-off between latency and throughput

### Optimizing for Low Latency

**Advantages**
- Faster user experience
- More responsive applications
- Better customer satisfaction
- Essential for real-time systems like gaming, ride-sharing, and video calls

**Trade-offs**
- May require more servers
- Can increase infrastructure costs
- Some optimizations can only benefit small numbers of users

### Optimizing for High Throughput

**Advantages**
- Supports many users simultaneously
- Makes better use of hardware
- Reduces cost per request
- Essential for large-scale applications

**Trade-offs**
- Individual requests may take longer
- System becomes more complex
- Heavy workloads can increase response times

---
> ## The Goal
**An ideal production system achieves low latency and high throughput.**

Achieving both requires techniques such as:
- caching
- load balancing
- horizontal scaling
- content delivery networks (CDNs)
- asynchronous processing
These are all concepts we'll explore later in this repository.

---
> ## 6. Questions

**What is latency?**

```
Latency is the total time taken for a request to travel through a system and return a response to the client.
```

**What is throughput?**

```
Throughput is the amount of work a system completes within a given period, such as requests per second.
```

**Can a system have low latency but low throughput?**
```
Yes.

A system might respond very quickly to individual requests but only handle a small number of requests simultaneously.
```

**Can a system have high throughput but high latency?**
```
Yes.

A system may process thousands of requests every second while each individual request still takes longer to complete due to heavy load or batching.
```

**Which is more important: latency or throughput?**
```
Neither is universally more important.

It depends on the application:

Real-time systems prioritize low latency.
Large-scale data processing systems often prioritize high throughput.
Most modern internet applications aim to optimize both.
```
**How can latency be reduced?**
```
Common techniques include:

Caching frequently accessed data
Using CDNs for static content
Optimizing database queries
Reducing network hops
Improving server-side algorithms
```

**How can throughput be increased?**

```
Common techniques include:

Horizontal scaling
Load balancing
Asynchronous processing
Efficient database design
Queue-based architectures
```

---
> ## Key Takeaways
- Latency measures how long one request takes from start to finish.
- Throughput measures how much work a system completes over time.
- Low latency improves responsiveness.
- High throughput improves capacity.
- Improving one metric does not automatically improve the other.
- High-performance systems strive for low latency and high throughput, using techniques such as caching, scaling, and load balancing.
  
