# 🟡 Intermediate Level

# 20️⃣ Dependency Injection (DI) Hierarchy in Angular – Detailed Guide

---

## ✅ Short Interview Answer

Angular’s Dependency Injection (DI) system is hierarchical. Services can be provided at different levels (root, module, component), and Angular resolves dependencies by searching upward through the injector tree.

---

# 🟢 Simple Explanation

Think of Angular DI like a family tree 🌳

- Root Injector (Top Level)
- Module Injector
- Component Injector

If a component asks for a service:

👉 Angular checks its own injector  
👉 If not found → goes to parent  
👉 If not found → goes to root

This is called **Hierarchical Dependency Injection**.

---

# 🔥 Why DI Hierarchy Matters

It helps control:

- Service scope
- Service lifetime
- Memory usage
- Instance sharing
- Lazy loading behavior

---

# 🟡 Types of Injectors in Angular

1️⃣ Root Injector  
2️⃣ Module Injector  
3️⃣ Component Injector

---

# 1️⃣ Root Injector

When we write:

```ts
@Injectable({ providedIn: 'root' })
```

The service:

- Is available application-wide
- Has a single instance (Singleton)
- Shared across all components

---

# 2️⃣ Module Injector

If provided inside a module:

```ts
@NgModule({
  providers: [UserService]
})
```

The service:

- Is available inside that module
- Lazy-loaded modules create separate instances

---

# 3️⃣ Component Injector

If provided inside component:

```ts
@Component({
  providers: [UserService]
})
```

The service:

- Instance is unique to that component
- Child components inherit it
- Destroyed when component is destroyed

---

# 🔥 How Angular Resolves Dependencies

Resolution process:

1️⃣ Check component injector  
2️⃣ Check parent component injector  
3️⃣ Check module injector  
4️⃣ Check root injector

If not found → Error

---

# 💻 Example Scenario

### Root Provided Service

```ts
@Injectable({ providedIn: "root" })
export class LoggerService {}
```

Used everywhere → Same instance.

---

### Component Provided Service

```ts
@Component({
  selector: 'app-child',
  providers: [LoggerService]
})
```

Each child gets its own instance.

---

# 🧠 Lazy Loading + DI Hierarchy

Lazy-loaded module:

```ts
@NgModule({
  providers: [AuthService]
})
```

Each lazy module:

- Gets its own instance
- Not shared with root

Important for multi-tenant apps.

---

# 🔥 Instance Comparison

| Provided At | Instance Scope | Lifetime           |
| ----------- | -------------- | ------------------ |
| Root        | Singleton      | Entire app         |
| Module      | Per module     | Module lifetime    |
| Component   | Per component  | Component lifetime |

---

# 🚀 Real Enterprise Use Case

Scenario:

- Global AuthService → Root
- Feature-specific ConfigService → Module
- Local UI State Service → Component

This improves memory control and modular architecture.

---

# 🚨 Common Mistakes

- Providing same service at multiple levels accidentally
- Not understanding lazy module instances
- Assuming always singleton
- Overusing component-level providers

---

# 🎯 What Interviewer Is Testing

- Do you understand injector tree?
- Difference between root vs component provider?
- Lazy-loaded module behavior?
- Singleton concept?
- Instance lifecycle?

---

# 🏆 Perfect Interview Answer (2 Minutes)

> Angular’s Dependency Injection system is hierarchical. Services can be provided at root, module, or component level. When a component requests a dependency, Angular searches upward through the injector tree until it finds a provider. Services provided in root are singletons across the app, while services provided in components create separate instances per component. Lazy-loaded modules create their own injector, which can result in separate service instances.

---

# 💬 Common Follow-up Questions

1. What happens in lazy-loaded modules?
2. How to make a true singleton service?
3. Can child component override parent service?
4. What is injector tree?
5. Why use component-level providers?

---

## 🔙 Navigation

[⬅️ Back to Intermediate Questions List](../../README.md)
