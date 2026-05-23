[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23993044&assignment_repo_type=AssignmentRepo)
# Lab 05: Interfaces — The Universal Payment Gateway 💳

## 🎯 Learning Objective
In our previous labs, we used **Inheritance** and **Abstract Classes** to define what objects *are*. In this lab, we use **Interfaces** to define what objects *can do*. You will build a system that processes payments from unrelated sources (Credit Cards and PayPal) using a single, unified interface.

---

## 🏗️ The Architecture
An interface acts as a **contract**. Any class that `implements` the `PaymentMethod` interface is "promising" the Java compiler that it will provide its own specific logic for the `processPayment` method.



---

## 🛠️ Instructions

### 1. Define the Interface
Create a file named `PaymentMethod.java`.
* It must be an `interface`.
* It should have one method signature: `void processPayment(double amount);`.

### 2. Implement Credit Card Logic
Create a file named `CreditCard.java`.
* It must `implements PaymentMethod`.
* **Field:** One private `String` for the `cardNumber`.
* **Constructor:** Initialize the card number.
* **Method:** Implement `processPayment` to print:  
  `"Charging $[amount] to Card: [cardNumber]"`

### 3. Implement PayPal Logic
Create a file named `PayPal.java`.
* It must `implements PaymentMethod`.
* **Field:** One private `String` for the `email`.
* **Constructor:** Initialize the email.
* **Method:** Implement `processPayment` to print:  
  `"Redirecting $[amount] to PayPal account: [email]"`

### 4. The Driver Class (Main)
In `Main.java`, demonstrate **Interface Polymorphism**:
1. Create a `List<PaymentMethod>`.
2. Add one `CreditCard` object and one `PayPal` object to that list.
3. Loop through the list and call `.processPayment(99.99)` on every object.

---

## ✅ Submission Checklist
Before you `git push`, make sure:
- [ ] You used the keyword `interface` for `PaymentMethod`.
- [ ] You used the keyword `implements` in `CreditCard` and `PayPal`.
- [ ] Your fields (`cardNumber` and `email`) are marked **private**.
- [ ] Your `Main.java` uses a `List<PaymentMethod>` rather than two separate lists.
- [ ] The code compiles locally without errors.

---

## 🆘 Troubleshooting & Autograder
* **Timed Out:** Check for infinite loops in your `Main` method.
* **Exit Code 1:** This usually means a syntax error. Check your semicolons and curly braces!
* **Reflection Error:** The autograder checks if your fields are private. If you get this error, ensure you are using proper **Encapsulation**.

---

## 🚀 Why does this matter? (The Path to SOLID)

This lab introduces you to the core of **High-Quality Software Design**. In the coming weeks, we will study **SOLID Principles**. This specific lab demonstrates the **Open-Closed Principle (OCP)**:

> **"Software entities should be open for extension, but closed for modification."**

### How it works here:
1. **Open for Extension:** If our store suddenly wants to accept **Bitcoin**, we don't need to change the existing `CreditCard` or `PayPal` code. We simply "extend" the system by creating a new `Bitcoin.java` class that `implements PaymentMethod`.
2. **Closed for Modification:** The `Main` class (our Checkout system) is "closed." It doesn't need to be edited or re-tested every time a new payment type is added because it only interacts with the `PaymentMethod` interface, not the specific classes.

By using interfaces, you create "pluggable" code that is easier to maintain, test, and refactor!
