# 6️⃣ What is Dependency Injection (DI) in Angular?

---

## ✅ Short Interview Answer

Dependency Injection (DI) is a design pattern used in Angular where required dependencies (like services) are automatically provided to a class instead of the class creating them manually.

---

# 🟢 Simple Explanation (For Freshers)

Imagine you own a restaurant.

Instead of the chef going to the market to buy vegetables every time,
someone else supplies the vegetables to the kitchen.

The chef just uses what is provided.

In Angular:

- Component = Chef
- Service = Vegetable
- Injector = Supplier

👉 Angular automatically supplies required services to components.

This process is called **Dependency Injection**.

---

# 🔹 Why Do We Need Dependency Injection?

Without DI:

- Components would create services manually.
- Code becomes tightly coupled.
- Testing becomes difficult.

With DI:

- Code becomes loosely coupled.
- Services are reusable.
- Easy to mock services during testing.
- Better maintainability.

---

# 🟡 Technical Explanation (For Experienced Developers)

Angular has a built-in hierarchical dependency injection system.

It uses:

- Injectors
- Providers
- Tokens

When a component requests a dependency, Angular:

1. Looks in the component injector.
2. If not found, checks parent injector.
3. Eventually checks the root injector.

This structure improves modularity and scalability.

---

# 🔥 Basic Example

### Step 1: Create Service

```ts
import { Injectable } from "@angular/core";

@Injectable({
  providedIn: "root",
})
export class UserService {
  getUsers() {
    return ["Dipak", "Angular"];
  }
}
```

---

### Step 2: Inject Service into Component

```ts
import { Component } from "@angular/core";
import { UserService } from "./user.service";

@Component({
  selector: "app-root",
  template: `<h2>{{ users }}</h2>`,
})
export class AppComponent {
  users: string[];

  constructor(private userService: UserService) {
    this.users = this.userService.getUsers();
  }
}
```

Angular automatically provides `UserService` instance.

---

# 🧠 Important Concepts (Interview Booster)

## 🔹 providedIn: 'root'

- Makes the service singleton.
- Available application-wide.
- Recommended approach.

---

## 🔹 Injector Hierarchy

Angular DI works hierarchically:

- Root Injector
- Module Injector
- Component Injector

This allows scoped service instances.

---

## 🔹 Singleton Services

When provided in root, Angular creates only one instance and shares it across the app.

---

# 🚀 Advantages of Dependency Injection

- Loose coupling
- Better testing (easy mocking)
- Improved modularity
- Centralized dependency management
- Cleaner architecture

---

# 🎯 What Interviewer Is Testing

When this question is asked, interviewer checks:

- Do you understand DI conceptually?
- Can you explain injector hierarchy?
- Do you know singleton services?
- Can you inject a service properly?

---

# 🏆 Perfect Interview Answer (1 Minute Version)

> Dependency Injection in Angular is a design pattern where services or dependencies are automatically provided to components using Angular's built-in injector system. It promotes loose coupling, reusability, and better testability. Services are typically provided in the root injector to make them singleton across the application.

---

# 💬 Common Follow-up Questions

1. What is injector hierarchy?
2. What is providedIn: 'root'?
3. What are multi-providers?
4. How do you provide service at component level?
5. Difference between useClass, useValue, useFactory?

---

## 🔙 Navigation

[⬅️ Back to Basic Questions List](../../README.md)
