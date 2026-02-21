# 🟡 Intermediate Level

# 10️⃣ FormGroup & FormArray in Angular – Detailed Guide

---

## ✅ Short Interview Answer

FormGroup and FormArray are building blocks of Reactive Forms in Angular.  
FormGroup represents a group of form controls with a fixed structure, while FormArray represents a dynamic collection of form controls.

---

# 🟢 Simple Explanation

Think of a form like a company structure 🏢

FormGroup → A department with fixed employees  
FormArray → A team where members can increase or decrease dynamically  

👉 FormGroup = Fixed structure  
👉 FormArray = Dynamic structure  

---

# 🔹 What is FormGroup?

FormGroup is used when the structure of the form is known and fixed.

Example:

Login Form:
- username
- password

---

## 🔹 Basic FormGroup Example

### TypeScript

```ts
import { FormBuilder, Validators } from '@angular/forms';

constructor(private fb: FormBuilder) {}

loginForm = this.fb.group({
  username: ['', Validators.required],
  password: ['', Validators.required]
});
```

---

### HTML

```html
<form [formGroup]="loginForm">
  <input formControlName="username">
  <input type="password" formControlName="password">
</form>
```

---

# 🔥 Accessing FormGroup Values

```ts
this.loginForm.value
this.loginForm.get('username')?.value
```

---

# 🔥 Nested FormGroup Example

```ts
this.fb.group({
  personalInfo: this.fb.group({
    firstName: [''],
    lastName: ['']
  })
});
```

Used for complex structured forms.

---

# 🔹 What is FormArray?

FormArray is used when form controls are dynamic.

Example:
- Multiple skills
- Multiple addresses
- Multiple phone numbers

---

# 🔥 Basic FormArray Example

### TypeScript

```ts
import { FormArray } from '@angular/forms';

profileForm = this.fb.group({
  skills: this.fb.array([])
});

get skills(): FormArray {
  return this.profileForm.get('skills') as FormArray;
}

addSkill() {
  this.skills.push(this.fb.control(''));
}
```

---

### HTML

```html
<div formArrayName="skills">
  <div *ngFor="let skill of skills.controls; let i = index">
    <input [formControlName]="i">
  </div>
</div>

<button (click)="addSkill()">Add Skill</button>
```

---

# 🔥 Removing Item from FormArray

```ts
removeSkill(index: number) {
  this.skills.removeAt(index);
}
```

---

# 🧠 FormGroup vs FormArray Comparison

| Feature | FormGroup | FormArray |
|----------|-----------|-----------|
| Structure | Fixed | Dynamic |
| Key-based access | Yes | Index-based access |
| Use case | Login, Registration | Skills, Addresses |
| Scalability | Moderate | High |

---

# 🔥 Validation in FormArray

```ts
this.fb.array([
  this.fb.control('', Validators.required)
]);
```

Each control can have its own validators.

---

# 🔥 Real-World Enterprise Example

Employee Registration:

- Personal Info (FormGroup)
- Skills (FormArray)
- Projects (FormArray of FormGroups)

```ts
projects: this.fb.array([
  this.fb.group({
    projectName: [''],
    duration: ['']
  })
])
```

---

# 🚀 Best Practices

- Use FormGroup for fixed forms
- Use FormArray for dynamic fields
- Always typecast to FormArray when accessing
- Use FormBuilder for cleaner code
- Validate before submitting form

---

# 🎯 What Interviewer Is Testing

- Do you understand reactive forms deeply?
- Difference between FormGroup and FormArray?
- Can you build dynamic forms?
- Can you handle nested FormGroups?
- How to remove items from FormArray?

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> FormGroup represents a fixed set of form controls, while FormArray is used for dynamic collections of controls. FormGroup uses key-based access, whereas FormArray uses index-based access. FormArray is commonly used for dynamic fields like skills or addresses, and both are core parts of Angular Reactive Forms.

---

# 💬 Common Follow-up Questions

1. Difference between FormGroup and FormArray?
2. How to validate dynamic controls?
3. Can FormArray contain FormGroup?
4. How to reset FormArray?
5. How to pre-fill FormArray from API?

---

## 🔙 Navigation

⬅️ Back to Intermediate Questions List
