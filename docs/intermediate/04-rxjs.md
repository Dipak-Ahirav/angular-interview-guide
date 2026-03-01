# 🟡 Intermediate Level

# 04️⃣ RxJS in Angular – Detailed Guide

---

## ✅ Short Interview Answer

RxJS (Reactive Extensions for JavaScript) is a library used in Angular to handle asynchronous data streams using Observables. It provides powerful operators to transform, filter, combine, and manage async data efficiently.

---

# 🟢 Simple Explanation

Imagine data flowing like a river 🌊

Instead of waiting for one bucket of water (Promise),
RxJS lets you control the whole river.

You can:

- Filter the water
- Transform the water
- Stop the flow
- Combine multiple rivers

👉 RxJS = Powerful tool to manage async data streams.

---

# 🔹 Why RxJS is Important in Angular?

Angular heavily relies on RxJS for:

- HTTP requests
- Router events
- Form value changes
- WebSockets
- State management
- Event handling

Without RxJS, Angular async handling would be limited.

---

# 🟡 Core Concepts of RxJS

## 1️⃣ Observable

Represents a stream of values over time.

```ts
import { Observable } from "rxjs";

const obs = new Observable((observer) => {
  observer.next("Hello");
  observer.complete();
});
```

---

## 2️⃣ Observer

Consumes values emitted by Observable.

```ts
obs.subscribe((value) => console.log(value));
```

---

## 3️⃣ Subscription

Represents execution of Observable.

```ts
const sub = obs.subscribe();
sub.unsubscribe();
```

Important for preventing memory leaks.

---

# 🔥 Types of Observables

## 🔹 Cold Observable

- Executes separately for each subscriber.
- Example: HTTP call

## 🔹 Hot Observable

- Shared execution among subscribers.
- Example: Subject

---

# 🔥 Subjects in RxJS

## 1️⃣ Subject

Acts as both Observable and Observer.

```ts
import { Subject } from "rxjs";

const subject = new Subject<number>();
subject.subscribe((val) => console.log("A:", val));
subject.next(1);
```

---

## 2️⃣ BehaviorSubject

Stores latest value.

```ts
import { BehaviorSubject } from "rxjs";

const bs = new BehaviorSubject<number>(0);
bs.subscribe((val) => console.log(val));
```

Used heavily for state management.

---

## 3️⃣ ReplaySubject

Replays previous values to new subscribers.

---

# 🚀 Important RxJS Operators

Operators are used inside `pipe()`.

---

## 🔹 map()

Transforms data.

```ts
.pipe(map(data => data.length))
```

---

## 🔹 filter()

Filters emitted values.

---

## 🔹 switchMap()

Cancels previous request and switches to new one.

Very important for search API calls.

```ts
.pipe(switchMap(term => this.http.get(`/api?q=${term}`)))
```

---

## 🔹 mergeMap()

Runs multiple Observables in parallel.

---

## 🔹 concatMap()

Executes Observables sequentially.

---

## 🔹 debounceTime()

Used in search input optimization.

```ts
.pipe(debounceTime(300))
```

---

## 🔹 catchError()

Handles errors.

---

## 🔹 take(), takeUntil()

Used for automatic unsubscription.

---

# 🧠 Common Interview Scenario

## 🔹 Search Optimization

```ts
this.searchControl.valueChanges
  .pipe(
    debounceTime(300),
    distinctUntilChanged(),
    switchMap((value) => this.api.search(value)),
  )
  .subscribe();
```

Why switchMap?
Because it cancels previous API call if user types again.

---

# 🔥 Memory Leak Prevention

Best practices:

- Use async pipe
- Use takeUntil pattern
- Unsubscribe in ngOnDestroy
- Avoid nested subscriptions

---

# 🚀 Async Pipe (Recommended)

```html
<div *ngFor="let user of users$ | async">{{ user.name }}</div>
```

Async pipe automatically:

- Subscribes
- Unsubscribes
- Prevents memory leaks

---

# 🧠 Advanced RxJS Concepts

- Multicasting
- shareReplay()
- forkJoin()
- combineLatest()
- withLatestFrom()

Example:

```ts
forkJoin([this.api.getUsers(), this.api.getProducts()]).subscribe(
  ([users, products]) => {},
);
```

---

# 🎯 What Interviewer Is Testing

- Do you understand Observables deeply?
- Can you explain switchMap vs mergeMap?
- Do you know Subjects?
- Can you prevent memory leaks?
- Do you understand reactive programming?

---

# 🏆 Perfect Interview Answer (1–2 Minutes)

> RxJS is a reactive programming library used in Angular to handle asynchronous data streams. It uses Observables and powerful operators like map, switchMap, and debounceTime to transform and control data flow. Angular relies heavily on RxJS for HTTP requests, forms, and routing. Proper subscription management and operator usage are critical for performance and memory management.

---

# 💬 Common Follow-up Questions

1. Difference between switchMap and mergeMap?
2. What is Subject vs BehaviorSubject?
3. What is forkJoin?
4. How to prevent memory leaks?
5. What is shareReplay used for?

---

## 🔙 Navigation

[⬅️ Back to Intermediate Questions List](../../README.md)
