
# Design Patterns Study Guide

## 1. Factory Method Pattern
**Implement the Factory Method design pattern.**
**The *Factory Method* is a creational design pattern that provides an interface for creating objects in a superclass but allows subclasses to alter the type of objects that will be created.**
**You are given code that includes a few vehicles types and their respective factories. Complete the factory method implementation such that each factory returns the correct vehicle.**

**Example:**
```cpp
VehicleFactory carFactory = new CarFactory();
VehicleFactory truckFactory = new TruckFactory();
VehicleFactory bikeFactory = new BikeFactory();
Vehicle myCar = carFactory.createVehicle();
Vehicle myTruck = truckFactory.createVehicle();
Vehicle myBike = bikeFactory.createVehicle();
myCar.getType();   // "Car"
myTruck.getType(); // "Truck"
myBike.getType();  // "Bike"
```

**Solution:**
```cpp
class Vehicle {
public:
    virtual string getType() = 0;
};

class Car : public Vehicle {
public:
    string getType() override {
        return "Car";
    }
};

class Bike : public Vehicle {
public:
    string getType() override {
        return "Bike";
    }
};

class Truck : public Vehicle {
public:
    string getType() override {
        return "Truck";
    }
};

class VehicleFactory {
public:
    virtual Vehicle* createVehicle() = 0;
};

class CarFactory : public VehicleFactory {
public:
    Vehicle* createVehicle() override {
        return new Car();
    }
};

class BikeFactory : public VehicleFactory {
public:
    Vehicle* createVehicle() override {
        return new Bike();
    }
};

class TruckFactory : public VehicleFactory {
public:
    Vehicle* createVehicle() override {
        return new Truck();
    }
};
```

## 2. Singleton Pattern
**Implement the Singleton design pattern.**
**The *Singleton* is a creational design pattern that ensures a class has only one instance and provides a global point of access to that instance.**
**You are given a Database class that should have only one instance throughout the application. Complete the singleton implementation to ensure only one database connection exists.**

**Example:**
```cpp
Database* db1 = Database::getInstance();
Database* db2 = Database::getInstance();
db1->connect();     // "Connected to database"
db2->connect();     // "Connected to database"
// db1 and db2 point to the same instance
assert(db1 == db2); // true
```

**Solution:**
```cpp
class Database {
private:
    static Database* instance;
    Database() {} // Private constructor

public:
    static Database* getInstance() {
        // Write your code here
    }
    
    void connect() {
        cout << "Connected to database" << endl;
    }
    
    // Delete copy constructor and assignment operator
    Database(const Database&) = delete;
    Database& operator=(const Database&) = delete;
};

Database* Database::instance = nullptr;
```

## 3. Builder Pattern
**Implement the Builder design pattern.**
**The *Builder* is a creational design pattern that lets you construct complex objects step by step. The pattern allows you to produce different types and representations of an object using the same construction code.**
**You are given a House class with multiple optional components. Complete the builder implementation to construct houses with different configurations.**

**Example:**
```cpp
HouseBuilder builder;
House* house = builder.setFoundation("Concrete")
                     .setWalls("Brick")
                     .setRoof("Tile")
                     .setGarage(true)
                     .build();
house->getDescription(); // "House with Concrete foundation, Brick walls, Tile roof, and garage"
```

**Solution:**
```cpp
class House {
private:
    string foundation;
    string walls;
    string roof;
    bool hasGarage;

public:
    House() : hasGarage(false) {}
    
    void setFoundation(string f) { foundation = f; }
    void setWalls(string w) { walls = w; }
    void setRoof(string r) { roof = r; }
    void setGarage(bool g) { hasGarage = g; }
    
    string getDescription() {
        string desc = "House with " + foundation + " foundation, " + walls + " walls, " + roof + " roof";
        if (hasGarage) desc += ", and garage";
        return desc;
    }
};

class HouseBuilder {
private:
    House* house;

public:
    HouseBuilder() {
        house = new House();
    }
    
    HouseBuilder& setFoundation(string foundation) {
        // Write your code here
    }
    
    HouseBuilder& setWalls(string walls) {
        // Write your code here
    }
    
    HouseBuilder& setRoof(string roof) {
        // Write your code here
    }
    
    HouseBuilder& setGarage(bool garage) {
        // Write your code here
    }
    
    House* build() {
        // Write your code here
    }
};
```

## 4. Prototype Pattern
**Implement the Prototype design pattern.**
**The *Prototype* is a creational design pattern that lets you copy existing objects without making your code dependent on their classes.**
**You are given a Shape hierarchy where each shape should be able to clone itself. Complete the prototype implementation for different shapes.**

**Example:**
```cpp
Shape* circle = new Circle(5);
Shape* rectangle = new Rectangle(10, 20);
Shape* clonedCircle = circle->clone();
Shape* clonedRectangle = rectangle->clone();
clonedCircle->getInfo();    // "Circle with radius: 5"
clonedRectangle->getInfo(); // "Rectangle with width: 10, height: 20"
```

**Solution:**
```cpp
class Shape {
public:
    virtual Shape* clone() = 0;
    virtual string getInfo() = 0;
    virtual ~Shape() {}
};

class Circle : public Shape {
private:
    int radius;

public:
    Circle(int r) : radius(r) {}
    
    Shape* clone() override {
        // Write your code here
    }
    
    string getInfo() override {
        return "Circle with radius: " + to_string(radius);
    }
};

class Rectangle : public Shape {
private:
    int width, height;

public:
    Rectangle(int w, int h) : width(w), height(h) {}
    
    Shape* clone() override {
        // Write your code here
    }
    
    string getInfo() override {
        return "Rectangle with width: " + to_string(width) + ", height: " + to_string(height);
    }
};
```

## 5. Adapter Pattern
**Implement the Adapter design pattern.**
**The *Adapter* is a structural design pattern that allows objects with incompatible interfaces to collaborate.**
**You are given a legacy printer system and a modern document system. Complete the adapter implementation to make them work together.**

**Example:**
```cpp
LegacyPrinter* legacyPrinter = new LegacyPrinter();
ModernPrinter* adapter = new PrinterAdapter(legacyPrinter);
adapter->print("Hello World"); // "Legacy printing: Hello World"
```

**Solution:**
```cpp
class LegacyPrinter {
public:
    void printOldWay(string text) {
        cout << "Legacy printing: " << text << endl;
    }
};

class ModernPrinter {
public:
    virtual void print(string document) = 0;
};

class PrinterAdapter : public ModernPrinter {
private:
    LegacyPrinter* legacyPrinter;

public:
    PrinterAdapter(LegacyPrinter* printer) : legacyPrinter(printer) {}
    
    void print(string document) override {
        // Write your code here
    }
};
```

## 6. Decorator Pattern
**Implement the Decorator design pattern.**
**The *Decorator* is a structural design pattern that lets you attach new behaviors to objects by placing these objects inside special wrapper objects that contain the behaviors.**
**You are given a coffee ordering system where you can add various toppings. Complete the decorator implementation to add toppings to coffee.**

**Example:**
```cpp
Coffee* coffee = new SimpleCoffee();
coffee = new MilkDecorator(coffee);
coffee = new SugarDecorator(coffee);
coffee->getDescription(); // "Simple Coffee, Milk, Sugar"
coffee->getCost();        // 3.5
```

**Solution:**
```cpp
class Coffee {
public:
    virtual string getDescription() = 0;
    virtual double getCost() = 0;
    virtual ~Coffee() {}
};

class SimpleCoffee : public Coffee {
public:
    string getDescription() override {
        return "Simple Coffee";
    }
    
    double getCost() override {
        return 2.0;
    }
};

class CoffeeDecorator : public Coffee {
protected:
    Coffee* coffee;

public:
    CoffeeDecorator(Coffee* c) : coffee(c) {}
};

class MilkDecorator : public CoffeeDecorator {
public:
    MilkDecorator(Coffee* c) : CoffeeDecorator(c) {}
    
    string getDescription() override {
        // Write your code here
    }
    
    double getCost() override {
        // Write your code here
    }
};

class SugarDecorator : public CoffeeDecorator {
public:
    SugarDecorator(Coffee* c) : CoffeeDecorator(c) {}
    
    string getDescription() override {
        // Write your code here
    }
    
    double getCost() override {
        // Write your code here
    }
};
```

## 7. Facade Pattern
**Implement the Facade design pattern.**
**The *Facade* is a structural design pattern that provides a simplified interface to a library, a framework, or any other complex set of classes.**
**You are given a complex home theater system with multiple components. Complete the facade implementation to provide a simple interface for common operations.**

**Example:**
```cpp
HomeTheaterFacade* theater = new HomeTheaterFacade();
theater->watchMovie();  // Turns on all components and starts movie
theater->endMovie();    // Turns off all components
```

**Solution:**
```cpp
class DVDPlayer {
public:
    void on() { cout << "DVD Player on" << endl; }
    void play() { cout << "DVD Player playing" << endl; }
    void stop() { cout << "DVD Player stopped" << endl; }
    void off() { cout << "DVD Player off" << endl; }
};

class Projector {
public:
    void on() { cout << "Projector on" << endl; }
    void setInput() { cout << "Projector input set" << endl; }
    void off() { cout << "Projector off" << endl; }
};

class SoundSystem {
public:
    void on() { cout << "Sound system on" << endl; }
    void setVolume(int volume) { cout << "Volume set to " << volume << endl; }
    void off() { cout << "Sound system off" << endl; }
};

class HomeTheaterFacade {
private:
    DVDPlayer* dvd;
    Projector* projector;
    SoundSystem* sound;

public:
    HomeTheaterFacade() {
        dvd = new DVDPlayer();
        projector = new Projector();
        sound = new SoundSystem();
    }
    
    void watchMovie() {
        // Write your code here
    }
    
    void endMovie() {
        // Write your code here
    }
};
```

## 8. Strategy Pattern
**Implement the Strategy design pattern.**
**The *Strategy* is a behavioral design pattern that lets you define a family of algorithms, put each of them into a separate class, and make their objects interchangeable.**
**You are given a payment processing system that should support different payment methods. Complete the strategy implementation for various payment types.**

**Example:**
```cpp
PaymentProcessor* processor = new PaymentProcessor();
processor->setStrategy(new CreditCardStrategy());
processor->processPayment(100.0); // "Processing $100 via Credit Card"
processor->setStrategy(new PayPalStrategy());
processor->processPayment(50.0);  // "Processing $50 via PayPal"
```

**Solution:**
```cpp
class PaymentStrategy {
public:
    virtual void pay(double amount) = 0;
    virtual ~PaymentStrategy() {}
};

class CreditCardStrategy : public PaymentStrategy {
public:
    void pay(double amount) override {
        // Write your code here
    }
};

class PayPalStrategy : public PaymentStrategy {
public:
    void pay(double amount) override {
        // Write your code here
    }
};

class BankTransferStrategy : public PaymentStrategy {
public:
    void pay(double amount) override {
        // Write your code here
    }
};

class PaymentProcessor {
private:
    PaymentStrategy* strategy;

public:
    void setStrategy(PaymentStrategy* s) {
        strategy = s;
    }
    
    void processPayment(double amount) {
        // Write your code here
    }
};
```

## 9. Observer Pattern
**Implement the Observer design pattern.**
**The *Observer* is a behavioral design pattern that lets you define a subscription mechanism to notify multiple objects about any events that happen to the object they're observing.**
**You are given a weather station that should notify multiple displays when weather data changes. Complete the observer implementation.**

**Example:**
```cpp
WeatherStation* station = new WeatherStation();
CurrentConditionsDisplay* display1 = new CurrentConditionsDisplay();
ForecastDisplay* display2 = new ForecastDisplay();
station->addObserver(display1);
station->addObserver(display2);
station->setWeatherData(25.0, 65.0); // Both displays get updated
```

**Solution:**
```cpp
class Observer {
public:
    virtual void update(float temperature, float humidity) = 0;
    virtual ~Observer() {}
};

class Subject {
public:
    virtual void addObserver(Observer* observer) = 0;
    virtual void removeObserver(Observer* observer) = 0;
    virtual void notifyObservers() = 0;
    virtual ~Subject() {}
};

class WeatherStation : public Subject {
private:
    vector<Observer*> observers;
    float temperature;
    float humidity;

public:
    void addObserver(Observer* observer) override {
        // Write your code here
    }
    
    void removeObserver(Observer* observer) override {
        // Write your code here
    }
    
    void notifyObservers() override {
        // Write your code here
    }
    
    void setWeatherData(float temp, float hum) {
        temperature = temp;
        humidity = hum;
        notifyObservers();
    }
};

class CurrentConditionsDisplay : public Observer {
public:
    void update(float temperature, float humidity) override {
        // Write your code here
    }
};

class ForecastDisplay : public Observer {
public:
    void update(float temperature, float humidity) override {
        // Write your code here
    }
};
```

## 10. State Pattern
**Implement the State design pattern.**
**The *State* is a behavioral design pattern that lets an object alter its behavior when its internal state changes. It appears as if the object changed its class.**
**You are given a vending machine that should behave differently based on its current state. Complete the state implementation for different machine states.**

**Example:**
```cpp
VendingMachine* machine = new VendingMachine();
machine->insertCoin();    // "Coin inserted. Please select item."
machine->selectItem();    // "Item dispensed. Please take your item."
machine->insertCoin();    // "Coin inserted. Please select item."
machine->dispenseItem();  // "Please select an item first."
```

**Solution:**
```cpp
class VendingMachine;

class State {
public:
    virtual void insertCoin(VendingMachine* machine) = 0;
    virtual void selectItem(VendingMachine* machine) = 0;
    virtual void dispenseItem(VendingMachine* machine) = 0;
    virtual ~State() {}
};

class IdleState : public State {
public:
    void insertCoin(VendingMachine* machine) override {
        // Write your code here
    }
    
    void selectItem(VendingMachine* machine) override {
        // Write your code here
    }
    
    void dispenseItem(VendingMachine* machine) override {
        // Write your code here
    }
};

class HasCoinState : public State {
public:
    void insertCoin(VendingMachine* machine) override {
        // Write your code here
    }
    
    void selectItem(VendingMachine* machine) override {
        // Write your code here
    }
    
    void dispenseItem(VendingMachine* machine) override {
        // Write your code here
    }
};

class DispensingState : public State {
public:
    void insertCoin(VendingMachine* machine) override {
        // Write your code here
    }
    
    void selectItem(VendingMachine* machine) override {
        // Write your code here
    }
    
    void dispenseItem(VendingMachine* machine) override {
        // Write your code here
    }
};

class VendingMachine {
private:
    State* currentState;
    State* idleState;
    State* hasCoinState;
    State* dispensingState;

public:
    VendingMachine() {
        idleState = new IdleState();
        hasCoinState = new HasCoinState();
        dispensingState = new DispensingState();
        currentState = idleState;
    }
    
    void setState(State* state) {
        currentState = state;
    }
    
    State* getIdleState() { return idleState; }
    State* getHasCoinState() { return hasCoinState; }
    State* getDispensingState() { return dispensingState; }
    
    void insertCoin() {
        currentState->insertCoin(this);
    }
    
    void selectItem() {
        currentState->selectItem(this);
    }
    
    void dispenseItem() {
        currentState->dispenseItem(this);
    }
};
```



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
        |  PaymentStrategy    |<---------------------+
        |---------------------|                      |
        | + pay()             |                      |
        +---------------------+                      |
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
