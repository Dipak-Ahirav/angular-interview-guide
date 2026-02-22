# 🟡 Intermediate Level

# 13️⃣ ViewChild & ContentChild in Angular – Detailed Guide

---

## ✅ Short Interview Answer

ViewChild and ContentChild are Angular decorators used to access child components, directives, or DOM elements.  
ViewChild accesses elements inside the component’s own template, while ContentChild accesses projected content passed using ng-content.

---

# 🟢 Simple Explanation

Imagine a Parent Component.

There are two types of children:

1️⃣ Children inside its template → ViewChild  
2️⃣ Children passed from outside using <ng-content> → ContentChild  

👉 ViewChild = View (inside template)  
👉 ContentChild = Content (projected from outside)

---

# 🔹 What is ViewChild?

ViewChild allows a parent component to access:

- Child component instance
- Directive
- Template reference variable
- Native DOM element

---

# 🔥 Basic ViewChild Example

## Parent Template

```html
<app-child></app-child>
```

## Parent Component

```ts
import { ViewChild } from '@angular/core';
import { ChildComponent } from './child.component';

@ViewChild(ChildComponent) child!: ChildComponent;

ngAfterViewInit() {
  this.child.sayHello();
}
```

## Child Component

```ts
sayHello() {
  console.log("Hello from Child");
}
```

---

# 🔥 ViewChild with Template Reference Variable

```html
<input #inputRef type="text">
<button (click)="focusInput()">Focus</button>
```

```ts
@ViewChild('inputRef') input!: ElementRef;

focusInput() {
  this.input.nativeElement.focus();
}
```

---

# 🔥 Important Lifecycle Note

ViewChild becomes available in:

```ts
ngAfterViewInit()
```

Not in constructor or ngOnInit.

---

# 🔹 What is ContentChild?

ContentChild is used with Content Projection (ng-content).

It accesses projected content from parent into child.

---

# 🔥 Content Projection Example

## Child Template

```html
<ng-content></ng-content>
```

## Parent Template

```html
<app-child>
  <p #projectedParagraph>Projected Content</p>
</app-child>
```

## Child Component

```ts
import { ContentChild, ElementRef, AfterContentInit } from '@angular/core';

@ContentChild('projectedParagraph') paragraph!: ElementRef;

ngAfterContentInit() {
  console.log(this.paragraph.nativeElement.textContent);
}
```

---

# 🔥 ViewChild vs ContentChild Comparison

| Feature | ViewChild | ContentChild |
|----------|------------|---------------|
| Access internal template | ✅ Yes | ❌ No |
| Access projected content | ❌ No | ✅ Yes |
| Lifecycle hook | ngAfterViewInit | ngAfterContentInit |
| Used for | Child components, DOM | ng-content elements |

---

# 🧠 ViewChildren & ContentChildren

Angular also provides plural versions:

- ViewChildren → Multiple elements inside view
- ContentChildren → Multiple projected elements

Example:

```ts
@ViewChildren(ChildComponent) children!: QueryList<ChildComponent>;
```

---

# 🚀 Real-World Use Cases

- Calling child methods from parent
- Managing focus on input fields
- Accessing custom directive instance
- Working with dynamic components
- Custom UI wrapper components

---

# ❌ Common Mistakes

- Accessing ViewChild before ngAfterViewInit
- Tight coupling between parent & child
- Overusing ViewChild instead of @Input/@Output
- Manipulating DOM excessively

---

# 🎯 What Interviewer Is Testing

- Do you understand component lifecycle?
- Difference between view and content?
- Can you explain ngAfterViewInit vs ngAfterContentInit?
- When to use ViewChild vs @Input?
- Do you understand tight coupling?

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> ViewChild is used to access elements, components, or directives inside a component’s own template and becomes available in ngAfterViewInit. ContentChild is used to access projected content passed using ng-content and becomes available in ngAfterContentInit. ViewChild works with the component view, while ContentChild works with projected external content.

---

# 💬 Common Follow-up Questions

1. When does ViewChild become available?
2. Difference between ViewChild and ContentChild?
3. What is QueryList?
4. When to use ViewChildren?
5. Can ViewChild cause tight coupling?

---

## 🔙 Navigation

⬅️ Back to Intermediate Questions List
