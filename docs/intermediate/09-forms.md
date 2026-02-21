# 🟡 Intermediate Level

# 09️⃣ Angular Forms – Detailed Guide (Template-Driven vs Reactive Forms)

---

## ✅ Short Interview Answer

Angular provides two approaches to handling forms:

1️⃣ Template-Driven Forms  
2️⃣ Reactive Forms  

Template-driven forms are simpler and rely on directives in the template.  
Reactive forms are more powerful, scalable, and suitable for complex enterprise applications.

---

# 🟢 Simple Explanation

Imagine you are building a Login Form.

Angular gives you two ways:

Template-Driven → Simple, form logic mostly in HTML  
Reactive → Form logic fully controlled in TypeScript  

👉 Small app → Template-driven  
👉 Large enterprise app → Reactive forms

---

# 🔹 1️⃣ Template-Driven Forms

### Characteristics:

- Uses FormsModule
- Uses ngModel
- Two-way data binding
- Less code in TypeScript
- Good for simple forms

---

## 🔹 Setup

```ts
import { FormsModule } from '@angular/forms';
```

---

## 🔹 Example

### HTML

```html
<form #loginForm="ngForm" (ngSubmit)="onSubmit(loginForm)">
  <input type="text" name="username" ngModel required>
  <input type="password" name="password" ngModel required>
  <button type="submit">Login</button>
</form>
```

### TS

```ts
onSubmit(form: any) {
  console.log(form.value);
}
```

---

# 🔹 2️⃣ Reactive Forms

### Characteristics:

- Uses ReactiveFormsModule
- Form model defined in TypeScript
- More scalable
- Easier testing
- Better validation control
- Suitable for dynamic forms

---

## 🔹 Setup

```ts
import { ReactiveFormsModule } from '@angular/forms';
```

---

## 🔹 Example

### TS

```ts
import { FormBuilder, Validators } from '@angular/forms';

constructor(private fb: FormBuilder) {}

loginForm = this.fb.group({
  username: ['', Validators.required],
  password: ['', [Validators.required, Validators.minLength(6)]]
});
```

### HTML

```html
<form [formGroup]="loginForm" (ngSubmit)="onSubmit()">
  <input formControlName="username">
  <input type="password" formControlName="password">
  <button type="submit">Login</button>
</form>
```

---

# 🔥 Template vs Reactive Comparison

| Feature | Template-Driven | Reactive |
|----------|----------------|----------|
| Setup location | HTML | TypeScript |
| Validation | Template-based | Code-based |
| Scalability | Limited | High |
| Testing | Harder | Easier |
| Dynamic forms | Difficult | Easy |
| Enterprise use | Rare | Common |

---

# 🔥 Form Validation in Reactive Forms

## Built-in Validators

```ts
Validators.required  
Validators.minLength(5)  
Validators.maxLength(10)  
Validators.email  
Validators.pattern()
```

---

# 🔥 Custom Validator Example

```ts
function customValidator(control: AbstractControl) {
  if (control.value === 'admin') {
    return { notAllowed: true };
  }
  return null;
}
```

---

# 🔥 Async Validator Example

```ts
username: ['', null, this.userService.checkUsernameExists]
```

Used for server-side validation.

---

# 🔥 FormArray (Dynamic Forms)

```ts
this.fb.group({
  skills: this.fb.array([])
});
```

Used when number of form controls is dynamic.

---

# 🔥 Form States

Each control has:

- valid
- invalid
- touched
- untouched
- dirty
- pristine
- pending

Example:

```ts
this.loginForm.valid
```

---

# 🧠 Common Interview Scenario

Question:
Why are Reactive Forms preferred in enterprise applications?

Answer:
Because they provide better scalability, dynamic form support, strong validation control, and better testability.

---

# 🚀 Best Practices

- Prefer Reactive Forms in large apps
- Avoid mixing template-driven and reactive
- Use FormBuilder for cleaner code
- Use async validators carefully
- Always check form validity before submit

---

# 🎯 What Interviewer Is Testing

- Do you understand both form approaches?
- Can you implement validation?
- Do you know FormArray?
- Can you explain form states?
- Which approach is better for enterprise apps?

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> Angular provides two approaches to forms: Template-Driven and Reactive Forms. Template-driven forms are simple and suitable for small forms, while Reactive Forms are more scalable, testable, and preferred in enterprise applications. Reactive forms allow better validation control, dynamic form creation using FormArray, and improved maintainability.

---

# 💬 Common Follow-up Questions

1. Difference between template-driven and reactive forms?
2. What is FormArray?
3. How to create custom validator?
4. What is async validator?
5. How to reset form?

---

## 🔙 Navigation

⬅️ Back to Intermediate Questions List
