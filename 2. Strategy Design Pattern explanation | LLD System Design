# Creating markdown content for Strategy Design Pattern with UML diagram and examples

markdown_content = """
# 🧩 Strategy Design Pattern – Hindi Explanation (LLD Style)

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
