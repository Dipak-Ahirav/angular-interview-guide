# 4️⃣ What is Data Binding in Angular?

---

## ✅ Short Interview Answer

Data binding is the mechanism that connects the component (TypeScript) with the template (HTML), allowing data to flow between the UI and application logic.

---

# 🟢 Simple Explanation (For Freshers)

Imagine you have a variable in your TypeScript file:

```ts
name = "Dipak";
```

And you want to show it in your HTML page.

Data binding helps Angular connect that variable to the UI automatically.

So when the value changes in TypeScript → UI updates automatically.

That connection is called **Data Binding**.

---

# 🔹 Why Do We Need Data Binding?

Without data binding:

- We would manually update the DOM.
- Code would become complex and messy.

With data binding:

- Angular updates the UI automatically.
- Code becomes cleaner and reactive.

---

# 🟡 Technical Explanation (For Experienced Developers)

Data binding is Angular’s mechanism to synchronize data between:

- Component class (business logic)
- Template (view)

Angular supports **four types of data binding**, enabling unidirectional and bidirectional data flow.

---

# 🔥 Types of Data Binding

## 1️⃣ Interpolation (Component → View)

Used to display values inside HTML.

```html
<h1>{{ title }}</h1>
```

- One-way binding
- Only for displaying text

---

## 2️⃣ Property Binding (Component → View)

Used to bind values to HTML element properties.

```html
<img [src]="imageUrl" /> <button [disabled]="isDisabled">Click</button>
```

- One-way binding
- Used for DOM properties

---

## 3️⃣ Event Binding (View → Component)

Used to listen to DOM events.

```html
<button (click)="save()">Save</button>
```

- One-way binding
- View sends data to component

---

## 4️⃣ Two-Way Binding (Component ↔ View)

Combines property + event binding.

```html
<input [(ngModel)]="username" />
<p>{{ username }}</p>
```

- Data flows both ways
- Requires FormsModule

---

# 🧠 Understanding Data Flow

### 🔹 One-Way Binding

Data flows in one direction:
Component → View OR View → Component

### 🔹 Two-Way Binding

Data flows in both directions:
Component ↔ View

---

# 💻 Practical Example

Component:

```ts
export class AppComponent {
  username = "Dipak";

  updateName() {
    this.username = "Angular";
  }
}
```

Template:

```html
<h2>{{ username }}</h2>
<button (click)="updateName()">Change Name</button>
```

When button is clicked → UI updates automatically.

---

# 🚀 Performance Note (Interview Booster)

Angular uses **change detection** to track data changes and update the view efficiently.

Using unidirectional data flow improves performance and predictability.

---

# 🎯 What Interviewer Is Testing

When this question is asked, interviewer checks:

- Do you understand Angular’s core concept?
- Do you know different binding types?
- Can you explain one-way vs two-way binding?
- Do you understand change detection basics?

---

# 🏆 Perfect Interview Answer (1 Minute Version)

> Data binding in Angular is the mechanism that synchronizes data between the component and the template. Angular provides four types of binding: interpolation, property binding, event binding, and two-way binding. It enables dynamic UI updates without manual DOM manipulation.

---

# 💬 Common Follow-up Questions

1. Difference between interpolation and property binding?
2. How does two-way binding work internally?
3. What is unidirectional data flow?
4. Does Angular use two-way binding by default?

---

## 🔙 Navigation

[⬅️ Back to Basic Questions List](../../README.md)
