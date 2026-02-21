# 7️⃣ What is a Service in Angular and Why Do We Use It?

---

## ✅ Short Interview Answer

A service in Angular is a reusable class that contains business logic, data access logic, or shared functionality, and is typically injected into components using Dependency Injection.

---

# 🟢 Simple Explanation (For Freshers)

Imagine you are building a website.

Instead of writing API call code inside every component, 
you create one separate file that handles all API logic.

That separate reusable file is called a **Service**.

👉 Service = Shared Logic Container

For example:
- Login logic
- API calls
- Shared data
- Utility functions

---

# 🔹 Why Do We Need Services?

Without services:
- Code duplication happens.
- Business logic mixes with UI code.
- Hard to maintain and test.

With services:
- Clean separation of concerns.
- Reusable logic.
- Easy testing.
- Better architecture.

---

# 🟡 Technical Explanation (For Experienced Developers)

Services are:

- Plain TypeScript classes
- Decorated with `@Injectable()`
- Managed by Angular's Dependency Injection system

They are typically used for:

- HTTP requests
- State management
- Data transformation
- Authentication logic
- Cross-component communication

---

# 🔥 Basic Example

## Step 1: Create Service

```ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class UserService {

  getUsers() {
    return ["Dipak", "Angular", "Developer"];
  }
}
```

---

## Step 2: Use Service in Component

```ts
import { Component } from '@angular/core';
import { UserService } from './user.service';

@Component({
  selector: 'app-root',
  template: `<ul>
              <li *ngFor="let user of users">{{ user }}</li>
            </ul>`
})
export class AppComponent {

  users: string[];

  constructor(private userService: UserService) {
    this.users = this.userService.getUsers();
  }
}
```

Angular automatically injects the service instance.

---

# 🧠 Important Concepts (Interview Booster)

## 🔹 Singleton Services

When `providedIn: 'root'` is used:
- Angular creates only one instance.
- Shared across entire application.

---

## 🔹 Service vs Component

| Service | Component |
|----------|------------|
| Contains business logic | Controls UI |
| No template | Has template |
| Reusable across app | Used in specific view |
| Injected via DI | Rendered in DOM |

---

## 🔹 Sharing Data Between Components

Services can act as a shared data store:

```ts
sharedData = new BehaviorSubject<string>('Initial');
```

This allows communication between unrelated components.

---

# 🚀 Real-World Usage Examples

- AuthenticationService
- ProductService
- PaymentService
- LoggingService
- NotificationService

Almost every enterprise Angular app heavily relies on services.

---

# 🎯 What Interviewer Is Testing

When this question is asked, interviewer checks:

- Do you understand separation of concerns?
- Can you explain DI usage?
- Do you know singleton behavior?
- Can you implement a basic service?

---

# 🏆 Perfect Interview Answer (1 Minute Version)

> A service in Angular is a reusable TypeScript class used to handle business logic, API communication, or shared data across components. Services are typically provided using Angular’s Dependency Injection system and are often singleton when provided in the root injector.

---

# 💬 Common Follow-up Questions

1. What is the difference between service and component?
2. How are services injected?
3. What is providedIn: 'root'?
4. How do services help in component communication?
5. Can services be provided at component level?

---

## 🔙 Navigation

⬅️ Back to Basic Questions List
