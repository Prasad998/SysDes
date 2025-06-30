# 🚀 Atlassian Interview Experience (P40)

**💰 Compensation:** ₹80 LPA  
**🧩 Position:** P40  
**🎯 Goal:** Help others prepare efficiently 🙌

---

## ✅ Round 1: Karat (3rd-party Screening)
⏱ **Duration:** 60 mins  
**Format:**
- **20 mins – System Design:** 5 rapid Qs (design patterns, architecture basics)
- **20 mins – DSA:** 2 coding questions
- **20 mins – MCQs:** Core CS (OOP, DBMS, OS, Networks)

✅ Passing this unlocks internal Atlassian rounds.

---

## ✅ Round 2: DSA Round
**Problem:** YouTube-like Like/Dislike system  
**Key Concepts:**  
- Use of **HashMap**, **HashSet**  
- Discussed **time/space complexity**, edge cases  
- Emphasis on clean, scalable logic

---

## ✅ Round 3: Low-Level Design (LLD)
**Task:** Implement a **Rate Limiter from scratch**  
**Post-task discussion:**  
- Variants: **Fixed Window**, **Sliding Log**, **Token Bucket**, etc.  
- Talked about **optimizations**, **thread safety**, **real-time usage**

---

## ✅ Round 4: High-Level Design (HLD)
**Task:** Design a simplified **Jira-like system**  
**Expectations:**
- **Full system architecture**  
- **Scalability choices**  
- Focus on **clarity, tradeoffs**, and **real-time decisions**

---

## ✅ Round 5: Managerial Round
🔹 **Surprisingly technical!**  
- Extended HLD discussion (real Atlassian use case)  
- Talked about **team structure, timelines, execution**  
📌 *Don’t underestimate this round!*

---

## ✅ Round 6: Leadership Principles
🎯 **Focus:** Atlassian’s core values  
- "Tell me a time when…" stories  
- Highlighted **real outcomes**, **ownership**, and **collaboration**

---

## 📝 Tip:
Prepare **real stories**, brush up **system design**, and have clarity on **DSA fundamentals**.  
This interview **blends tech depth with behavioral maturity**.
---
If I lost everything today and had to start from scratch to get back into Microsoft as a software engineer, here’s exactly what I’d do on system design prep,. based on what I know now:

I’m currently a Senior Software Engineer at Microsoft (7+ years). I get a LOT of questions about system design interviews, so here’s my full approach. 

1. Understand What System Design Interviews Really Test

- It’s not about fancy boxes and buzzwords.
- You’ll be asked to design a real system (e.g., Uber, Dropbox) on a whiteboard
- The goal: Can you break a big problem into working parts and explain your decisions?

2. Brush Up Your Fundamentals

- Don’t skip this step. Even seniors forget basic concepts.

- Know the differences and use cases for:
 - Relational DBs (SQL)
 - NoSQL/Document Stores (MongoDB, DynamoDB)
 - Key-Value Stores (Redis)

- Learn ACID vs BASE. Understand when each makes sense.
- Scalability basics: What’s vertical scaling? What’s horizontal? What’s sharding/partitioning?

- Networking: You only need to know Application, Transport, and Network layers. (APIs, REST vs gRPC, TCP vs UDP, basic load balancing.)

- Latency and performance: Have rough numbers in your head (memory vs disk vs network speeds). Learn to spot and fix bottlenecks.
- Fault tolerance: Know how redundancy and replication work.

- CAP theorem: Every interviewer expects you to mention consistency, availability, and partition tolerance, and pick the right one for the use case.

3. Pick a Simple, Repeatable Framework for Interviews

- Always start with requirements, 
- functional (features) and non-functional (scale, latency, consistency, etc).
- List core entities/tables (users, events, orders, etc).
- Map out basic APIs/endpoints needed.
- Draw a simple, high-level design: what’s needed for V1 to work at all.
- Dive deeper only when the interviewer asks, optimize for scale, speed, or whatever NFR matters most.


4. Focus Your Practice on Common Patterns, Not Random Problems

- Don’t get lost in huge lists online.
- Instead, focus on core, repeating problems:
 1. URL Shortener (Bitly)
 2. File Storage (Dropbox)
 3. Ticket Booking (Ticketmaster)
 4. News Feed
 5. Chat System
 6. Rate Limiter
 7. Message Queue
 8. Search Autocomplete
 9. Video Streaming
 10. Post Search

- Work through these one at a time until you can explain every part, storage, traffic, failure, scaling.

5. When Practicing, Use This Cycle

- First, try the problem on your own, sketch it on a whiteboard or notebook.
- Don’t check solutions right away. Get stuck. Find out what you don’t know.
- THEN, look up a detailed solution or watch a video to fill the gaps.

- Make notes: What patterns, what components, what trade-offs?
- Repeat with the next problem.
 (This “struggle first” approach is 10x better than passive reading.)


6. Communicate Clearly

- Interviewers don’t care just about your diagram.
- They want to hear your reasoning, why did you pick X, why not Y?
- Practice explaining every choice as if teaching a beginner.
- Bonus: Do at least one peer/mock interview for real feedback.


7. During the Actual Interview

- Don’t rush to draw. Spend the first few minutes confirming requirements and priorities with your interviewer.
- Think in “milestones”, start with a simple version, then add scale, performance, or reliability.
- If you don’t know something, say so, and show how you’d learn or validate in real life.
- Always mention trade-offs: No system is perfect; every design has costs.
---

# 🚀 Google SWE III - Machine Learning Interview Experience

I recently got the incredible opportunity to interview with **Google** for the **Software Engineer III – Machine Learning** position. This turned out to be one of the **best interview experiences** I've had so far!

---

## 📩 How It Started

Despite applying to several roles on Google’s careers page with no response, I was eventually contacted **out of the blue** by a Google recruiter via **LinkedIn and email**.  
She asked for my resume, and after a quick review, invited me to schedule a **📞 phone screening**.

---

## ☎️ Phone Screening

In this initial conversation, I shared:
- My background & work experience
- Proficiency in **Data Structures & Algorithms**
- Experience in **Machine Learning** and **Deep Learning**

The recruiter was kind enough to give me **a month to prepare**. I filled out a form to confirm availability for further rounds.

---

## 🧩 Interview Rounds Overview

- **3 Coding Rounds** – Focused on DSA
- **1 ML Round** – Theoretical + practical
- **1 Googliness/Behavioral Round**

---

## 🧠 Preparation & Warm-ups

### ✅ Group Preparation Session (1 Hour)
- Discussed interview structure, expectations, and doubts.

### ✅ Mock Interview (45 mins)
- Practiced coding in Google Docs (no IDE support).
- Helped get comfortable with the interview format.

---

## 🔍 Preliminary Coding Round (45 mins)

- ✅ 1 Warm-up: List comprehension
- ✅ 1 Medium: Tree-based problem
- ✅ 1 Hard: Dynamic programming

> 🎉 Cleared with a **Strong Hire** rating!

---

## 💻 Technical Interview Rounds

### 🔹 1st Technical Interview (45 mins)
- **Topic:** Dynamic Programming, 2D Arrays  
- **Difficulty:** Leetcode Medium  
- **Outcome:** ✅ **Strong Hire**

Walked through my approach, coded, dry-ran, and discussed time complexity.

---

### 🔹 2nd Technical Interview (45 mins)
- **Topic:** Trees, DFS, DP  
- **Difficulty:** Leetcode Hard  
- **Outcome:** ✅ **Hire**

Solved quickly, handled follow-ups, and discussed complexities.

---

### 🔹 3rd Technical Interview (45 mins)
- **Topic:** Dynamic Programming, Heap, Arrays  
- **Difficulty:** Leetcode Hard  
- **Outcome:** ✅ **Lean Hire**

This was the most challenging. I iterated based on feedback, dry-ran test cases, and addressed edge cases.

---

## 🧠 Machine Learning Round

This round focused on both theory and implementation:
- Building a **CNN from scratch**
- In-depth discussion on **ML algorithms**
- Explaining **mathematical foundations** behind models

---

## 🌟 Key Takeaways

- **Adaptability is key** – Google's interviews emphasize **collaboration**, **clarity of thought**, and **responsiveness to feedback**, not just correct answers.
- **Preparation matters**, but evolving your approach in real-time is equally important.
- Be ready to **communicate** your thinking and **justify your decisions**.
---
