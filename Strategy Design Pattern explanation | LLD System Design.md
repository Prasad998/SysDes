## 🧩 Strategy Design Pattern – Hindi Explanation (LLD Style)
---
## 📘 Definition:
The Strategy Pattern defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from clients that use it.

---

## 🧠 आसान भाषा में समझो:
> **"Kaam वही है, तरीका बदलता रहता है।"**

यानि, behavior को class के बाहर अलग-अलग strategies में define करो, और ज़रूरत के हिसाब से dynamically switch कर सको।

---

## 🎯 Real-World Analogy:
> **Payment Gateway** – UPI, Credit Card, और PayPal से payment करने के अलग-अलग तरीके, लेकिन interface एक जैसा: `pay()`.

---

## ❌ Without Strategy Pattern:
```java
class PaymentService {
    void pay(String method) {
        if (method.equals("UPI")) {
            System.out.println("Paid via UPI");
        } else if (method.equals("CreditCard")) {
            System.out.println("Paid via Credit Card");
        } else if (method.equals("PayPal")) {
            System.out.println("Paid via PayPal");
        }
    }
}
```

## 👎 Problems:

New payment method जोड़ने पर code modify करना पड़ेगा

Violates Open/Closed Principle

Hard to test and maintain

## ✅ With Strategy Pattern:  
**Step 1 – Interface (Strategy):**
```java
interface PaymentStrategy {
    void pay();
}
```
**Step 2 – Concrete Strategies:**
```java
class UpiPayment implements PaymentStrategy {
    public void pay() {
        System.out.println("Paid via UPI");
    }
}

class CreditCardPayment implements PaymentStrategy {
    public void pay() {
        System.out.println("Paid via Credit Card");
    }
}

class PayPalPayment implements PaymentStrategy {
    public void pay() {
        System.out.println("Paid via PayPal");
    }
}
```
**Step 3 – Context Class:**
```java
class PaymentService {
    private PaymentStrategy strategy;

    public PaymentService(PaymentStrategy strategy) {
        this.strategy = strategy;
    }

    public void makePayment() {
        strategy.pay();
    }
}
```

**Step 4 – Usage:**
```java
public class Main {
    public static void main(String[] args) {
        PaymentService service1 = new PaymentService(new UpiPayment());
        service1.makePayment();

        PaymentService service2 = new PaymentService(new CreditCardPayment());
        service2.makePayment();
    }
}
```


**📦 Benefits:**
| Benefit                  | हिंदी में                                      |
| ------------------------ | ---------------------------------------------- |
| ✅ Open/Closed Principle  | नया तरीका जोड़ो, existing code मत तोड़ो        |
| ✅ Separation of Concerns | हर strategy अलग class में                      |
| ✅ Testability            | हर strategy independently test हो सकती है      |
| ✅ Runtime Flexibility    | Strategy को run-time पर switch किया जा सकता है |



**📊 UML Diagram:**

        +---------------------+
        |  PaymentStrategy    |<--------------------+
        |---------------------|                     |
        | + pay()             |                     |
        +---------------------+                     |
                ^                                    |
                |                                    |
    +---------------------+    +---------------------+    +---------------------+
    |    UpiPayment       |    |  CreditCardPayment  |    |   PayPalPayment     |
    |---------------------|    |---------------------|    |---------------------|
    | + pay()             |    | + pay()             |    | + pay()             |
    +---------------------+    +---------------------+    +---------------------+

                |
                v
       +----------------------+
       |   PaymentService     |
       |----------------------|
       | - strategy: PaymentStrategy |
       | + makePayment()      |
       +----------------------+

       
**💡 Conclusion: Strategy pattern आपको flexible, reusable और loosely-coupled code design करने में मदद करता है।**
