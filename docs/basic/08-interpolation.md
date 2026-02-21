# 8️⃣ What is Interpolation in Angular?

---

## ✅ Short Interview Answer

Interpolation is a one-way data binding technique in Angular used to display component data inside the template using double curly braces {{ }}.

---

# 🟢 Simple Explanation (For Freshers)

Suppose you have a variable in your component:

```ts
name = "Dipak";
```

And you want to show it on your webpage.

You write:

```html
<h1>{{ name }}</h1>
```

Angular automatically replaces {{ name }} with the value.

👉 Interpolation = Displaying data from TypeScript into HTML.

---

# 🔹 Why Do We Need Interpolation?

Without interpolation:
- We would manually update HTML using JavaScript.
- Code becomes complex.

With interpolation:
- Angular automatically updates UI when data changes.
- Clean and readable templates.

---

# 🟡 Technical Explanation (For Experienced Developers)

Interpolation is a form of **one-way data binding**:

Component → View

Syntax:

```html
{{ expression }}
```

Angular evaluates the expression inside the curly braces and updates the DOM whenever change detection runs.

---

# 🔥 What Can Be Used Inside Interpolation?

You can use:

- Variables
- Expressions
- Method calls
- Ternary operators

Example:

```html
<p>{{ 5 + 5 }}</p>
<p>{{ username.toUpperCase() }}</p>
<p>{{ isLoggedIn ? 'Welcome' : 'Login' }}</p>
```

---

# 💻 Practical Example

Component:

```ts
export class AppComponent {
  title = "Angular Interview Guide";
  count = 10;
}
```

Template:

```html
<h1>{{ title }}</h1>
<p>Total Count: {{ count }}</p>
```

If `count` changes → UI updates automatically.

---

# 🧠 Important Interview Concept

## 🔹 Interpolation vs Property Binding

Interpolation:

```html
<h1>{{ title }}</h1>
```

Property Binding:

```html
<img [src]="imageUrl">
```

Difference:
- Interpolation is mainly used for text.
- Property binding is used for element properties.

---

## 🔹 Can Interpolation Be Used in Attributes?

Yes, but property binding is preferred.

Example:

```html
<img src="{{ imageUrl }}">
```

Better way:

```html
<img [src]="imageUrl">
```

---

# 🚀 Performance Note

Interpolation is evaluated during change detection.

Heavy computations inside interpolation (like complex functions) can impact performance.

Bad practice:

```html
{{ calculateTotal() }}
```

Better practice:
Compute value once in component.

---

# 🎯 What Interviewer Is Testing

- Do you understand one-way binding?
- Can you differentiate interpolation and property binding?
- Do you know change detection impact?
- Can you explain expression evaluation?

---

# 🏆 Perfect Interview Answer (1 Minute Version)

> Interpolation in Angular is a one-way data binding technique that allows displaying component data inside the template using {{ }} syntax. It binds data from the component to the view and updates automatically during change detection.

---

# 💬 Common Follow-up Questions

1. Difference between interpolation and property binding?
2. Can we use functions inside interpolation?
3. How does change detection affect interpolation?
4. Is interpolation two-way binding?

---

## 🔙 Navigation

⬅️ Back to Basic Questions List
