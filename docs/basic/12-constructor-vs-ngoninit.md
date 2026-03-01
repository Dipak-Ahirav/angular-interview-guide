# 1️⃣2️⃣ Constructor vs ngOnInit in Angular

---

## ✅ Short Interview Answer

The constructor is used for initializing class dependencies (Dependency Injection), while ngOnInit is a lifecycle hook used for component initialization logic after Angular has set input properties.

---

# 🟢 Simple Explanation (For Freshers)

Think of it like this:

When you build a house 🏠

1. Constructor → Lays the foundation (basic setup)
2. ngOnInit → Interior setup (actual working setup)

In Angular:

- Constructor runs first when the component is created.
- ngOnInit runs after Angular finishes setting up the component.

👉 Constructor = Basic Setup  
👉 ngOnInit = Real Initialization Logic

---

# 🔹 What is Constructor?

The constructor is a TypeScript feature (not Angular-specific).

It is used for:

- Injecting services
- Initializing simple variables
- Basic setup

Example:

```ts
constructor(private userService: UserService) {}
```

Important:

- Angular calls constructor when creating the class instance.
- Input properties are NOT available yet.
- Avoid heavy logic or API calls here.

---

# 🔹 What is ngOnInit?

ngOnInit is an Angular lifecycle hook.

It runs:

- After Angular initializes component inputs
- Once per component lifecycle

Best place for:

- API calls
- Initialization logic
- Data loading
- Complex setup

Example:

```ts
ngOnInit() {
  this.loadUsers();
}
```

---

# 🟡 Technical Comparison

| Constructor          | ngOnInit                      |
| -------------------- | ----------------------------- |
| TypeScript feature   | Angular lifecycle hook        |
| Runs first           | Runs after constructor        |
| Used for DI          | Used for initialization logic |
| Inputs not available | Inputs available              |
| Avoid heavy logic    | Safe for API calls            |

---

# 💻 Practical Example

```ts
export class UserComponent implements OnInit {
  @Input() userId!: number;

  constructor(private userService: UserService) {
    console.log("Constructor called");
  }

  ngOnInit() {
    console.log("ngOnInit called");
    console.log("User ID:", this.userId);
    this.userService.getUser(this.userId);
  }
}
```

Execution Order:

1. Constructor runs
2. Angular sets @Input values
3. ngOnInit runs

---

# 🚀 Why Shouldn't We Call API in Constructor?

Bad Practice:

```ts
constructor(private service: ApiService) {
  this.service.getData(); // ❌ Not recommended
}
```

Why?

- Component not fully initialized
- Inputs not ready
- Harder to test

Correct Practice:

```ts
ngOnInit() {
  this.service.getData(); // ✅ Recommended
}
```

---

# 🧠 Advanced Interview Concept

## 🔹 What About ngOnChanges?

If your component depends on @Input values and they change dynamically:

- Use ngOnChanges instead of only ngOnInit.

---

## 🔹 Standalone Components & Constructor

Even with standalone components (Angular 15+), constructor usage remains same for DI.

---

# 🎯 What Interviewer Is Testing

- Do you understand lifecycle order?
- Do you know where to place API calls?
- Do you understand dependency injection timing?
- Can you explain @Input availability?

---

# 🏆 Perfect Interview Answer (1 Minute Version)

> The constructor is a TypeScript feature used mainly for dependency injection and basic setup, while ngOnInit is an Angular lifecycle hook used for component initialization after Angular sets input properties. API calls and heavy initialization logic should be placed in ngOnInit, not in the constructor.

---

# 💬 Common Follow-up Questions

1. Which runs first — constructor or ngOnInit?
2. Can we access @Input in constructor?
3. Why avoid heavy logic in constructor?
4. What is the difference between ngOnInit and ngOnChanges?

---

## 🔙 Navigation

[⬅️ Back to Basic Questions List](../../README.md)
