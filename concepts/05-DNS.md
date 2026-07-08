#  DNS (Domain Name System)

> ## The Problem
Imagine every website on the internet was identified only by its IP address.

Instead of visiting:

```
google.com
```
you would have to remember:

```
142.250.190.78
```

Now imagine trying to remember hundreds of IP addresses. It would be nearly impossible.

There's another, even bigger problem.

Suppose Google decides to move its website to a different server.

The IP changes from

```
142.250.190.78
```
to
```
34.149.120.1
```
If everyone had memorized the old IP address, Google would instantly become unreachable.

So engineers needed a system where:
- Humans could use easy-to-remember names
- Computers could still communicate using IP addresses
- Websites could change servers without users noticing.

  That problem led to DNS.
  ---

  > ## What is DNS?
  DNS is the internet's phonebook.

  It translates human-readable domain names into IP addresses that computers use to communicate.

  Example:
  ```
  google.com

  ↓

  142.250.xxx.xxx
  ```

  Without DNS, browsers wouldn't know where to send your request.
  ---

  > ## How DNS Works
  Suppose you type into your browser:
  ```
  www.netflix.com
  ```

  The browser first asks:
  > Do I already know this IP address?

**Step 1: Browser Cache**
If the browser has recently visited Netflix, it may already have the IP address stored.

If found:
```
Use cached IP
```
If not... (DNS lookup Step 1)

---
**Step 2: Operating System Cache**
Your operating system also keeps recently used DNS records.
If it finds the IP:
```
Return IP to browser
```
Otherwise... (Step 3)
---

**Step 3: Recursive DNS Resolver**
The request is sent to a DNS resolver, usually operated by:
- Your ISP
- Google DNS (8.8.8.8)
- Cloudfare DNS (1.1.1.1)
The resolver's job is to find the correct IP address for you.

If it already has the answer cached, it returns it immediately.

Otherwise, it starts asking the DNS servers. (Step 4)
---
**Step 4: Root DNS Server **
The resolver asks a Root Server:
> Where can I find information about `.com`?
The Root server doesn't know Netflix's IP.

Instead, it replies:

> Ask the `.com` TLD servers (see next step).
---
**Step 5: Top-Level Domain(TLD) Server**
The resolver asks the `.com` server:

> "Where can I find `netflix.com`?
The TLD server replies:
> "Ask Netflix's authoritative name server."
---
**Step 6: Authoritative Name Server**
> The resolver asks for the IP address of `www.netflix.com`.
This server owns the DNS records for Netflix.
It returns the correct IP address
---
**Step 7: Browser Connects**
The resolver sends the IP back to your browser.
Now your browser can finally connect to Netflix's server and begin downloading the website.
---
> ## Why is DNS Hierarchical?
Imagine one giant DNS server for the entire internet.

Every request for every website would go to one machine.

Problems:
- Massive bottleneck
- Single point of failure
- Impossible to maintain
- Would never scale
Instead, DNS distributes responsibility

```
Root

↓

TLD (.com, .org, .net)

↓

Authoritative Servers

↓

Website
```
> ## DNS Caching
Notice that DNS lookups involve several servers.

Doing that for every request would make browsing slow.
Instead, DNS responses are cached.

For example:
```
google.com

↓

142.250.xxx.xxx
```

This mapping is stored temporarily.

The next request can skip the entire lookup process.
---
## TTL (Time To Live)

Every DNS record includes a TTL.

Example:

```
TTL = 3600 seconds
```
This means:
> The record can be cached for one hour.
After TTL expires, the resolver performs another lookup to check whether the IP address has changed.

TTL balances:
- Faster lookups (long TTL)
- Faster updates when server changes (short TTL)
---
## Why DNS Matters in System Design
DNS is the first step in almost every web request.

Before a browser can contact:
- a load balancer
- a reverse proxy
- an API Gateway
- or your application server
it first needs to know where the server is.

Without DNS, users couldn't simply type `amazon.com` or `uber.com`; they'd need to know and manage IP addresses themselves.



---
## Key takeaways
- DNS solves the problem of translating human-friendly domain names into machine-readable IP addresses.
- It uses a hierarchical structure (Root -> TLD -> Authoritative) to scale to the entire internet.
- Caching makes DNS fast by avoiding repeated lookups.
- TTL controls how long a DNS record can remain cached before it must be refreshed.
- DNS is usually the first network service involved whenever a user visits a website.






