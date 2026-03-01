# 🟡 Intermediate Level

# 16️⃣ Async Pipe in Angular – Detailed Guide

---

## ✅ Short Interview Answer

The Async Pipe in Angular is used to automatically subscribe to an Observable or Promise in the template and unsubscribe when the component is destroyed. It simplifies asynchronous data handling and prevents memory leaks.

---

# 🟢 Simple Explanation

When working with Observables, normally we do:

```ts
this.data$.subscribe((value) => {
  this.data = value;
});
```

But then we must remember to unsubscribe.

👉 Async Pipe does both automatically:

- Subscribes
- Unsubscribes

All inside the template.

---

# 🔹 Why Do We Need Async Pipe?

Without Async Pipe:

- Manual subscription required
- Risk of memory leaks
- More boilerplate code

With Async Pipe:

- Cleaner template
- Automatic unsubscription
- Less code
- Better performance management

---

# 🟡 Basic Example

## TypeScript

```ts
users$ = this.http.get("/api/users");
```

## Template

```html
<div *ngFor="let user of users$ | async">{{ user.name }}</div>
```

That’s it.

No subscribe() needed.

---

# 🔥 How Async Pipe Works Internally

When template renders:

1️⃣ Async Pipe subscribes to Observable  
2️⃣ When value emits → UI updates  
3️⃣ When component destroys → automatically unsubscribes

---

# 🔥 Async Pipe with Promise

```ts
dataPromise = fetch("/api/data").then((res) => res.json());
```

```html
<div>{{ dataPromise | async }}</div>
```

Works for Promises as well.

---

# 🔥 Async Pipe with BehaviorSubject

```ts
message$ = this.dataService.message$;
```

```html
<p>{{ message$ | async }}</p>
```

Every time BehaviorSubject emits → UI updates.

---

# 🧠 Async Pipe vs Manual Subscribe

| Feature                 | Manual Subscribe | Async Pipe |
| ----------------------- | ---------------- | ---------- |
| Code size               | More             | Less       |
| Memory leak risk        | High             | Low        |
| Auto unsubscribe        | ❌ No            | ✅ Yes     |
| Recommended in template | ❌ No            | ✅ Yes     |

---

# 🚀 Real-World Scenario

## Search Example

```ts
results$ = this.searchControl.valueChanges.pipe(
  debounceTime(300),
  switchMap((value) => this.api.search(value)),
);
```

Template:

```html
<div *ngFor="let result of results$ | async">{{ result }}</div>
```

Clean and reactive.

---

# 🔥 Important Behavior

Async Pipe:

- Subscribes automatically
- Triggers change detection on new value
- Unsubscribes on component destroy

---

# 🧠 Async Pipe + OnPush

Async Pipe works perfectly with:

```ts
ChangeDetectionStrategy.OnPush;
```

Because async emission triggers change detection.

---

# 🚀 Multiple Async Pipes

You can use it multiple times:

```html
<div>{{ user$ | async }}</div>
<div>{{ settings$ | async }}</div>
```

Each pipe manages its own subscription.

---

# ❌ Common Mistakes

- Using async pipe and manual subscribe together
- Calling heavy functions inside async expression
- Forgetting null checks before render
- Using async pipe inside component TS (not allowed)

---

# 🎯 What Interviewer Is Testing

- Do you understand subscription lifecycle?
- How to prevent memory leaks?
- Async pipe vs manual subscribe?
- Does async pipe trigger change detection?
- Can it work with Promises?

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> The Async Pipe in Angular automatically subscribes to Observables or Promises in the template and unsubscribes when the component is destroyed. It simplifies asynchronous data handling, reduces boilerplate code, and prevents memory leaks. It works seamlessly with ChangeDetectionStrategy.OnPush and is the recommended approach for handling Observables in templates.

---

# 💬 Common Follow-up Questions

1. Does async pipe unsubscribe automatically?
2. Can async pipe work with Promise?
3. Does async pipe trigger change detection?
4. Async pipe vs manual subscribe?
5. Can we use async pipe inside component TypeScript?

---

## 🔙 Navigation

[⬅️ Back to Intermediate Questions List](../../README.md)
