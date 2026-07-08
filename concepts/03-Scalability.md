# Scalability

> ## The Problem
Imagine you've built an application similar to Uber.

Initially, only a few hundred people use it every day. A single server handles every request without any issues.

As your application becomes more popular, the number of users steadily increases.
- More people log in
- More API requests are sent
- More database queries are executed

At first, the increase is barely noticeable.

Eventually, however, users begin experiencing slower response times.

Pages take longer to load.

Requests begin timing out.

Some users can no longer access the application.

**The application hasn't changed; the number of users has**
---
> **Why does this happen?**
Every server has physical limits.

A machine only has a finite amount of:
- CPU
- Memory(RAM)
- Storage
- Network bandwidth
Every incoming request consumes some of these resources.

As more users arrive, the server must process more requests simultaneously.

Eventually, one or more resources become fully utilized.

When this happens:
- Requests wait in queues
- Response times increase
- Throughput stops increasing
- Users experience failures

The system has reached its capacity.
---
> ## The First Solution Most People Try
The simplest solution is to make the existing server more powerful.

Instead of replacing the architecture, upgrade the hardware.

```
Before

4 CPU Cores
8 GB RAM

↓

After

32 CPU Cores
128 GB RAM
```

The application becomes fast again, but for a while.

---
> ## The New Problem
Success brings more users.

Eventually, even the largest available server reaches its limits.

There's another issue.

If that single server fails, the entire application becomes unavailable.

```
        Users
           │
           ▼
     Powerful Server X

Application Offline
```

One machine has become a single point of failure.

---
> ## What is Scalability?
Scalability is the ability of a system to continue handling increasing users, requests, or data without significant degradation in performance.

A scalable system should continue functioning effectively as demand grows.
---

> ## Types of Scalability

### Vertical Scaling (Scaling Up)
Vertical scaling means increasing the resources of a single machine.

```
One Server

↓

More CPU
More RAM
More Storage
```

**Advantages**
- Simple to implement
- No architectural changes
- Minimal code changes

**Disadvantages**
- Hardware has physical limits
- Can become expensive
- Single point of failure
  ---
  ### Horizontal Scaling (Scaling out)
Horizontal scaling means adding more machines instead of making one machine larger.

```
             Users
                │
                ▼
         Load Balancer
          /    |    \
         /     |     \
   Server 1 Server 2 Server 3
```
Each server processes part of the workload.

**Advantages**
- Can support millions of users
- Better fault tolerance
- Easier to expand over time

**Disadvantages**
- More complex architecture
- Requires load balancing
- Data consistency becomes challenging
---
> ## Real-World Examples

 **Most modern internet companies rely heavily on horizontal scaling.**

- Uber scales its ride matching services across many servers to handle requests from cities around the world.
- Netflix distributes streaming requests across thousands of servers and multiple regions.
- WhatsApp processes billions of messages daily using horizontally scaled backend services.
- Amazon continuously adds servers to support increased shopping traffic, especially during events like Black Friday.
---

> ## Key Takeaways
- Every server has physical limits
- More users eventually require more computing resources.
- Upgrading one server is called vertical scaling.
- Adding more servers is called horizontal scaling.
- Modern distributed systems primarily rely on horizontal scaling because it provides better growth potential and fault tolerance.

> ## Summary
  A single computer cannot serve an unlimited number of users. As demand grows, systems must grow with it. Scalability is the discipline of designing software and infrastructure so that increasing demand does not result in unacceptable performance or availability.

  ## What's Next?
  Availability & Reliability
