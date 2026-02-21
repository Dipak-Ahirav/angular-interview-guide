# 1️⃣1️⃣ What are Lifecycle Hooks in Angular?

---

## ✅ Short Interview Answer

Lifecycle hooks are special methods in Angular that are automatically called at different stages of a component’s life — from creation to destruction.

---

# 🟢 Simple Explanation (For Freshers)

Think of a component like a human life cycle:

1. Born 👶  
2. Grows 🧑  
3. Changes 🔄  
4. Dies 💀  

Similarly, an Angular component:

1. Gets created  
2. Receives data  
3. Updates when data changes  
4. Gets destroyed  

Angular gives us **lifecycle hooks** to run code at each stage.

👉 Lifecycle Hooks = Important checkpoints in a component’s life.

---

# 🔹 Why Do We Need Lifecycle Hooks?

Without lifecycle hooks:
- We wouldn’t know when a component is ready.
- We wouldn’t know when inputs change.
- We wouldn’t know when to clean up resources.

With lifecycle hooks:
- We can initialize data properly.
- React to input changes.
- Avoid memory leaks.
- Control performance.

---

# 🟡 Technical Explanation (For Experienced Developers)

Angular components go through a lifecycle managed by Angular’s change detection mechanism.

Lifecycle hooks are methods defined inside a component class that Angular calls automatically at specific moments.

---

# 🔥 Important Lifecycle Hooks

## 1️⃣ constructor()

- Called when class instance is created.
- Used for Dependency Injection.
- Should NOT contain heavy logic.

```ts
constructor(private userService: UserService) {}
```

---

## 2️⃣ ngOnChanges()

- Called when input properties change.
- Runs before ngOnInit.

```ts
ngOnChanges(changes: SimpleChanges) {
  console.log(changes);
}
```

---

## 3️⃣ ngOnInit()

- Called once after component initialization.
- Best place for API calls or initialization logic.

```ts
ngOnInit() {
  this.loadData();
}
```

---

## 4️⃣ ngDoCheck()

- Called during every change detection cycle.
- Used for custom change detection.

---

## 5️⃣ ngAfterContentInit()

- Called after content projection (<ng-content>).

---

## 6️⃣ ngAfterViewInit()

- Called after component view is fully initialized.
- Useful for DOM-related logic.

```ts
ngAfterViewInit() {
  console.log("View Initialized");
}
```

---

## 7️⃣ ngOnDestroy()

- Called before component is destroyed.
- Used for cleanup (unsubscribe Observables, clear intervals).

```ts
ngOnDestroy() {
  this.subscription.unsubscribe();
}
```

---

# 🧠 Lifecycle Order (Important for Interviews)

Correct execution order:

1. constructor  
2. ngOnChanges  
3. ngOnInit  
4. ngDoCheck  
5. ngAfterContentInit  
6. ngAfterContentChecked  
7. ngAfterViewInit  
8. ngAfterViewChecked  
9. ngOnDestroy  

---

# 💻 Practical Example

```ts
export class AppComponent implements OnInit, OnDestroy {

  constructor() {
    console.log("Constructor called");
  }

  ngOnInit() {
    console.log("Component initialized");
  }

  ngOnDestroy() {
    console.log("Component destroyed");
  }
}
```

---

# 🚀 Important Interview Concept

## 🔹 Why Should We Unsubscribe?

If you subscribe to Observables and don’t unsubscribe in `ngOnDestroy`, 
it can cause memory leaks.

Example:

```ts
this.subscription = this.service.getData().subscribe();
```

Cleanup:

```ts
ngOnDestroy() {
  this.subscription.unsubscribe();
}
```

---

# 🎯 What Interviewer Is Testing

- Do you understand component lifecycle?
- Do you know correct hook order?
- Do you know where to place API calls?
- Do you understand memory leaks?

---

# 🏆 Perfect Interview Answer (1 Minute Version)

> Lifecycle hooks in Angular are special methods that Angular calls at different stages of a component’s life, such as initialization, change detection, view rendering, and destruction. Common hooks include ngOnInit, ngOnChanges, and ngOnDestroy. They allow developers to run code at specific lifecycle phases and manage resources properly.

---

# 💬 Common Follow-up Questions

1. Difference between constructor and ngOnInit?
2. What is the correct lifecycle order?
3. When should we unsubscribe?
4. What is ngAfterViewInit used for?
5. What is content projection lifecycle?

---

## 🔙 Navigation

⬅️ Back to Basic Questions List
