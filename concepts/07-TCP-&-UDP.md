# TCP & UDP

## The Problem

You've learned that HTTP allows a browser and a server to communicate.

But another question arises.
> How is the data actually transported across the network?

Imagine you're downloading a file.

The file is too large to send all at once, so it is divided into many smaller pieces called packets.

Those packets travel across the Internet, passing through many routers before reaching their destination.

Unfortunately, several things can happen along the way:

- Packets may be lost.
- Packets may arrive out of order.
- Packets may be duplicated.
- Network congestion may slow transmission.

The receiving computer needs a way to know:

- Did every packet arrive?
- Did they arrive in the correct order?
- Should missing packets be resent?
Different applications require different answers to these questions.

For example:
- Online banking cannot afford to lose transaction data.
- A video call can tolerate losing a few packets if it keeps the conversation smooth.

One communication method couldn't effectively satisfy both needs.

This led to two transport protocols:
- TCP (Transmission Control Protocol)
- UDP (User Datagram Protocol)

---

## What is TCP?
TCP is a connection-oriented transport protocol that prioritizes reliability.

Before sending data, TCP establishes a connection between the sender and receiver.

It ensures that:

- Packets arrive successfully.
- Packets arrive in the correct order.
- Lost packets are retransmitted.
- Duplicate packets are discarded.

TCP guarantees reliable communication.

---

### How TCP Works

Before any data is exchanged, TCP performs a three-way handshake to establish a connection.

```
Client                 Server

  SYN  ------------->

       <------------- SYN-ACK

  ACK  ------------->

Connection Established
```

Once connected, data is transmitted reliably.

If a packet is lost, TCP automatically retransmits it.

---

## What is UDP?
UDP is a connectionless transport protocol that prioritizes speed.

Instead of establishing a connection, UDP sends packets immediately.

There is:

- No handshake
- No packet ordering
- No retransmissions
- No delivery guarantee

UDP sends the data and moves on.

---

### Why would anyone use UDP?

Because reliability isn't always the most important goal.

Sometimes speed matters more.

Imagine a live football match.

If one video packet is lost, would you rather:
- Wait for the missing packet and freeze the video?

or
- Skip that packet and continue playing smoothly?

Most users prefer uninterrupted playback.

For real-time communication, it's often better to lose a few packets than introduce delays.

---

## TCP vs UDP

| TCP                      | UDP                    |
| ------------------------ | ---------------------- |
| Connection-oriented      | Connectionless         |
| Reliable delivery        | Best-effort delivery   |
| Guarantees packet order  | No ordering guarantees |
| Retransmits lost packets | Does not retransmit    |
| Higher latency           | Lower latency          |
| Slower                   | Faster                 |

---

## Real-World Examples
**TCP**

Applications that require accurate and complete data.

Examples include:

- HTTP / HTTPS
- Web browsing
- Email
- File downloads
- Banking applications
- Database communication

---

**UDP**

Applications that prioritize speed and real-time communication.

Examples include:

- Video conferencing
- Voice calls
- Online gaming
- Live streaming
- DNS lookups

---

Key Takeaways
- TCP and UDP are transport-layer protocols responsible for moving data across networks.
- TCP prioritizes reliability by guaranteeing packet delivery, ordering, and retransmission.
- UDP prioritizes speed by sending packets without establishing a connection or guaranteeing delivery.
- Choose TCP when correctness is critical.
- Choose UDP when low latency is more important than perfect reliability.

