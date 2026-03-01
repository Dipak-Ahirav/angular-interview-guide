# 2️⃣ What are Components in Angular?

---

## ✅ Short Interview Answer

Components are the fundamental building blocks of Angular applications. Each component controls a specific part of the UI and contains its template, logic, and metadata.

---

# 🟢 Simple Explanation (For Freshers)

Think of a website like a LEGO structure.

Each small LEGO piece builds a small part of the structure.

In Angular:

- Header is a component
- Footer is a component
- Login form is a component
- Dashboard card is a component

👉 An Angular application is made up of multiple components combined together.

---

## 🔹 What Does a Component Contain?

Every Angular component has three main parts:

1️⃣ **Template (HTML)** → Defines the UI  
2️⃣ **Class (TypeScript)** → Contains logic and data  
3️⃣ **Metadata (@Component decorator)** → Configuration for Angular

---

# 🟡 Technical Explanation (For Experienced Developers)

A component is a TypeScript class decorated with `@Component`, which tells Angular:

- The selector (custom HTML tag)
- The template (inline or external)
- The styles
- Change detection strategy (optional)

Angular applications follow a **component tree structure**.

Example hierarchy:

AppComponent  
 ├── HeaderComponent  
 ├── SidebarComponent  
 ├── DashboardComponent  
 │ ├── CardComponent  
 │ └── ChartComponent  
 └── FooterComponent

This structure improves:

- Scalability
- Maintainability
- Testability

---

# 🔥 Component Anatomy

```ts
import { Component } from "@angular/core";

@Component({
  selector: "app-user",
  template: `<h2>Hello {{ name }}</h2>`,
  styleUrls: ["./user.component.css"],
})
export class UserComponent {
  name = "Dipak";
}
```

Usage:

```html
<app-user></app-user>
```

---

# 🧠 Important Concepts

### 🔹 Component-Based Architecture

Angular applications are built as a tree of components.

### 🔹 Smart vs Dumb Components

**Smart (Container) Components:**

- Handle business logic
- Call APIs
- Manage state

**Dumb (Presentational) Components:**

- Receive data via @Input
- Emit events via @Output
- Only responsible for UI

This separation makes apps cleaner and easier to scale.

---

# 💡 Why Components Are Important

- Code reusability
- Clear separation of concerns
- Easier debugging
- Better performance control
- Unit test friendly

---

# 🎯 What Interviewer Is Testing

When asked about components, interviewer checks:

- Do you understand Angular architecture?
- Can you explain template + class relationship?
- Do you understand component communication?
- Do you know best practices?

---

# 🏆 Perfect Interview Answer (30–60 Seconds)

> Components are the core building blocks of Angular applications. Each component controls a specific part of the UI and consists of a TypeScript class, an HTML template, and metadata defined using the @Component decorator. Angular applications are structured as a tree of components, making them scalable and maintainable.

---

# 💬 Common Follow-up Questions

1. Difference between component and directive?
2. How do parent and child components communicate?
3. What is a standalone component?
4. What is change detection strategy?

---

## 🔙 Navigation

[⬅️ Back to Basic Questions List](../../README.md)
