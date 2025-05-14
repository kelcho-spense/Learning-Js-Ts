# OOP Practise Scenarios

Great — let's elevate the **complexity** of each OOP scenario. Below are **enhanced versions** of the same ideas, introducing deeper interactions, more OOP principles (inheritance, encapsulation, polymorphism, abstraction), and even some design patterns where applicable.

---

### 🔷 1. **Advanced Library Management System**

**Description:**
Design a system for managing a full-service library, including book lending, user accounts, overdue fines, and digital resources.

#### Key Elements:

* **`LibraryItem` (abstract)** → base for `Book`, `DVD`, `EBook`
* **`UserAccount`** → handles login, borrowing history, fine calculation
* **`Borrowable` Interface** → enforces `checkOut()` and `returnItem()` for physical items only
* **`Librarian` vs `Member` (inherit from `User`)**
* **Feature:** Fine is auto-calculated based on return date

> 🔹 *Polymorphism* through multiple item types
> 🔹 *Encapsulation* of fine logic in `UserAccount`
> 🔹 *Abstraction* using an abstract `LibraryItem`
> 🔹 *Interface* for borrowable vs digital-only items

---

### 🔷 2. **Advanced E-Commerce System**

**Description:**
Create a multi-vendor e-commerce platform supporting different product types, user roles (admin, customer, seller), discounts, and order tracking.

#### Key Elements:

* **`Product` (abstract)** → extended by `ElectronicProduct`, `ClothingProduct`, `FurnitureProduct`
* **`User`** → extended by `Admin`, `Seller`, `Customer`
* **`Cart`** → holds products, calculates total with tax and discount
* **`Order`** → links to `Shipping`, `Payment`, and `Customer`
* **Strategy Pattern:** Discount strategy applied at checkout

> 🔹 *Inheritance* for product and user types
> 🔹 *Polymorphism* for payment (e.g. card, wallet, COD)
> 🔹 *Encapsulation* of cart/checkout logic
> 🔹 *Design Patterns:* Strategy (for discount), Factory (for product creation)

---

### 🔷 3. **University Registration & Learning Management System**

**Description:**
Build a system that manages course registration, class schedules, grading, and content distribution. Include roles for students, professors, and administrators.

#### Key Elements:

* **`Person`** → base for `Student`, `Professor`, `Admin`
* **`Course`** → includes lectures, assignments, enrolled students
* **`Enrollment` Class** → maps students to courses with grading logic
* **`Assessment` Interface** → implemented by `Quiz`, `Assignment`, `Project`
* **Notification System** for reminders and feedback

> 🔹 *Abstraction* for people and content
> 🔹 *Polymorphism* in assessments
> 🔹 *Encapsulation* of grade calculations
> 🔹 *Composite Pattern* for course content (modules contain lectures, assignments)

---

### 🔷 4. **Ride Sharing System with Dynamic Pricing & Ratings**

**Description:**
Create a full ride-sharing platform with user authentication, GPS location tracking, ride history, and driver/passenger matching logic.

#### Key Elements:

* **`User`** → parent for `Driver`, `Passenger`
* **`Ride`** → includes pickup/dropoff, fare calculation, ratings
* **Dynamic Pricing Strategy** based on time of day, traffic
* **Vehicle Management** for drivers
* **Matching Algorithm** → nearest driver selection

> 🔹 *Polymorphism* in pricing strategies
> 🔹 *Encapsulation* of rating and fare logic
> 🔹 *Strategy Pattern* for fare calculation
> 🔹 *Factory Pattern* for creating ride instances

---

### 🔷 5. **Intelligent Zoo Management System**

**Description:**
Develop a smart zoo system with intelligent feeding schedules, sensor-driven habitat monitoring, and animal behavior tracking.

#### Key Elements:

* **`Animal` (abstract)** → extended by `Bird`, `Mammal`, `Reptile`
* **`Habitat`** → includes temperature, feeding schedule, cleanliness
* **Observer Pattern:** Animal health alerts via sensors
* **`FeedingStrategy` Interface** → different feeding logic for herbivores, carnivores, omnivores
* **Zookeeper & Vet Roles** for monitoring

> 🔹 *Polymorphism* in animal behavior and feeding
> 🔹 *Encapsulation* of habitat control
> 🔹 *Observer Pattern* for real-time alerts
> 🔹 *Interface Segregation* for specific animal actions (fly, swim, hibernate)

---