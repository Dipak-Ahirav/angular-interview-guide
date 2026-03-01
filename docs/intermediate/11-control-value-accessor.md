# 🟡 Intermediate Level

# 11️⃣ ControlValueAccessor (CVA) in Angular – Detailed Guide

---

## ✅ Short Interview Answer

ControlValueAccessor is an Angular interface that allows custom components to behave like native form controls. It enables integration of custom UI components with Angular Forms (Reactive and Template-driven).

---

# 🟢 Simple Explanation

Angular knows how to work with:

- <input>
- <select>
- <textarea>

But what if you create your own custom component like:

```html
<app-rating></app-rating>
```

Angular does NOT automatically know how to bind this to a form.

👉 ControlValueAccessor acts as a bridge between Angular Forms and custom components.

---

# 🔹 Why Do We Need ControlValueAccessor?

Without CVA:

- Custom components cannot use formControlName
- No integration with Reactive Forms
- No validation support
- No touched/dirty state tracking

With CVA:

- Custom component works like native input
- Supports form validation
- Tracks touched, dirty, disabled states
- Fully compatible with Angular Forms

---

# 🟡 What is ControlValueAccessor?

It is an interface with 4 methods:

writeValue()
registerOnChange()
registerOnTouched()
setDisabledState()

---

# 🔥 Interface Structure

```ts
import { ControlValueAccessor } from "@angular/forms";

export class CustomComponent implements ControlValueAccessor {
  writeValue(obj: any): void {}

  registerOnChange(fn: any): void {}

  registerOnTouched(fn: any): void {}

  setDisabledState?(isDisabled: boolean): void {}
}
```

---

# 🔹 Understanding Each Method

## 1️⃣ writeValue(value)

Called by Angular when form value changes.
Used to update component UI.

---

## 2️⃣ registerOnChange(fn)

Stores function that Angular calls when value changes.

---

## 3️⃣ registerOnTouched(fn)

Marks control as touched.

---

## 4️⃣ setDisabledState(isDisabled)

Handles disabled state from form.

---

# 💻 Complete Example

## Step 1️⃣ Create Custom Component

```ts
import { Component, forwardRef } from "@angular/core";
import { ControlValueAccessor, NG_VALUE_ACCESSOR } from "@angular/forms";

@Component({
  selector: "app-rating",
  template: `
    <button (click)="setRating(1)">1</button>
    <button (click)="setRating(2)">2</button>
    <button (click)="setRating(3)">3</button>
  `,
  providers: [
    {
      provide: NG_VALUE_ACCESSOR,
      useExisting: forwardRef(() => RatingComponent),
      multi: true,
    },
  ],
})
export class RatingComponent implements ControlValueAccessor {
  value = 0;
  onChange = (value: any) => {};
  onTouched = () => {};

  writeValue(value: number): void {
    this.value = value;
  }

  registerOnChange(fn: any): void {
    this.onChange = fn;
  }

  registerOnTouched(fn: any): void {
    this.onTouched = fn;
  }

  setDisabledState(isDisabled: boolean): void {}

  setRating(rating: number) {
    this.value = rating;
    this.onChange(rating);
    this.onTouched();
  }
}
```

---

## Step 2️⃣ Use in Reactive Form

```ts
this.form = this.fb.group({
  rating: [0],
});
```

```html
<form [formGroup]="form">
  <app-rating formControlName="rating"></app-rating>
</form>
```

Now your custom component behaves like native input.

---

# 🔥 How It Works Internally

Angular FormControl:

1. Calls writeValue() when setting value
2. Calls registerOnChange() to listen for changes
3. Calls registerOnTouched() for touch tracking
4. Calls setDisabledState() when control disabled

CVA connects both sides.

---

# 🧠 Real-World Use Cases

- Custom dropdown component
- Date picker
- Rating system
- Toggle switch
- Rich text editor
- Third-party UI library integration

---

# 🚀 Common Mistakes

- Forgetting NG_VALUE_ACCESSOR provider
- Not calling onChange()
- Not calling onTouched()
- Not handling disabled state

---

# 🎯 What Interviewer Is Testing

- Understanding of Angular Forms internals
- Ability to integrate custom components with forms
- Knowledge of writeValue vs registerOnChange
- Awareness of NG_VALUE_ACCESSOR usage

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> ControlValueAccessor is an Angular interface used to connect custom form components with Angular Forms. It allows custom components to behave like native form controls by implementing writeValue, registerOnChange, registerOnTouched, and setDisabledState methods. It is commonly used for reusable UI components like date pickers or rating systems.

---

# 💬 Common Follow-up Questions

1. Why do we need NG_VALUE_ACCESSOR?
2. What happens if writeValue is not implemented?
3. Difference between CVA and Validator?
4. How does Angular call registerOnChange?
5. Can CVA be used with Template-driven forms?

---

## 🔙 Navigation

[⬅️ Back to Intermediate Questions List](../../README.md)
