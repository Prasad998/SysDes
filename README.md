# SysDes

**My own System Design Resources**

> 80% of the System Design interviews I’ve given in the last 7 years…  
> …have revolved around just 20% of the most repeated, practical problems.

If you’re preparing for FAANG+ interviews or just trying to learn System Design the right way, this is the **MUST-SOLVE LIST**.

I've categorized them based on themes, with key notes on what each problem is really testing.

---

## 📚 Read-Heavy Systems  
*These focus on scale, latency, and efficient data fetching.*

1. **Design a URL Shortener (Bitly)**  
   → Key generation, collision handling, DB storage  
   → Caching and DB sharding for high traffic

2. **Design an Image Hosting Service**  
   → Object storage (S3, GCS), CDN usage  
   → Image deduplication and resizing strategies

3. **Design a Social Media Platform (Twitter/Facebook)**  
   → Posts, timelines, relationships (follows/friends)  
   → Denormalized storage, horizontal scaling

4. **Design a NewsFeed System (Hard)**  
   → Push vs Pull models, Fanout on Write vs Read  
   → Caching, pagination, ranking algorithms

---

## ✍️ Write-Heavy Systems  
*Durability, throughput, and ingestion speed are key here.*

5. **Design a Rate Limiter**  
   → Token bucket or leaky bucket algorithms  
   → Redis counters with TTL

6. **Design a Log Collection and Analysis System**  
   → Kafka ingestion, ELK for processing  
   → Partitioning, buffering, real-time querying

7. **Design a Voting System**  
   → Idempotency, fraud prevention, result aggregation  
   → Real-time vs eventual updates

8. **Design a Trending Topics System**  
   → Count-min sketch, approximate counting  
   → Sliding window aggregation, ranking

---

## 🔒 Strong Consistency Systems  
*Transactional integrity and failure handling matter most.*

9. **Design an Online Ticket Booking System**  
   → Race conditions, locking, optimistic concurrency  
   → Seat reservation, payment orchestration

10. **Design an E-Commerce Website (Amazon)**  
    → Product catalog, cart, order pipeline  
    → DB consistency, checkout idempotency

11. **Design an Online Messaging App (WhatsApp/Slack)**  
    → Message queues, delivery receipts, retries  
    → Offline storage, notification systems, scaling

12. **Design a Task Management Tool**  
    → CRUD APIs, user auth, task assignment  
    → Background jobs, status updates, audit trail

---

## ⏲️ Scheduler Services  
*Focus on timing, reliability, and execution guarantees.*

13. **Design a Web Crawler**  
    → BFS vs DFS, politeness rules  
    → Distributed queues, duplicate URL filtering

14. **Design a Task Scheduler**  
    → Job queues, retry logic, cron triggers  
    → Priority queues, deduplication

15. **Design a Real-Time Notification System**  
    → Push vs Polling, webhooks, token management  
    → Scalable delivery to millions of devices

---

## 📡 Trie / Proximity-Based Systems  
*Efficient data structures + low latency retrieval strategies.*

16. **Design a Search Autocomplete System**  
    → Trie or Ternary Tree, ranked by frequency  
    → Debouncing, typo-tolerance, caching

17. **Design a Ride-Sharing App (Uber/Lyft)**  
    → Matchmaking engine, real-time tracking  
    → ETA algorithms, surge pricing, DB schema

---

📌 *Like this list? Feel free to fork and build your own mental map for systems!*  

🧠 *Remember: depth > breadth. Focus on tradeoffs, constraints, and real-world scalability.*

---
