# 🟡 Intermediate Level

# 12️⃣ Component Communication in Angular – Detailed Guide

---

## ✅ Short Interview Answer

Component communication in Angular refers to the ways components share data and events. Angular supports communication using @Input/@Output, ViewChild, Services with RxJS Subjects, and state management approaches for scalable architectures.

---

# 🟢 Simple Explanation

In real projects, components are not isolated.

Example:

- Parent component shows a list
- Child component shows item details
- Another component updates the cart count

So they must share data.

👉 Component Communication = Passing data/events between components.

---

# 🔥 Types of Component Communication

There are 4 major scenarios:

1️⃣ Parent → Child  
2️⃣ Child → Parent  
3️⃣ Sibling ↔ Sibling  
4️⃣ Unrelated components (across modules)

---

# 1️⃣ Parent → Child Communication (@Input)

Used when parent sends data to child.

✅ Child receives via `@Input()`

---

### Parent Component

```html
<app-child [message]="parentMessage"></app-child>
```

```ts
parentMessage = "Hello from Parent";
```

### Child Component

```ts
@Input() message!: string;
```

```html
<p>{{ message }}</p>
```

---

# 2️⃣ Child → Parent Communication (@Output + EventEmitter)

Used when child wants to notify parent.

✅ Child emits event using EventEmitter

---

### Child Component

```ts
@Output() notify = new EventEmitter<string>();

sendMessage() {
  this.notify.emit("Hello Parent!");
}
```

```html
<button (click)="sendMessage()">Send</button>
```

---

### Parent Component

```html
<app-child (notify)="onNotify($event)"></app-child>
```

```ts
onNotify(msg: string) {
  console.log(msg);
}
```

---

# 3️⃣ Parent ↔ Child using ViewChild

Used when parent needs access to child component instance.

Example:

- Parent calls child method directly
- Parent reads child variable

---

### Parent Component

```ts
@ViewChild(ChildComponent) child!: ChildComponent;

ngAfterViewInit() {
  this.child.childMethod();
}
```

---

### Child Component

```ts
childMethod() {
  console.log("Called from Parent");
}
```

---

# 4️⃣ Sibling ↔ Sibling Communication (Service + Subject)

Siblings cannot directly use @Input/@Output.

So we use shared service with RxJS Subject / BehaviorSubject.

---

### Shared Service

```ts
import { Injectable } from "@angular/core";
import { BehaviorSubject } from "rxjs";

@Injectable({ providedIn: "root" })
export class DataService {
  private messageSource = new BehaviorSubject<string>("Default");
  message$ = this.messageSource.asObservable();

  updateMessage(msg: string) {
    this.messageSource.next(msg);
  }
}
```

---

### Sibling A (Sender)

```ts
constructor(private dataService: DataService) {}

send() {
  this.dataService.updateMessage("Hello from Sibling A");
}
```

---

### Sibling B (Receiver)

```ts
constructor(private dataService: DataService) {}

ngOnInit() {
  this.dataService.message$.subscribe(msg => console.log(msg));
}
```

---

# 🧠 Subject vs BehaviorSubject (Interview Booster)

| Feature                        | Subject | BehaviorSubject |
| ------------------------------ | ------- | --------------- |
| Stores last value              | ❌ No   | ✅ Yes          |
| Needs initial value            | ❌ No   | ✅ Yes          |
| New subscriber gets last value | ❌ No   | ✅ Yes          |

BehaviorSubject is more common in state management.

---

# 🚀 Unrelated Components Communication

For large apps, communication can happen via:

- Shared Services
- State Management (NgRx, Akita, NGXS)
- Signals Store (modern Angular approach)

---

# 🔥 Best Practices (Enterprise Standard)

✅ Use @Input/@Output for simple parent-child communication  
✅ Use services + BehaviorSubject for sibling or cross-module communication  
✅ Use state management for complex shared data  
✅ Avoid too many ViewChild dependencies (tight coupling)

---

# ❌ Common Mistakes

- Excessive usage of ViewChild
- Nested subscriptions without cleanup
- Using services as global variables
- Overusing EventEmitters across deep trees

---

# 🎯 What Interviewer Is Testing

- Do you know communication patterns?
- Can you choose correct approach for scenario?
- Can you explain Subject vs BehaviorSubject?
- Do you understand coupling vs decoupling?
- How do you scale communication in large apps?

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> Angular supports multiple component communication patterns. Parent-to-child uses @Input, child-to-parent uses @Output with EventEmitter, parent can access child using ViewChild, and sibling or unrelated communication is usually done via a shared service using RxJS Subject or BehaviorSubject. In large-scale applications, state management solutions like NgRx or Signals stores are preferred for predictable and scalable data flow.

---

# 💬 Common Follow-up Questions

1. When to use ViewChild vs @Input?
2. Subject vs BehaviorSubject?
3. How to communicate between modules?
4. What is state management and why needed?
5. How to avoid memory leaks in shared services?

---

## 🔙 Navigation

[⬅️ Back to Intermediate Questions List](../../README.md)
