# 1️⃣5️⃣ What is Two-Way Data Binding in Angular?

---

## ✅ Short Interview Answer

Two-way data binding in Angular is a mechanism that synchronizes data between the component (TypeScript) and the template (HTML). When the value changes in the UI, it updates the component, and when the component value changes, it updates the UI automatically.

---

# 🟢 Simple Explanation (For Freshers)

Imagine you have an input box:

```html
<input />
```

And you want:

- When user types → value updates in component
- When component value changes → input box updates automatically

Two-way data binding allows both directions to stay synchronized.

👉 Component ↔ View

---

# 🔹 Why Do We Need Two-Way Binding?

Without two-way binding:

- We would manually listen to input events.
- Then manually update variables.
- Code becomes repetitive.

With two-way binding:

- Angular automatically keeps UI and data in sync.
- Cleaner and faster development.

---

# 🟡 Technical Explanation (For Experienced Developers)

Two-way binding is a combination of:

- Property Binding → `[property]`
- Event Binding → `(event)`

Angular provides special syntax:

```html
[(ngModel)]
```

This is called **banana-in-a-box syntax**.

Internally:

```html
[(ngModel)]="username"
```

Is equivalent to:

```html
[ngModel]="username" (ngModelChange)="username = $event"
```

---

# 🔥 Basic Example

## Step 1: Import FormsModule

In AppModule:

```ts
import { FormsModule } from "@angular/forms";

@NgModule({
  imports: [FormsModule],
})
export class AppModule {}
```

(For standalone apps, use provideForms().)

---

## Step 2: Use Two-Way Binding

Component:

```ts
export class AppComponent {
  username = "Dipak";
}
```

Template:

```html
<input [(ngModel)]="username" />
<p>{{ username }}</p>
```

Now:

- If user types → paragraph updates
- If component updates value → input updates

---

# 🧠 Important Interview Concepts

## 🔹 Two-Way Binding Is Not Default

Angular follows **unidirectional data flow** by default.

Two-way binding must be explicitly used.

---

## 🔹 Two-Way Binding in Custom Components

For custom components, you need:

```ts
@Input() value: string;
@Output() valueChange = new EventEmitter<string>();
```

Usage:

```html
<app-child [(value)]="parentValue"></app-child>
```

---

## 🔹 Difference Between One-Way and Two-Way

| One-Way Binding                      | Two-Way Binding        |
| ------------------------------------ | ---------------------- |
| Component → View OR View → Component | Component ↔ View       |
| More predictable                     | Easier for forms       |
| Better for performance               | Useful for user inputs |

---

# 🚀 When Should We Use Two-Way Binding?

Best for:

- Forms
- User inputs
- Small dynamic inputs

Avoid for:

- Large complex data flows
- Performance-critical components

---

# 💻 Advanced Note

In larger applications, many developers prefer Reactive Forms instead of ngModel for better scalability and control.

---

# 🎯 What Interviewer Is Testing

- Do you understand banana-in-a-box syntax?
- Do you know how it works internally?
- Do you know FormsModule requirement?
- Can you implement custom two-way binding?

---

# 🏆 Perfect Interview Answer (1 Minute Version)

> Two-way data binding in Angular synchronizes data between the component and template using the [(ngModel)] syntax. It combines property and event binding, allowing changes in the UI to reflect in the component and vice versa. It is mainly used in form handling and requires FormsModule.

---

# 💬 Common Follow-up Questions

1. What is banana-in-a-box syntax?
2. How does two-way binding work internally?
3. Difference between ngModel and reactive forms?
4. Can we implement two-way binding in custom components?
5. Is two-way binding recommended everywhere?

---

## 🔙 Navigation

[⬅️ Back to Basic Questions List](../../README.md)
