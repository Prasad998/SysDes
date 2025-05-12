# 🛠️ System Design Process
🎥 **Watch:** [Exponent -YT](https://youtu.be/L9TfZdODuFQ?si=M8lI5aTCSEZZRwrV)

## 1. Define the Problem Space
- Understand the problem and define its scope.
- Clarify **functional** and **non-functional** requirements.
- State **assumptions** and **decisions** clearly and explicitly.

## 2. Design the System at a High Level
- Design **APIs** to define how clients access system resources.
- Consider request parameters, response types, and **client-server communication**.
- Create a **high-level design diagram** to represent system architecture.

## 3. Deep Dive into the Design
- Analyze system **components** and their **interactions** in depth.
- Evaluate how **non-functional requirements** influence design decisions.
- Present **design alternatives** with their **pros and cons**.

## 4. Identify Bottlenecks and Scaling Opportunities
- Evaluate how the system performs under **varied conditions** and **growth**.
- Identify and address:
  - **Single points of failure**
  - **Data replication**
  - **Global availability**
  - **Scalability**
- Techniques to consider:
  - **Horizontal sharding**
  - **CDN**
  - **Caching**
  - **Rate limiting**
  - **Database design**

## 5. Review and Wrap Up
- Summarize key decisions with **justifications** and **trade-offs**.
- Ensure the design meets all stated requirements.
- Suggest **potential improvements** and **future directions**.


**For Example ---**

_I am not sure if I am right as I am a beginner, I am just listing what came to my mind as components for an image sharing service._

1. User Registration/SignIn service.
2. A Followers/Following DB Structure so that users can follow each other.
3. An API for the User to POST an image. 
4. A GET API for other users to view the images posted.
5. An ML model served through an API for recommending people to follow other users.
6. Like and Comment option
7. Block/ Report option
    
