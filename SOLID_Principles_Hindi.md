
# 🔷 SOLID Principles – Explained in Hindi (with Simple Examples)

> SOLID principles help in writing clean, maintainable, and scalable object-oriented code. ये principles हर developer को Low-Level Design (LLD) में follow करने चाहिए।

---

## 🔵 1. S – Single Responsibility Principle (SRP)

📌 **Definition:**  
एक class का सिर्फ एक ही काम होना चाहिए – एक ही reason से change होना चाहिए।

🧠 **आसान भाषा:**  
"Ek naukar ek kaam" — अगर किसी को कई काम दे दिए, तो कोई भी ढंग से नहीं होगा।

### ❌ Bad Example:
```java
class Invoice {
    void calculateTotal() {}
    void printInvoice() {}
    void saveToDatabase() {}
}
```

### ✅ Good Design:
```java
class InvoiceCalculator { void calculateTotal() {} }
class InvoicePrinter { void printInvoice() {} }
class InvoiceRepository { void saveToDatabase() {} }
```

### ✅ UML Diagram:
```plaintext
+-----------------------+         +---------------------+
| InvoiceCalculator     |         | InvoicePrinter      |
|-----------------------|         |---------------------|
| + calculateTotal()    |         | + printInvoice()    |
+-----------------------+         +---------------------+
                 \_________________
                  \
                   \
             +-------------------------+
             | InvoiceRepository       |
             |-------------------------|
             | + saveToDatabase()      |
             +-------------------------+
```
---

## 🟠 2. O – Open/Closed Principle (OCP)

📌 **Definition:**  
Code open होना चाहिए extension के लिए, लेकिन closed होना चाहिए modification के लिए।

🧠 **आसान भाषा:**  
"Naye features जोड़ो, पुराने code को मत छेड़ो"

### ❌ Bad Example:
```java
class DiscountCalculator {
    int getDiscount(String customerType) {
        if (customerType.equals("Regular")) return 10;
        else if (customerType.equals("Premium")) return 20;
        else return 0;
    }
}
```

### ✅ Good Design:
```java
interface DiscountStrategy {
    int getDiscount();
}

class RegularCustomer implements DiscountStrategy {
    public int getDiscount() { return 10; }
}

class PremiumCustomer implements DiscountStrategy {
    public int getDiscount() { return 20; }
}

class DiscountCalculator {
    private DiscountStrategy strategy;
    DiscountCalculator(DiscountStrategy strategy) {
        this.strategy = strategy;
    }
    int calculateDiscount() {
        return strategy.getDiscount();
    }
}
```
```plaintext
           +------------------------+
           |    DiscountStrategy    |<----------------------+
           |------------------------|                       |
           | + getDiscount()        |                       |
           +------------------------+                       |
                    ^                                        |
     +-----------------------------+      +-----------------------------+
     | RegularCustomer             |      | PremiumCustomer             |
     |-----------------------------|      |-----------------------------|
     | + getDiscount()             |      | + getDiscount()             |
     +-----------------------------+      +-----------------------------+

                           |
                           v
            +-----------------------------+
            |     DiscountCalculator      |
            |-----------------------------|
            | - strategy: DiscountStrategy|
            | + calculateDiscount()       |
            +-----------------------------+
```
---

## 🟡 3. L – Liskov Substitution Principle (LSP)

📌 **Definition:**  
Base class की जगह उसकी derived (child) class use कर सकें, और program का behavior न बदले।

🧠 **आसान भाषा:**  
"Bachcha agar maa ke jagah kaam kare, to sab kuch smooth chale" — subclass वही behave करे जो superclass करता है।

### ❌ Violation:
```java
class Bird {
    void fly() {}
}

class Ostrich extends Bird {
    void fly() {
        throw new UnsupportedOperationException("Ostrich can't fly!");
    }
}
```

### ✅ Good Design:
```java
interface Bird { void eat(); }

interface FlyingBird extends Bird { void fly(); }

class Sparrow implements FlyingBird {
    public void eat() {}
    public void fly() {}
}

class Ostrich implements Bird {
    public void eat() {}
}
```
### ✅ UML Diagram:
```plaintext
       +--------------------+
       |     Bird           |
       |--------------------|
       | + eat()            |
       +--------------------+
               ^
               |
   +--------------------+      +----------------------+
   |    Sparrow         |      |      Ostrich         |
   |--------------------|      |----------------------|
   | + eat()            |      | + eat()              |
   | + fly()            |      |                      |
   +--------------------+      +----------------------+

✅ Bird interface को दो हिस्सों में divide करके Ostrich और Sparrow का सही abstraction हुआ।
```

---

## 🟢 4. I – Interface Segregation Principle (ISP)

📌 **Definition:**  
Client को ऐसा interface implement करने को मजबूर नहीं करना चाहिए जो वो use नहीं करता।

🧠 **आसान भाषा:**  
"Menu में वही item दिखाओ जो खाना है" – ज़बरदस्ती सब कुछ मत परोस दो।

### ❌ Violation:
```java
interface Worker {
    void work();
    void eat();
}

class Robot implements Worker {
    public void work() {}
    public void eat() {} // Robot को खाना नहीं चाहिए!
}
```

### ✅ Good Design:
```java
interface Workable { void work(); }
interface Eatable { void eat(); }

class Human implements Workable, Eatable {
    public void work() {}
    public void eat() {}
}

class Robot implements Workable {
    public void work() {}
}
```
### ✅ UML Diagram:
```plaintext
     +--------------------+         +--------------------+
     |    Workable        |         |     Eatable        |
     |--------------------|         |--------------------|
     | + work()           |         | + eat()            |
     +--------------------+         +--------------------+

           ^                               ^
           |                               |
   +----------------+              +------------------+
   |     Robot      |              |     Human        |
   |----------------|              |------------------|
   | + work()       |              | + work()         |
   |                |              | + eat()          |
   +----------------+              +------------------+
```

---

## 🔴 5. D – Dependency Inversion Principle (DIP)

📌 **Definition:**  
High-level और low-level modules को interface के माध्यम से connect करो – direct dependency नहीं होनी चाहिए।

🧠 **आसान भाषा:**  
"Boss को ye nahi pata होना चाहिए कि kaam कौन कर रहा है, बस kaam हो रहा है!"

### ❌ Bad Design:
```java
class LightBulb {
    void turnOn() {}
}

class Switch {
    LightBulb bulb;
    void operate() {
        bulb.turnOn();
    }
}
```

### ✅ Good Design:
```java
interface Switchable {
    void turnOn();
}

class LightBulb implements Switchable {
    public void turnOn() {}
}

class Fan implements Switchable {
    public void turnOn() {}
}

class Switch {
    Switchable device;
    Switch(Switchable device) {
        this.device = device;
    }
    void operate() {
        device.turnOn();
    }
}
```
### ✅ UML Diagram:
```plaintext
       +----------------------+
       |    Switchable        |<---------------------+
       |----------------------|                      |
       | + turnOn()           |                      |
       +----------------------+                      |
              ^                                      ^
              |                                      |
   +-------------------+               +--------------------+
   |    LightBulb      |               |       Fan          |
   |-------------------|               |--------------------|
   | + turnOn()        |               | + turnOn()         |
   +-------------------+               +--------------------+

                         |
                         v
             +----------------------+
             |       Switch         |
             |----------------------|
             | - device: Switchable |
             | + operate()          |
             +----------------------+
```

---

## ✅ Summary Table

| Principle | Hindi Naam | Kya Sikhaata Hai |
|-----------|-------------|------------------|
| S - SRP   | Ek class, ek kaam | Responsibilities अलग करो |
| O - OCP   | Feature जोड़ो, code मत तोड़ो | Extendable बनाओ |
| L - LSP   | Subclass parent की तरह behave करे | Reliable subclasses |
| I - ISP   | Chhoti chhoti interfaces banao | ज़रूरत जितना ही दो |
| D - DIP   | Interface के ज़रिए dependency banao | Loose coupling karo |

---

> 🚀 ये principles Low-Level Design में strong foundation देते हैं। इन्हें समझो, याद रखो और अपने design में apply करो!


# 🔷 SOLID Principles with UML Diagrams (Hindi + Visuals)

---

## 1️⃣ S – Single Responsibility Principle (SRP)

## 2️⃣ O – Open/Closed Principle (OCP)

## 3️⃣ L – Liskov Substitution Principle (LSP)

## 4️⃣ I – Interface Segregation Principle (ISP)

## 5️⃣ D – Dependency Inversion Principle (DIP)
---



