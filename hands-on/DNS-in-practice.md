# DNS in Practice

## The Goal
You've built an application and deployed it to the cloud.

Instead of users accessing your application through an IP address or a provider-specific URL, you want them to access it using a custom domain.

For example, instead of:

```
https://your-app.onrender.com
```

or 
```
http://54.221.34.89
```
you want users to visit:
```
https://your-app.com
```

DNS makes this possible.
---
# Step 1: Deploy Your Application
Before configuring DNS, your application must already be running somewhere.

Examples include:
- AWS EC2
- Azure Virtual Machine
- Google Cloud VM
- Render
- Railway
- Fly.io
- DigitalOcean

After deployment, your provider gives you either

An IP address

```
54.221.34.89
```
or a provider-managed domain

```
your-app.onrender.com
```
At this point, your application is already accessible.
---

# Step 2: Register a Domain
Purchase or register a domain from a domain registrar.

Examples include:
- Cloudflare
- GoDaddy
- Namecheap

Example domain:
```
pawpal.com
```

Owning a domain does **not** automatically connect it to your application.

You must configure DNS records.
---

# Step 3: Configure DNS Records

DNS records tell the internet where your application lives.

The two records you'll use mostly are:

## A record
Maps a domain directly to an IPv4 address

Example
| Type | Name | Value |
|------|------|-------|
| A | @ | 54.221.34.89 |

This means:

```
pawpal.com

↓

54.221.34.89
```

## CNAME Record

Maps one domain name to another domain name

Example

| Type | Name | Value |
|------|------|-------|
| CNAME | www | pawpal.onrender.com |

Instead of pointing directly to an IP address, the DNS server follows the provider's domain until it reaches the correct IP.
---

# Step 4: DNS Propagation

After changing DNS records, the update is not immediate.

DNS servers around the world cache records to improve performance.

As those cached records expire, they request the updated information.

This process is known as **DNS propagation**.

Propagation may take anywhere from a few minutes to several hours, depending on the record's TTL.
---

# Step 5: HTTPS
Once DNS is correctly configured, the next step is securing your website.

Most hosting providers automatically issue an SSL/TLS certificate using Let's  Encrypt.

Your users can now securely access:

```
https://pawpal.com
```

instead of 

```
http://pawpal.com
```
---
# Production architecture
In production, DNS rarely points directly to an application server.

Instead, it usually points to a Load Balancer.

```

                 User
                   │
                   ▼
          pawpal.com
                   │
                   ▼
            DNS Provider
                   │
                   ▼
           Load Balancer
             │       │
        ┌────┘       └────┐
        ▼                 ▼
    Server 1         Server 2
        │                 │
        └────────┬────────┘
                 ▼
             Database

```

This architecture provides:
- High availability
- Scalability
- Fault tolerance
---

# Common DNS Records
| Record | Purpose |
|---------|---------|
| A | Maps a domain to an IPv4 address |
| AAAA | Maps a domain to an IPv6 address |
| CNAME | Maps one domain to another domain |
| MX | Specifies mail servers for email |
| TXT | Stores verification and security information |
---

# Key Takeaways
- Deploying an application gives you an IP address or provider-managed domain.
- DNS records connect your custom domain to your deployed application.
- **A Records** point to IP addresses.
- **CNAME Records** point to other domain names.
- DNS changes require propagation because records are cached around the internet.
- In production systems, DNS usually points to a Load Balancer instead of directly to an application server.
