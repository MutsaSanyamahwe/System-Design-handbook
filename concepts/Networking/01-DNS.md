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
> Where can I find information about .com?
The Root server doesn't know Netflix's IP.

Instead, it replies:

> Ask the .com TLD serves.




