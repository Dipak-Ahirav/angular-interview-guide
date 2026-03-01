# 🟡 Intermediate Level

# 02️⃣ What is ChangeDetectionStrategy.OnPush in Angular?

---

## ✅ Short Interview Answer

ChangeDetectionStrategy.OnPush is an optimized change detection strategy in Angular that tells Angular to check a component only when specific conditions occur, instead of checking the entire component tree on every change detection cycle.

---

# 🟢 Simple Explanation

By default, Angular checks every component whenever something changes (like a button click or HTTP response).

In small apps, this is fine.

But in large enterprise apps, checking everything can slow down performance.

👉 OnPush tells Angular:

"Only check this component when really necessary."

---

# 🔹 Why Do We Need OnPush?

Without OnPush:

- Angular runs change detection on the whole component tree.
- Performance may degrade in large applications.

With OnPush:

- Angular checks only when required.
- Improves performance.
- Encourages better coding practices (immutability).

---

# 🟡 Technical Explanation

By default, Angular uses:

```ts
ChangeDetectionStrategy.Default;
```

This means:

- Every async event triggers change detection.
- Entire component tree is checked.

When we use:

```ts
ChangeDetectionStrategy.OnPush;
```

Angular checks the component only when:

1. An @Input() reference changes
2. An event originates from the component
3. An Observable emits a new value (via async pipe)
4. detectChanges() or markForCheck() is manually called

---

# 💻 Basic Example

```ts
import { Component, ChangeDetectionStrategy } from "@angular/core";

@Component({
  selector: "app-user",
  template: `<p>{{ user.name }}</p>`,
  changeDetection: ChangeDetectionStrategy.OnPush,
})
export class UserComponent {
  user = { name: "Dipak" };
}
```

---

# 🧠 Important Concept: Reference Change

OnPush checks only object reference, not deep property mutation.

❌ This will NOT trigger change detection:

```ts
this.user.name = "Angular";
```

✅ This WILL trigger change detection:

```ts
this.user = { ...this.user, name: "Angular" };
```

This is why immutability is important.

---

# 🔥 Using markForCheck()

If data changes outside Angular's detection:

```ts
constructor(private cd: ChangeDetectorRef) {}

this.cd.markForCheck();
```

This tells Angular to check the component in the next cycle.

---

# 🔥 Using detectChanges()

```ts
this.cd.detectChanges();
```

This immediately triggers change detection for that component.

---

# 🧠 Default vs OnPush Comparison

| Feature                  | Default    | OnPush |
| ------------------------ | ---------- | ------ |
| Checks whole tree        | ✅ Yes     | ❌ No  |
| Performance optimized    | ❌ No      | ✅ Yes |
| Requires immutability    | ❌ No      | ✅ Yes |
| Good for enterprise apps | ⚠️ Limited | ✅ Yes |

---

# 🚀 Real-World Usage

OnPush is commonly used in:

- Large dashboards
- Enterprise systems
- High-performance applications
- Component-driven architectures

---

# 🎯 What Interviewer Is Testing

- Do you understand Angular performance?
- Do you know how change detection works internally?
- Do you understand reference vs value comparison?
- Do you know when to use markForCheck()?

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> ChangeDetectionStrategy.OnPush is an optimized strategy in Angular that limits change detection checks to specific triggers like input reference changes, events inside the component, or observable emissions. It improves performance in large applications and encourages immutable data patterns.

---

# 💬 Common Follow-up Questions

1. What triggers OnPush change detection?
2. Why is immutability important with OnPush?
3. What is markForCheck vs detectChanges?
4. How does OnPush improve performance?
5. Can OnPush cause UI not updating issues?

---

## 🔙 Navigation

[⬅️ Back to Intermediate Questions List](../../README.md)
