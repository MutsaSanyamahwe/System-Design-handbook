# Availability vs Reliability

> ## Availability

Availability measures **whether a system is accessible and operational when users need it**.

A highly available system continues accepting requests even during failures.

**Example**

If Netflix is online and users can watch videos, the service is considered available.

### Formula

```text
Availability = (Uptime / Total Time) × 100%
```

Common availability targets:

| Availability | Downtime per Year |
|--------------|-------------------|
| 99% | ~3.65 days |
| 99.9% | ~8.8 hours |
| 99.99% | ~52.6 minutes |
| 99.999% ("Five Nines") | ~5.3 minutes |

---

> ## Reliability

Reliability measures **whether a system performs its intended function correctly and consistently over time**.

A reliable system produces correct results without failures or data loss.

**Example**

If WhatsApp successfully delivers every message without duplication or loss, it is reliable.

---

## The Difference

A system can be available but not reliable.

**Example**

An e-commerce website is online, and users can place orders, but payments randomly fail.

-  High Availability
-  Low Reliability

---

A system can also be reliable but not available.

**Example**

A banking system is taken offline for maintenance. Once it's back online, every transaction is processed correctly.

-  Low Availability
-  High Reliability

---

## Comparison

| Availability | Reliability |
|--------------|-------------|
| Is the system accessible? | Does the system work correctly? |
| Focuses on uptime | Focuses on correctness and consistency |
| Measured by uptime percentage | Measured by failure rate and successful operations |
| Minimized by reducing downtime | Minimized by reducing failures and errors |

---

## How They're Achieved

### Improve Availability

- Redundant servers
- Load balancers
- Failover mechanisms
- Replication
- Multiple data centers

### Improve Reliability

- Data replication
- Backups
- Error handling
- Thorough testing
- Monitoring and automatic recovery

---

## Key Takeaways

- **Availability** answers: *"Can users access the system?"*
- **Reliability** answers: *"Will the system work correctly every time?"*
- A highly available system isn't necessarily reliable.
- A highly reliable system isn't necessarily available.
- Great distributed systems strive to achieve both.
