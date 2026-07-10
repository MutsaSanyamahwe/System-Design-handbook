# HTTPS in Practice

## The Goal

You've built a web application.

How does it actually become accessible over HTTPS?

Let's follow a request from your browser to your backend.

---

## Local Development

```
React

↓

http://localhost:5173

↓

http://localhost:3000
```

During development, most applications use HTTP.

Why?
- Simpler setup
- Local machine is trusted
- No SSL certificate required

---

## Production Deployment

After deploying:

```
https://pawpal.com

↓

React Frontend

↓

https://api.pawpal.com

↓

Express Backend
```
Now every request leaving the user's browser is encrypted.

---

## Does Express Provide HTTPS?

No.

Express creates an HTTP server.

```
app.listen(3000);
```

By itself, this serves HTTP.

HTTPS is usually added by another component.

---

## Where HTTPS Usually Comes From

In production, the HTTPS is often provided by:

- NGINX
- Cloudflare
- AWS Application Load Balancer
- Vercel
- Render
- Railway
- Azure Front Door
- Google Cloud Load Balancer

```
Browser

↓

HTTPS

↓

NGINX
Cloudflare
AWS ALB
Render
Vercel

↓

HTTP

↓

Express
```
This process is called TSL/SSL Termination.

The reverse proxy decrypts incoming HTTPS requests and forwards them to the backend application.

---

##  Can Express Use HTTPS?

Yes.

Express can create an HTTPS server by loading an SSL certificate.

https.createServer(...)

However, this is uncommon in production because reverse proxies are better suited to handling encryption.

---

## Why Use a Reverse Proxy?

Instead of every application managing certificates, encryption, and renewals individually, the reverse proxy handles these responsibilities.

Benefits include:

- Automatic certificate management
- Better performance
- Centralized security
- Easier scaling

---

## Real-World Example

Production architecture oftwn looks like this:

```
Browser

↓

HTTPS

↓

Cloudflare

↓

AWS Load Balancer

↓

NGINX

↓

Express API

↓

Database
```

Notice that Express never communicates directly with the browser.

The browser only sees an encrypted HTTPS connection.

---

## Key Takeaways
- Local development usually uses HTTP.
- Production applications almost always use HTTPS.
- Express creates an HTTP server by default.
- HTTPS is commonly provided by a reverse proxy, load balancer, or hosting platform.
- This process is known as TLS (SSL) termination.
