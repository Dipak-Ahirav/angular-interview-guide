# 🟡 Intermediate Level

# 18️⃣ Memory Leaks in Angular – Detailed Guide

---

## ✅ Short Interview Answer

A memory leak in Angular occurs when unused objects or subscriptions are not properly cleaned up, causing memory usage to grow over time. The most common cause is forgetting to unsubscribe from Observables.

---

# 🟢 Simple Explanation

Imagine you open multiple pages in your app.

Each page subscribes to an Observable.

If you navigate away but the subscription is still active:

👉 Memory keeps increasing  
👉 Performance degrades  
👉 App becomes slow

That is a memory leak.

---

# 🔥 What Causes Memory Leaks in Angular?

Most common reasons:

1️⃣ Not unsubscribing from Observables  
2️⃣ Long-lived subscriptions in services  
3️⃣ setInterval / setTimeout not cleared  
4️⃣ Event listeners not removed  
5️⃣ Global objects holding references

---

# 🟡 Example of Memory Leak

```ts
ngOnInit() {
  this.dataService.getData().subscribe(data => {
    console.log(data);
  });
}
```

If component is destroyed but subscription continues → leak.

---

# ✅ Proper Way: Unsubscribe in ngOnDestroy

```ts
subscription!: Subscription;

ngOnInit() {
  this.subscription = this.dataService.getData()
    .subscribe(data => console.log(data));
}

ngOnDestroy() {
  this.subscription.unsubscribe();
}
```

---

# 🚀 Better Way: takeUntil Pattern

```ts
destroy$ = new Subject<void>();

ngOnInit() {
  this.dataService.getData()
    .pipe(takeUntil(this.destroy$))
    .subscribe();
}

ngOnDestroy() {
  this.destroy$.next();
  this.destroy$.complete();
}
```

Recommended pattern in enterprise apps.

---

# 🔥 Best Way: Async Pipe

If used in template:

```html
<div *ngFor="let user of users$ | async">{{ user.name }}</div>
```

Async pipe automatically unsubscribes.

---

# 🧠 Do All Observables Need Unsubscribe?

❌ No

Examples that auto-complete:

- HttpClient requests
- of()
- from()

These complete automatically.

---

# 🧠 Observables That Require Unsubscribe

- interval()
- fromEvent()
- Subject streams
- valueChanges (Forms)
- Custom infinite streams

---

# 🚀 Memory Leak from setInterval

```ts
let id: any;

ngOnInit() {
  id = setInterval(() => {
    console.log("Running");
  }, 1000);
}

ngOnDestroy() {
  clearInterval(id);
}
```

---

# 🔥 Event Listener Leak

```ts
window.addEventListener("resize", this.onResize);
```

Must remove:

```ts
window.removeEventListener("resize", this.onResize);
```

---

# 🧠 Real-World Enterprise Example

Common issue:

- Router navigation
- Component destroyed
- Subscription continues
- API still firing
- Duplicate calls

Fix: takeUntil + OnDestroy.

---

# 🟡 Detecting Memory Leaks

Tools:

- Chrome DevTools → Performance tab
- Chrome DevTools → Memory tab
- Angular DevTools
- Heap snapshots

Symptoms:

- Increasing memory usage
- Slow UI
- Duplicate API calls

---

# 🚨 Common Mistakes

- Subscribing inside subscribe
- Forgetting to unsubscribe from Subjects
- Not completing destroy$ Subject
- Using global event bus incorrectly

---

# 🎯 What Interviewer Is Testing

- Do you understand subscription lifecycle?
- When to unsubscribe?
- Does HttpClient need unsubscribe?
- Best pattern to prevent leaks?
- Async pipe vs manual subscribe?

---

# 🏆 Perfect Interview Answer (2 Minutes)

> A memory leak in Angular happens when subscriptions, event listeners, or timers are not cleaned up properly, causing memory to grow over time. The most common cause is not unsubscribing from long-lived Observables like interval or fromEvent. We can prevent memory leaks using ngOnDestroy, the takeUntil pattern, or by using the async pipe which automatically unsubscribes.

---

# 💬 Common Follow-up Questions

1. Does HttpClient require unsubscribe?
2. What is takeUntil pattern?
3. How to detect memory leaks?
4. What causes duplicate API calls?
5. Does async pipe prevent memory leaks?

---

## 🔙 Navigation

[⬅️ Back to Intermediate Questions List](../../README.md)
